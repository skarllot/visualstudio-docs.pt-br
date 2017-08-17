---
title: Borda de destino vs. Mecanismos herdados em APIs de JsRT | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbc7df6c-0bc9-48f5-b9ad-b9ed31c42f92
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 50947cbd619f086daecc1e09f88a4b238a36ee41
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="targeting-edge-vs-legacy-engines-in-jsrt-apis"></a>Borda de destino vs. Mecanismos herdados em APIs JsRT
Começando no Windows 10, uma das alterações que fizemos ao Chakra (o mecanismo JavaScript), que é alinhado com a estratégia de navegador do Windows 10 de dar suporte a um novo mecanismo de renderização de borda, é dar suporte a dois mecanismos Chakra diferentes:  
  
-   O mecanismo Chakra antigo (também chamado de *mecanismo herdado* ou jscript9.dll abaixo) que acompanha e dá suporte ao Internet Explorer 11. Esse mecanismo está congelado no tempo e permanece basicamente inalterado desde o lançamento do Win8.1/IE11.  
  
-   O novo mecanismo Chakra (também chamado de *mecanismo de Borda* ou chakra.dll abaixo) que acompanha e dá suporte ao novo navegador no Windows 10, o Microsoft Edge. Esse mecanismo será atualizado continuamente e dará suporte a um mecanismo de [borda](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx) "vivo". Uma mecanismo de borda vivo implica que, ao contrário o mecanismo herdado, o mecanismo de borda não preservaria nenhuma forma de funcionalidade de script de controle de versão a ser escolhida.  
  
 Ao criar um aplicativo usando a API de JsRT (hospedagem do tempo de execução do JavaScript), você pode escolher como destino o mecanismo herdado ou o mecanismo de Borda.  
  
-   Se você precisar enfatizar a compatibilidade com versões anteriores de seus aplicativos existentes, escolha o mecanismo herdado como destino.  
  
-   Se você quiser que seu aplicativo seja voltado para o futuro e dê suporte a novos recursos do JavaScript conforme eles forem lançados (por exemplo, ECMAScript 6), use o mecanismo de Borda como destino.  
  
 Este tópico inclui detalhes que descrevem como direcionar para os diferentes mecanismos.  
  
## <a name="target-your-preferred-version"></a>Direcionar para sua versão de preferência  
 Ao criar um aplicativo, você pode selecionar a versão do JsRT que dá suporte ao mecanismo de Borda ou ao mecanismo herdado. Você pode escolher a versão de JsRT com base nas diretrizes acima. Para acomodar essas diferenças, as alterações a seguir foram feitas para `JsCreateRuntime`, `JsCreateContext` e `JsStartDebugging`.  
  
 Para `JsCreateRuntime`:  
  
-   Quando o objetivo é o mecanismo herdado, o valor de enumeração `JsRuntimeVersionEdge` é preterido e uma mensagem sugere o uso do valor `JsRuntimeVersionInternetExplorer11` em seu lugar.  
  
-   Ao usar o mecanismo de Borda como destino, o parâmetro de versão é omitido da função `JsCreateRuntime`.  
  
    ```cpp  
    JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
    ```  
  
 Para `JsCreateContext` e `JsStartDebugging`:  
  
-   Quando o objetivo é o mecanismo herdado, a interface `IDebugApplication` é usada para fornecer seus próprios métodos de depuração não remota. Para fins de depuração, as funções `JsCreateContext` e `JsStartDebugging` usam `IDebugApplication` como parâmetro.  
  
-   Ao usar o mecanismo de Borda como destino, a interface `IDebugApplication` é preterida. O mecanismo Chakra nativo habilita a funcionalidade de depuração nativa e de script por meio do depurador do Visual Studio, sem a necessidade de uma implementação de `IDebugApplication` pelo usuário. Como resultado, a interface não é mais um parâmetro para `JsCreateContext` e `JsStartDebugging`.  
  
 As assinaturas para as APIs anteriores no mecanismo herdado são conforme demonstrado a seguir:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsRuntimeVersion version, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, IDebugApplication *debugApplication, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging(IDebugApplication *debugApplication);  
```  
  
 As assinaturas para as APIs anteriores no mecanismo de Borda são conforme demonstrado a seguir:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging();  
```  
  
## <a name="compile-for-your-preferred-version-using-visual-c"></a>Compilar para sua versão de preferência usando o Visual C++  
 Ao usar o Visual C++, importe a API de JsRT incluindo o cabeçalho jsrt.h e certifique-se de que jsrt.lib está incluído na lista de arquivos de entrada do vinculador:  
  
```cpp  
#include <jsrt.h>  
```  
  
 ![Adicionando jsrt.lib como um arquivo de entrada do vinculador](../chakra-hosting/media/js-chakra.png "JS_Chakra_")  
  
 Se você deseja usar os binários do mecanismo de borda como destino, você precisará definir a macro `USE_EDGEMODE_JSRT` antes de incluir jsrt.h e, em vez de vincular a jsrt.lib, você deve vincular a chakrart.lib:  
  
```cpp  
#define USE_EDGEMODE_JSRT  
#include <jsrt.h>  
```  
  
 ![Adicionando chakrart.lib como um arquivo de entrada do vinculador](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting_")  
  
 Se você está começando com um novo aplicativo, você agora está pronto para começar a escrever código para a API de JsRT.  
  
## <a name="compile-for-your-preferred-version-using-net"></a>Compilar para sua versão de preferência usando o .NET  
 Se você estiver usando o .NET e P/Invoke, você deverá alterar suas declarações [DllImport] de API de JsRT para importar chakra.dll em vez de jscript9.dll. Além disso, altere a definição de `JsCreateRuntime` para remover o parâmetro `JsRuntimeVersion` e a definição de `JsCreateContext` e `JsStartDebugging` para remover o parâmetro `IDebugApplication`.  
  
 Para o mecanismo herdado, use o código a seguir.  
  
```c#  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsRuntimeVersion version,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    IDebugApplication debugApplication,  
    out JsContextRef newContext  
);   
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsStartDebugging(  
    IDebugApplication debugApplication,  
);  
```  
  
 Para o mecanismo de Borda, use o código a seguir.  
  
```c#  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    out JsContextRef newContext  
);   
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsStartDebugging();  
```  
  
> [!CAUTION]
>  Se você estiver efetuando marshaling manual do ponteiro de função (por exemplo, por meio de LoadLibrary/GetProcAddress), é essencial que você não misture as declarações do método, caso contrário, você desbalanceará a pilha, o que resultará em um comportamento imprevisível como falha no aplicativo. O mesmo problema ocorrerá se você executar uma pesquisa e substituição global de instâncias de jscript9.dll em seu código de importação, porque você perderá o parâmetro `version` sendo descartado.  
  
## <a name="summary"></a>Resumo  
 No Windows 10, as APIs de hospedagem de tempo de execução do JavaScript estão sendo dividas em duas. Essas APIs agora dão suporte a um mecanismo de Borda “vivo”, cujos recursos de idioma serão alinhados com a mecanismo de Borda “vivo” no Microsoft Edge. Você pode aproveitar esses recursos dos seus aplicativos de área de trabalho ou da Windows Store para criar formas novas e interessantes de estender o seu aplicativo e para aproveitar as habilidades de Web modernas em sua base de código existente. No entanto, como há diferenças sutis entre as versões anteriores, você deve estar atento os seguintes pontos ao usar como destino o mecanismo de borda ou o mecanismo herdado.  
  
-   Seu aplicativo pode dar suporte a apenas uma versão de JsRT por processo.  
  
     Por exemplo, você não pode criar um tempo de execução do mecanismo de borda e, em seguida, um tempo de execução do mecanismo herdado e esperar que eles sejam executados corretamente no mesmo processo. Não há suporte para esse procedimento, que pode resultar em comportamento não documentado, assim como falha ao carregar a segunda DLL.  
  
-   Quando o objetivo é o mecanismo de borda, seu aplicativo pode adquirir novos recursos inesperadamente quando a plataforma subjacente é atualizada automaticamente.  
  
     Por exemplo, o Internet Explorer 11 modo de tempo de execução herdado dá suporte a declarações de variável de escopo de bloco, tais como `let` e `const`. Se o comportamento de controle de versão automático do mecanismo de Borda tivesse sido o padrão anteriormente, um determinado código que funcionava no modo do Internet Explorer 10, que não tinha regras de escopo de bloco, poderia ter começado a falhar quando a plataforma tivesse sido atualizada automaticamente. Isso deve ser algo a considerar ao escolher qual modelo de tempo de execução usar. Embora acreditemos que você deva ter como destino o mecanismo de Borda sempre que possível, você deve ter cuidado com o uso de estruturas de código JavaScript que podem se tornar inválidas no futuro.  
  
-   O JsRT para a Windows Store dá suporte apenas ao mecanismo de Borda (chakra.dll). Aplicativos que tentem vincular a qualquer API de JsRT em jscript9.dll terão falha na certificação.  
  
-   É essencial que você não confunda a declaração de `JsCreateRuntime`, `JsCreateContext` e `JsStartDebugging` entre jscript9.dll e chakra.dll, porque isso resultará em desbalanceamento da pilha.  
  
     Ao usar C e C++, se você tentar usar a declaração errada, você receberá um erro de vinculador, desde que você não esteja fazendo algo como chamar `LoadLibrary` e depois `GetProcAddress`. Os desenvolvedores do .NET podem não encontrar esse problema tão facilmente, então faça uma dupla verificação do seu código ao usar esse recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de tempo de execução do JavaScript](../chakra-hosting/javascript-runtime-hosting.md)
