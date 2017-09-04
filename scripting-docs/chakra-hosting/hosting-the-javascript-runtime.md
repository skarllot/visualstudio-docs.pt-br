---
title: "Hospedagem do tempo de execução do JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30ec744e-57cc-4ef5-8fe1-d2c27b946548
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 2bf213bf262ede7642e05c66e424b860238dc57f
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="hosting-the-javascript-runtime"></a>Hospedando o Tempo de Execução do JavaScript
As APIs de JsRT (tempo de execução de JavaScript) fornecem uma maneira para aplicativos da área de trabalho, da Windows Store e do lado do servidor em execução no sistema operacional Windows adicionarem recursos de script para o aplicativo usando o mecanismo JavaScript Chakra baseado em padrões que também é usado pelo Internet Explorer e Microsoft Edge. Essas APIs estão disponíveis no Windows 10 e qualquer versão do sistema operacional Windows que tenha o Internet Explorer versão 11.0 instalado no computador. Para obter mais informações, consulte [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md). Para obter informações sobre como usar o JsRT em aplicativos da Windows Store, consulte [JsRT e a Plataforma Universal do Windows](#Windows).  
  
> [!NOTE]
>  Esta documentação pressupõe uma familiaridade geral de trabalho com a linguagem JavaScript.  
  
## <a name="concepts"></a>Conceitos  
 Noções básicas sobre como hospedar o mecanismo JavaScript usando as APIs de JsRT dependem de dois conceitos principais: tempos de execução e contextos de execução.  
  
 Um *tempo de execução* representa um ambiente de execução do JavaScript completo. Cada tempo de execução que é criado tem seu próprio heap isolado removido por coleta de lixo e, por padrão, seu próprio thread compilador JIT (Just-In-Time) e thread GC (coletor de lixo). Um *contexto de execução* representa um ambiente JavaScript que tem seu próprio objeto global de JavaScript distinto de todos os outros contextos de execução. Um tempo de execução pode conter vários contextos de execução e, nesses casos, todos os contextos de execução compartilham o compilador JIT e o thread de GC associados ao tempo de execução.  
  
 Tempos de execução representam um único thread de execução. Apenas um tempo de execução pode estar ativo em um determinado thread por vez e um tempo de execução só pode estar ativo em um thread por vez. O modelo de threading dos tempos de execução é por empréstimo, portanto, um tempo de execução que não está ativo atualmente em um thread (ou seja, não está executando nenhum código JavaScript nem respondendo a todas as chamadas do host) pode ser usado em qualquer thread que ainda não tem um tempo de execução ativo.  
  
 Contextos de execução estão vinculados a um determinado tempo de execução e executam o código dentro desse tempo de execução. Ao contrário de tempos de execução, vários contextos de execução podem estar ativos em um thread simultaneamente. Assim, um host pode fazer uma chamada para um contexto de execução, esse contexto de execução pode retornar a chamada para o host e o host pode fazer uma chamada para um contexto de execução diferente.  
  
 ![Vários contextos de execução](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting")  
  
 Na prática, a menos que um host precise executar código em ambientes separados, um único contexto de execução pode ser usado. Da mesma forma, a menos que um host precise executar simultaneamente vários trechos de código, um único tempo de execução é suficiente.  
  
## <a name="memory-management"></a>Gerenciamento de memória  
 O JavaScript é uma linguagem de coleta de lixo e, portanto, há várias considerações que se deve ter em mente ao trabalhar com as APIs JsRT de outra linguagem.  
  
 A principal consideração é que o coletor de lixo de JavaScript só poderá ver referências aos valores em dois locais: o heap do seu tempo de execução e a pilha. Portanto, uma referência a um valor de JavaScript que é armazenado dentro de outro valor de JavaScript ou em uma variável local na pilha sempre será visto pelo coletor de lixo. Mas referências armazenadas em outros locais, como heaps gerenciados pelo host ou o sistema, não serão vistas pelo coletor de lixo e podem resultar na coleta prematura de valores que ainda estão em uso pelo host.  
  
> [!IMPORTANT]
>  Alguns compiladores de linguagem (por exemplo, o compilador do Visual Studio C++) otimizarão variáveis locais sempre que possível. Deve-se ter cuidado para garantir que as variáveis locais que referenciam valores de JavaScript estejam na pilha, se é esperado que esses valores sejam mantidos ativos.  
  
 Se uma referência a um valor de JavaScript será armazenada em um local não visível para o coletor de lixo, o host deverá adicionar e remover manualmente as referências usando as APIs de JsRT.  
  
## <a name="exception-handling"></a>Tratamento de exceções  
 Quando ocorre uma exceção de JavaScript durante a execução do script, o tempo de execução recipiente é colocado em um estado de exceção. Enquanto estiver em um estado de exceção, nenhum código poderá ser executado e todas as chamadas à API falharão com o código de erro `JsErrorInExceptionState` até que o host recupere e limpe a exceção usando a API `JsGetAndClearException`. Se o host retorna de um retorno de chamada do JavaScript sem limpar o tempo de execução de um estado de exceção, a exceção de JavaScript é relançada assim que o controle é devolvido ao mecanismo JavaScript. Isso também habilita os retornos de chamada de host a "lançarem" uma exceção de JavaScript, definindo o tempo de execução para um estado de exceção e, em seguida, voltando de um retorno de chamada de host.  
  
 Um host não tem permissão para deixar que suas próprias exceções internas se propaguem por todo um retorno de chamada de host – todos os métodos de retorno de chamada devem capturar todas as exceções de host antes de devolver o controle para o tempo de execução.  
  
## <a name="runtime-resource-usage"></a>Uso de recursos do tempo de execução  
 As APIs de JsRT expõem um número de maneira de monitorar e modificar o modo como os tempos de execução usam os recursos. Elas geralmente são divididas nas seguintes categorias:  
  
-   **Uso de thread**. Por padrão, cada tempo de execução criará um thread dedicado do compilador JIT e um thread dedicado de GC que servirão a esse tempo de execução. Se um tempo de execução é criado com o sinalizador `JsRuntimeAttributeDisableBackgroundWork`, o trabalho de JIT e GC será executado no thread de tempo de execução em si em vez de threads em segundo plano separados para cada um deles. Um host também pode fornecer um retorno de chamada de serviço de thread para a chamada `JsCreateRuntime`, o que permitirá que o host agende o trabalho JIT e GC da maneira que considerar adequada.  
  
-   **Uso de Memória**. Há várias maneiras de monitorar e modificar o uso de memória de um tempo de execução. Se o tempo de execução será executado por um longo período, o host poderá especificar o sinalizador `JsRuntimeAttributeEnableIdleProcessing` ao criar o tempo de execução e, em seguida, chamar `JsIdle` quando o host estiver em um estado ocioso. Isso permite que o mecanismo adie um trabalho de limpeza e contabilização de memória até o tempo ocioso.  
  
     O host pode monitorar as coletas de lixo chamando `JsSetRuntimeBeforeCollectCallback`. Ele também pode monitorar alocações feitas pelo heap chamando `JsSetRuntimeMemoryAllocationCallback`. Observe que essa API não retorna chamadas em todas as alocações de JavaScript, apenas quando o heap do tempo de execução precisa de mais espaço do qual alocar. O retorno de chamada de alocação de memória tem permissão para negar a solicitação, o que disparará uma coleta de lixo e, se não houver memória disponível, um erro de falta de memória no tempo de execução.  
  
     O host também pode chamar `JsSetRuntimeMemoryLimit` para definir limite para a quantidade de memória que um tempo de execução pode usar. Quando um tempo de execução atingir um limite, ele disparará uma coleta de lixo e, se não houver memória disponível, um erro de falta de memória será lançado pelo tempo de execução.  
  
-   **Interrupção e avaliação de script**. O host pode chamar `JsDisableRuntimeExecution` para finalizar a execução dentro de um tempo de execução. Essa chamada pode ser feita a qualquer momento e de qualquer thread. Já que o encerramento do script depende de alcançar os pontos de proteção inseridos no código, um script pode não terminar no exato momento, mas isso ocorrerá logo depois. Por padrão, os pontos de proteção de encerramento são colocados de forma prudente no código gerado e podem não abranger todas as situações, tais como um loop infinito. Criar o tempo de execução com o sinalizador `JsRuntimeAttributeAllowScriptInterrupt` faz com que o tempo de execução insira verificações adicionais para loops infinitos, muitas vezes às custas de uma pequena sobrecarga de desempenho.  
  
     Se um host deseja não permitir a geração de código nativo pelo compilador JIT, ele poderá especificar o sinalizador `JsRuntimeAttributeDisableNativeCodeGeneration`. Um host também pode impedir que scripts executem scripts dinamicamente por conta própria, especificando o sinalizador `JsRuntimeAttributeDisableEval`.  
  
## <a name="debugging-and-profiling"></a>Depuração e criação de perfil  
 APIs de JsRT dão suporte à depuração e criação de perfil por meio da tecnologia de script ativo.  
  
 Começando com o Windows 10, o mecanismo de JavaScript Chakra dá suporte a um mecanismo de borda e a um mecanismo herdado e você pode ter qualquer um deles como destino em JsRT (consulte [Direcionamento para mecanismos de borda vs. mecanismos herdados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md) para obter detalhes). Depurar um script no Visual Studio funciona de forma diferente entre o mecanismo herdado e o de borda. Com o mecanismo herdado, o host precisa fornecer um ponteiro de [Interface IDebugApplication](../winscript/reference/idebugapplication-interface.md), que pode ser obtido de uma instância de [Interface IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md). Com o mecanismo de borda, `IDebugApplication` é preterido e o mecanismo Chakra nativo habilita a funcionalidade de depuração nativa e de script por meio do depurador do Visual Studio, sem a necessidade de uma implementação de `IDebugApplication` pelo usuário.  
  
 Para tornar scripts depuráveis em um contexto de execução, o mecanismo Chakra tem que passar a usar métodos de execução de código menos eficientes. Assim, o código depurável normalmente é executado mais lentamente do que o código não depurável. Como resultado, com o mecanismo herdado, um host pode optar por iniciar a depuração em um contexto de execução desde o início, fornecendo o ponteiro `IDebugApplication` adiantado por meio de `JsCreateContext` ou então pode esperar até que a depuração seja necessário e, em seguida, chamar `JsStartDebugging`. Com o mecanismo de borda, `JsCreateContext` não usa mais um parâmetro `IDebugApplication` e, como resultado, o script só é depurável após `JsStartDebugging` ser chamado. Durante a depuração usando o Visual Studio, a opção "Script" do depurador deve ser habilitada.  
  
 O a criação de perfil do código JavaScript em um contexto de execução pode ser realizada de uma entre duas maneiras. A linha de comando do Visual Studio Profiler (vsperf.exe) pode ser usada no Windows 8.1 e versões posteriores com a opção /js para produzir um relatório que tem como destino o código JavaScript executado no aplicativo. Ou o host pode chamar diretamente `JsStartProfiling` e `JsStopProfiling` e fornecer um retorno de chamada para fazer por conta própria a criação de perfil. O host também pode examinar o estado do heap que sofreu coleta de lixo chamando `JsEnumerateHeap`. A criação de perfil em JsRT funciona da mesma maneira entre o mecanismo herdado e o de borda. No entanto, APIs de JsRT de criação de perfil (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap` e `JsIsEnumeratingHeap`) não estão disponíveis para aplicativos universais do Windows.  
  
<a name="Windows"></a>   
## <a name="jsrt-and-the-universal-windows-platform"></a>JsRT e a Plataforma Universal do Windows  
 Você pode usar as APIs de JsRT para adicionar recursos de script para um aplicativo universal do Windows. Um aplicativo universal do Windows que usa as APIs de JsRT precisará das APIs de JSRT de borda, que por sua vez têm como destino o mecanismo Chakra de borda. Para obter mais informações, consulte [Direcionamento para mecanismos de borda vs. mecanismos herdados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md). A API de JsRT completa está disponível para aplicativos universais do Windows, exceto para suporte a enumeração de heaps e para criação de perfil (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap` e `JsIsEnumeratingHeap` não têm suporte).  
  
 O JsRT também permite que scripts acessem nativamente quaisquer [APIs da UWP (Plataforma Universal do Windows)](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx) depois de expor o namespace da API por meio da API de JsRT de borda `JsProjectWinRTNamespace`. Enquanto os aplicativos universais do Windows não exigem nenhuma configuração além de projeção dos namespaces necessários, em um aplicativo do Windows clássico (Win32), um mecanismo de bombeamento delegado inicializado por COM precisa ser habilitado por meio de `JsSetProjectionEnqueueCallback` para habilitar eventos e APIs assíncronas. A amostra em Win32 a seguir utiliza APIs de UWP assíncronas para criar um cliente HTTP para obter o conteúdo de um URI:  
  
```cpp  
typedef struct _jsCall {  
    JsProjectionCallback jsCallback;  
    JsProjectionCallbackContext jsContext;  
    HANDLE event;  
} jsCall;  
  
// Set up delegated pumping mechanism; not necessary in UWP applications.  
jsCall outstandingCall = {};  
CoInitializeEx(nullptr, COINIT_MULTITHREADED);  
JsSetProjectionEnqueueCallback([](JsProjectionCallback jsCallback,   
JsProjectionCallbackContext jsContext, void *callbackState) {  
    jsCall* call = (jsCall*)callbackState;  
    call->jsCallback = jsCallback;  
    call->jsContext = jsContext;  
    SetEvent(call->event);  
    },  
&outstandingCall);  
HANDLE event = CreateEventEx(NULL, NULL, CREATE_EVENT_MANUAL_RESET, EVENT_ALL_ACCESS);  
outstandingCall.event = event;  
  
// Project necessary namespaces.  
JsProjectWinRTNamespace(L"Windows.Foundation");  
JsProjectWinRTNamespace(L"Windows.Web");  
  
// Get content from an Uri.  
JsRunScript(L"var uri = new Windows.Foundation.Uri(\"http://somedatasource.com\"); " \  
    L"var httpClient = new Windows.Web.Http.HttpClient();" \  
    L"httpClient.getStringAsync(uri).done(function (content) { " \  
    L"    // do something with the string content " \    
    L"}, onError); " \  
    L"function onError(reason) { " \  
    L"    // error handling " \        
    L"}",   
    currentSourceContext, L"", &result);  
  
// Wait for async call to come in and then execute; not necessary in UWP applications.  
WaitForSingleObjectEx(outstandingCall.event, 10000, FALSE) == WAIT_OBJECT_0;  
outstandingCall.jsCallback(outstandingCall.jsContext);  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Aplicativo de exemplo do Tempo de Execução do JavaScript](http://go.microsoft.com/fwlink/p/?LinkID=306674&clcid=0x409)   
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)   
 [Hospedagem de tempo de execução do JavaScript](../chakra-hosting/javascript-runtime-hosting.md)
