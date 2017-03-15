---
title: "T&#233;cnicas de depura&#231;&#227;o MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AfxEnableMemoryTracking"
  - "CMemoryState"
  - "delayFreeMemDF"
  - "checkAlwaysMemDF"
  - "vs.debug.mfc"
  - "vs.debug.objects.dump"
  - "vs.debug.memory.dump"
  - "allocMemDF"
  - "afxMemDF"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depuração [MFC]"
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# T&#233;cnicas de depura&#231;&#227;o MFC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você estiver depurando um programa MFC, essas técnicas de depuração podem ser útil.  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [AfxDebugBreak](#BKMK_AfxDebugBreak)  
  
 [A macro TRACE](#BKMK_The_TRACE_macro)  
  
 [Detectando perdas de memória no MFC](#BKMK_Memory_leak_detection_in_MFC)  
  
-   [Acompanhando alocações de memória](#BKMK_Tracking_memory_allocations)  
  
-   [Habilitar o diagnóstico de memória](#BKMK_Enabling_memory_diagnostics)  
  
-   [Tirando instantâneos de memória](#BKMK_Taking_memory_snapshots)  
  
-   [Exibindo estatísticas de memória](#BKMK_Viewing_memory_statistics)  
  
-   [Obtendo despejos de objeto](#BKMK_Taking_object_dumps)  
  
    -   [Interpretando despejos de memória](#BKMK_Interpreting_memory_dumps)  
  
    -   [Personalizando despejos de objeto](#BKMK_Customizing_object_dumps)  
  
     [Reduzindo o tamanho de uma compilação de depuração do MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
    -   [Criando um aplicativo do MFC com informações de depuração para os módulos selecionados](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
##  <a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak  
 MFC fornece um relacionamento especial [AfxDebugBreak](../Topic/AfxDebugBreak%20\(MFC\).md) função para codificar pontos de interrupção no código\-fonte:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Em plataformas Intel, `AfxDebugBreak` produz o seguinte código, que é interrompido na fonte de código em vez de código kernel:  
  
```  
_asm int 3  
```  
  
 Em outras plataformas, `AfxDebugBreak` simplesmente chama `DebugBreak`.  
  
 Certifique\-se de remover `AfxDebugBreak` instruções ao criar uma versão de compilação ou usar `#ifdef _DEBUG` para delimitá\-los.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_TRACE_macro"></a> A macro TRACE  
 Para exibir mensagens do seu programa no depurador [janela saída](../ide/reference/output-window.md), você pode usar o [ATLTRACE](../Topic/ATLTRACE%20\(ATL\).md) macro ou a MFC [rastreamento](../Topic/TRACE.md) macro. Como [asserções](../debugger/c-cpp-assertions.md), as macros de rastreamento estão ativas somente na versão de depuração do seu programa e desaparecem quando compiladas na versão de lançamento.  
  
 Os exemplos a seguir mostram algumas das maneiras como você pode usar o **rastreamento** macro. Como `printf`, o **rastreamento** macro pode lidar com um número de argumentos.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 A macro TRACE trata adequadamente os parâmetros char \* e wchar\_t \*. Os exemplos a seguir demonstram o uso da macro TRACE junto com diferentes tipos de parâmetros de cadeia de caracteres.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 Para obter mais informações sobre o **rastreamento** macro, consulte [Serviços de diagnóstico](/visual-cpp/mfc/reference/diagnostic-services).  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Memory_leak_detection_in_MFC"></a> Detectando perdas de memória no MFC  
 MFC fornece classes e funções para detectar a memória alocada, mas nunca desalocada.  
  
###  <a name="BKMK_Tracking_memory_allocations"></a> Acompanhando alocações de memória  
 Em MFC, você pode usar a macro [DEBUG\_NEW](../Topic/DEBUG_NEW.md) em vez do **novo** vazamentos de operador para ajudar a localizar a memória. Na versão de depuração do seu programa, `DEBUG_NEW` mantém o controle do número de linha e de nome de arquivo para cada objeto que aloca. Quando você compila uma versão de lançamento do seu programa, `DEBUG_NEW` resolve para um simples **novo** operação sem os nome e a linha número informações do arquivo. Assim, você não paga nenhuma penalidade de velocidade na versão de lançamento do seu programa.  
  
 Se você não deseja reescrever o programa inteiro usar `DEBUG_NEW` no lugar de **nova**, você pode definir esta macro em seus arquivos de origem:  
  
```  
#define new DEBUG_NEW  
```  
  
 Ao fazer uma [despejo de objeto](#BKMK_Taking_object_dumps), cada objeto alocado com `DEBUG_NEW` mostrará o número de arquivo e a linha onde foi alocado, permitindo que você identifique as fontes de vazamentos de memória.  
  
 A versão de depuração da estrutura MFC usa `DEBUG_NEW` automaticamente, mas não seu código. Se você quiser que os benefícios de `DEBUG_NEW`, você deve usar `DEBUG_NEW` explicitamente ou **\#define novos** conforme mostrado acima.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Enabling_memory_diagnostics"></a> Habilitar o diagnóstico de memória  
 Antes de poder usar os recursos de diagnóstico de memória, você deve habilitar o rastreamento de diagnóstico.  
  
 **Para habilitar ou desabilitar o diagnóstico de memória**  
  
-   Chame a função global [AfxEnableMemoryTracking](../Topic/AfxEnableMemoryTracking.md) para habilitar ou desabilitar o alocador de diagnóstico de memória. Porque o diagnóstico de memória é ativados por padrão na biblioteca de depuração, você normalmente usará essa função para desativá\-la, temporariamente, que aumenta a velocidade de execução do programa e reduz a saída de diagnóstico.  
  
 **Para selecionar os recursos de diagnóstico de memória específicos com afxMemDF**  
  
-   Se você quiser um controle mais preciso sobre os recursos de diagnóstico de memória, você pode seletivamente ativar os recursos de diagnóstico de memória individuais e desativar definindo o valor da variável global MFC [afxMemDF](../Topic/afxMemDF.md). Essa variável pode ter os seguintes valores conforme especificado pelo tipo enumerado **afxMemDF**.  
  
    |Valor|Descrição|  
    |-----------|---------------|  
    |**allocMemDF**|Ative o alocador de diagnóstico de memória \(padrão\).|  
    |**delayFreeMemDF**|Atrase a liberação de memória ao chamar `delete` ou `free` até que o programa será encerrado. Isso fará com que o programa alocar o máximo possível de memória.|  
    |**checkAlwaysMemDF**|Chamar [AfxCheckMemory](../Topic/AfxCheckMemory.md) sempre que a memória é alocada ou liberada.|  
  
     Esses valores podem ser usados em combinação executando uma operação OR lógica, como mostrado aqui:  
  
    ```cpp  
    afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
    ```  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_memory_snapshots"></a> Tirando instantâneos de memória  
  
1.  Criar um [CMemoryState](http://msdn.microsoft.com/pt-br/8fade6e9-c6fb-4b2a-8565-184a912d26d2) objeto e chamar o [CMemoryState::Checkpoint](../Topic/CMemoryState::Checkpoint.md) função de membro. Isso cria o primeiro instantâneo de memória.  
  
2.  Depois que o programa executa suas operações de alocação e desalocação de memória, criar outro `CMemoryState` objeto e chamada `Checkpoint` para esse objeto. Obtém um segundo instantâneo do uso da memória.  
  
3.  Crie um terceiro `CMemoryState` objeto e chamar seu [CMemoryState::Difference](../Topic/CMemoryState::Difference.md) função de membro, fornecendo como argumentos os dois anteriores `CMemoryState` objetos. Se houver uma diferença entre os dois estados da memória, o `Difference` função retorna um valor diferente de zero. Isso indica que alguns blocos de memória não foram desalocados.  
  
     Este exemplo mostra o código que se parece com:  
  
    ```  
    // Declare the variables needed  
    #ifdef _DEBUG  
        CMemoryState oldMemState, newMemState, diffMemState;  
        oldMemState.Checkpoint();  
    #endif  
  
        // Do your memory allocations and deallocations.  
        CString s("This is a frame variable");  
        // The next object is a heap object.  
       CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
  
    #ifdef _DEBUG  
        newMemState.Checkpoint();  
        if( diffMemState.Difference( oldMemState, newMemState ) )  
        {  
            TRACE( "Memory leaked!\n" );  
        }  
    #endif  
    ```  
  
     Observe que as instruções de verificação de memória são envolvidas por `#ifdef` [\_DEBUG](/visual-cpp/c-runtime-library/debug)\/ **\#endif** blocos para que elas sejam compiladas apenas em versões de depuração do seu programa.  
  
     Agora que você sabe que existe um vazamento de memória, você pode usar outra função de membro [CMemoryState::DumpStatistics](../Topic/CMemoryState::DumpStatistics.md) que ajudarão você a localizá\-lo.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Viewing_memory_statistics"></a> Exibindo estatísticas de memória  
 O [CMemoryState::Difference](../Topic/CMemoryState::Difference.md) função analisa dois objetos de estado da memória e detecta todos os objetos não desalocados do heap entre os estados inicial e final. Depois de ter instantâneos da memória e comparado\-os usando `CMemoryState::Difference`, você pode chamar [CMemoryState::DumpStatistics](../Topic/CMemoryState::DumpStatistics.md) para obter informações sobre os objetos que não foram desalocados.  
  
 Considere o exemplo a seguir:  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpStatistics();  
}  
```  
  
 Um despejo de exemplo do exemplo tem esta aparência:  
  
```  
0 bytes in 0 Free Blocks  
22 bytes in 1 Object Blocks  
45 bytes in 4 Non-Object Blocks  
Largest number used: 67 bytes  
Total allocations: 67 bytes  
```  
  
 Blocos livres são os blocos cuja desalocação será atrasada se `afxMemDF` foi definido como `delayFreeMemDF`.  
  
 Blocos de objeto comuns, mostrados na segunda linha, permanecem alocados no heap.  
  
 Blocos de objeto não incluem as matrizes e estruturas alocadas com `new`. Nesse caso, quatro blocos não\-objeto foram alocados no heap, mas não desalocados.  
  
 `Largest number used` fornece o máximo de memória usada pelo programa a qualquer momento.  
  
 `Total allocations` Retorna a quantidade total de memória usada pelo programa.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_object_dumps"></a> Obtendo despejos de objeto  
 Em um programa MFC, você pode usar [CMemoryState::DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md) para despejar uma descrição de todos os objetos no heap que não foram desalocados.`DumpAllObjectsSince` Despeja todos os objetos alocados desde o último [CMemoryState::Checkpoint](../Topic/CMemoryState::Checkpoint.md). Se nenhum `Checkpoint` chamada tiver ocorrido, `DumpAllObjectsSince` Despeja todos os objetos e não objetos atualmente na memória.  
  
> [!NOTE]
>  Antes de poder usar o despejo de objeto do MFC, você deve [Habilitar rastreamento de diagnóstico](../debugger/mfc-debugging-techniques.md#BKMK_Enabling_Memory_Diagnostics).  
  
> [!NOTE]
>  O MFC Despeja automaticamente todos os objetos vazados quando o programa é encerrado, portanto você não precisa criar código para despejar objetos nesse momento.  
  
 O código a seguir testa um vazamento de memória comparando dois estados de memória e despeja todos os objetos se um vazamento for detectado.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 O conteúdo do despejo tem esta aparência:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Os números entre chaves no início da maioria das linhas especificam a ordem na qual os objetos foram alocados. O objeto alocado mais recentemente tem o número mais alto e aparece na parte superior do despejo.  
  
 Para obter o máximo de informações fora do despejo de um objeto, você pode substituir o `Dump` a função de membro de qualquer `CObject`\-objeto para personalizar o despejo do objeto derivado.  
  
 Você pode definir um ponto de interrupção em uma alocação de memória específico, definindo a variável global `_afxBreakAlloc` para o número mostrado entre chaves. Se você executar novamente o programa o depurador interromperá a execução quando essa alocação. Em seguida, você pode examinar a pilha de chamadas para ver como o programa chegou a esse ponto.  
  
 A biblioteca de tempo de execução C tem uma função semelhante, [\_CrtSetBreakAlloc](/visual-cpp/c-runtime-library/reference/crtsetbreakalloc), que você pode usar para alocações de tempo de execução C.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Interpreting_memory_dumps"></a> Interpretando despejos de memória  
 Observe este despejo de objeto mais detalhadamente:  
  
```  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 O programa que gerou este despejo tinha apenas duas alocações explícitas — uma na pilha e uma no heap:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 O `CPerson` construtor usa três argumentos são ponteiros para `char`, que são usados para inicializar `CString` variáveis de membro. O despejo de memória, você pode ver o `CPerson` objeto juntamente com três blocos diferentes de objeto \(3, 4 e 5\). Eles mantêm os caracteres para o `CString` variáveis de membro e não será excluído quando o `CPerson` objeto destruidor é invocado.  
  
 Bloco número 2 é o `CPerson` objeto propriamente dito.`$51A4` representa o endereço do bloco e é seguido pelo conteúdo do objeto, que eram gerados pelo `CPerson`::`Dump` quando chamado por [DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md).  
  
 Você pode imaginar que o bloco número 1 está associado a `CString` variável de quadro devido a seu número de seqüência e o tamanho, o que corresponde ao número de caracteres no quadro `CString` variável. As variáveis alocadas no quadro são desalocadas automaticamente quando o quadro sai do escopo.  
  
 **Variáveis de quadro**  
  
 Em geral, você não deverá preocupar objetos heap associados a variáveis do quadro porque eles são desalocados automaticamente quando as variáveis do quadro saem do escopo. Para evitar a confusão em seu despejos de diagnóstico de memória, você deve posicionar suas chamadas para `Checkpoint` para que fiquem fora do escopo de variáveis do quadro. Por exemplo, coloque colchetes de escopo em todo o código de alocação anterior, conforme mostrado aqui:  
  
```  
oldMemState.Checkpoint();  
{  
    // Do your memory allocations and deallocations ...  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
}  
newMemState.Checkpoint();  
```  
  
 Com os colchetes de escopo em vigor, o despejo de memória para este exemplo é o seguinte:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
```  
  
 **Alocações diferentes de objeto**  
  
 Observe que algumas alocações são objetos \(como `CPerson`\) e algumas são alocações diferentes de objeto. "As alocações" são alocações para os objetos não derivados de `CObject` ou alocações de tipos C primitivos como `char`, `int`, ou **longo**. Se o **CObject**classe derivada aloca espaço adicional, como para buffers internos, esses objetos mostrarão as alocações de objeto e diferentes de objeto.  
  
 **Evitando vazamentos de memória**  
  
 Observe no código acima que o bloco de memória associado a `CString` variável de quadro foi desalocado automaticamente e não aparecem como um vazamento de memória. A desalocação automática associada regras de escopo cuida da maioria dos vazamentos de memória associados a variáveis do quadro.  
  
 Para objetos alocados no heap, no entanto, você deve excluir explicitamente o objeto para evitar um vazamento de memória. Para limpar o último vazamento de memória no exemplo anterior, exclua o `CPerson` objeto alocado no heap, da seguinte maneira:  
  
```  
{  
    // Do your memory allocations and deallocations.  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
    delete p;  
}  
```  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Customizing_object_dumps"></a> Personalizando despejos de objeto  
 Quando você deriva uma classe de [CObject](/visual-cpp/mfc/reference/cobject-class), você pode substituir o `Dump` a função de membro para fornecer informações adicionais quando você usa [DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md) para despejar objetos para o [janela saída](../ide/reference/output-window.md).  
  
 O `Dump` função grava uma representação textual do membro do objeto variáveis a um contexto de despejo \([CDumpContext](/visual-cpp/mfc/reference/cdumpcontext-class)\). O contexto de despejo é semelhante a um fluxo de e\/s. Você pode usar o operador de anexação \(**\<\<**\) para enviar dados a um `CDumpContext`.  
  
 Ao substituir o `Dump` função, primeiro você deve chamar a versão da classe base de `Dump` para despejar o conteúdo do objeto da classe base. Saída, em seguida, uma descrição textual e o valor de cada variável de membro da sua classe derivada.  
  
 A declaração do `Dump` função tem esta aparência:  
  
```  
class CPerson : public CObject  
{  
public:  
#ifdef _DEBUG  
    virtual void Dump( CDumpContext& dc ) const;  
#endif  
  
    CString m_firstName;  
    CString m_lastName;  
    // And so on...  
};  
```  
  
 Porque o objeto de despejo só faz sentido quando você estiver depurando seu programa, a declaração do `Dump` função é agrupada com um **\#ifdef DEBUG \/ \#endif** bloco.  
  
 No exemplo a seguir, o `Dump` função primeiro chama o `Dump` função para sua classe base. Em seguida, ele grava uma breve descrição de cada variável de membro junto com o valor do membro no fluxo de diagnóstico.  
  
```  
#ifdef _DEBUG  
void CPerson::Dump( CDumpContext& dc ) const  
{  
    // Call the base class function first.  
    CObject::Dump( dc );  
  
    // Now do the stuff for our specific class.  
    dc << "last name: " << m_lastName << "\n"  
        << "first name: " << m_firstName << "\n";  
}  
#endif  
```  
  
 Você deve fornecer um `CDumpContext` argumento para especificar onde a saída de despejo vai. A versão de depuração do MFC fornece um modelo predefinido `CDumpContext` objeto chamado `afxDump` que envia a saída para o depurador.  
  
```  
CPerson* pMyPerson = new CPerson;  
// Set some fields of the CPerson object.  
//...  
// Now dump the contents.  
#ifdef _DEBUG  
pMyPerson->Dump( afxDump );  
#endif  
```  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Reduzindo o tamanho de uma compilação de depuração do MFC  
 As informações de depuração para um aplicativo MFC grande podem ocupar muito espaço em disco. Você pode usar um dos seguintes procedimentos para reduzir o tamanho:  
  
1.  Recrie as bibliotecas MFC usando o [\/Z7, \/Zi, \/ZI \(depurar formato de informações\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) opção, em vez de **\/Z7**. Essas opções criam um arquivo de banco de dados \(PDB\) de programa único que contém informações de depuração para a biblioteca inteira, reduzindo a redundância e economizando espaço.  
  
2.  Recrie as bibliotecas MFC sem informações de depuração \(nenhum [\/Z7, \/Zi, \/ZI \(depurar formato de informações\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) opção\). Nesse caso, a falta de informações de depuração impedirá você de usar a maioria dos recursos do depurador no código da biblioteca MFC, mas como as bibliotecas MFC já estão completamente depuradas, isso pode não ser um problema.  
  
3.  Crie seu próprio aplicativo com informações de depuração para os módulos selecionados apenas como descrito abaixo.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Criando um aplicativo do MFC com informações de depuração para os módulos selecionados  
 Criar os módulos selecionados com as bibliotecas de depuração MFC permite usar a depuração e outros recursos nesses módulos. Esse procedimento utiliza dois de depuração e versão modos de makefile do Visual C\+\+, necessitando das alterações descritas nas etapas a seguir \(e também necessário fazer um "Recompilar tudo" quando uma compilação de versão completa é necessária\).  
  
1.  No Gerenciador de Soluções, selecione o projeto.  
  
2.  Do **exibição** menu, selecione **páginas de propriedade**.  
  
3.  Primeiro, você criará uma nova configuração de projeto.  
  
    1.  No **\< projeto \> páginas de propriedade** caixa de diálogo, clique o **do Configuration Manager** botão.  
  
    2.  No [caixa de diálogo Gerenciador de configuração](http://msdn.microsoft.com/pt-br/fa182dca-282e-4ae5-bf37-e155344ca18b), localize seu projeto na grade. No **configuração** coluna, selecione **\< Novo … \>**.  
  
    3.  No [caixa de diálogo nova configuração de projeto](http://msdn.microsoft.com/pt-br/cca616dc-05a6-4fe3-bdc1-40c72a66f2be), digite um nome para a nova configuração, como "Depuração parcial", o **nome de configuração do projeto** caixa.  
  
    4.  No **Copiar configurações de** escolha **versão**.  
  
    5.  Clique em **OK** para fechar o **nova configuração de projeto**caixa de diálogo.  
  
    6.  Feche o **do Configuration Manager** caixa de diálogo.  
  
4.  Agora, você irá definir opções para todo o projeto.  
  
    1.  No **páginas de propriedade** caixa de diálogo de **Propriedades de configuração** pasta, selecione o **geral** categoria.  
  
    2.  Na grade de configurações de projeto, expanda **padrões de projeto** \(se necessário\).  
  
    3.  Em **padrões de projeto**, localizar **uso do MFC**. A configuração atual aparece na coluna à direita da grade. Clique na configuração atual e altere\-a para **Usar MFC em uma biblioteca estática**.  
  
    4.  No painel esquerdo do **páginas de propriedades** caixa de diálogo, abra o **C\/C\+\+** pasta e selecione **pré\-processador**. Na grade de propriedades, localize **definições de pré\-processador** e substitua "NDEBUG" por debug".  
  
    5.  No painel esquerdo do **páginas de propriedades** caixa de diálogo, abra o **vinculador** pasta e selecione o **entrada** categoria. Na grade de propriedades, localize **dependências adicionais**. No **dependências adicionais** configuração, digite "NAFXCWD. LIB"e"LIBCMT".  
  
    6.  Clique em **OK** para salvar as novas opções de compilação e fechar o **páginas de propriedade** caixa de diálogo.  
  
5.  Do **criar** menu, selecione **recriar**. Isso remove todas as informações de depuração de seus módulos, mas não afeta a biblioteca MFC.  
  
6.  Agora você deve adicionar as informações de depuração para os módulos selecionados em seu aplicativo. Lembre\-se de que você pode definir pontos de interrupção e executar outras funções de depurador apenas nos módulos que você compilou com informações de depuração. Para cada arquivo de projeto no qual você deseja incluir informações de depuração, execute as seguintes etapas:  
  
    1.  No Solution Explorer, abra o **arquivos de origem** pasta localizada em seu projeto.  
  
    2.  Selecione o arquivo que você deseja definir informações de depuração.  
  
    3.  Do **exibição** menu, selecione **páginas de propriedade**.  
  
    4.  No **páginas de propriedade** caixa de diálogo o **configurações** pasta, abra o **C\/C\+\+** em seguida, selecione uma pasta a **geral** categoria.  
  
    5.  Na grade de propriedades, localize **formato informações de depuração.**  
  
    6.  Clique o **formato informações de depuração** configurações e selecione a opção desejada \(normalmente **\/ZI**\) para obter informações de depuração.  
  
    7.  Se você estiver usando um aplicativo gerado pelo Assistente de aplicativo ou tê cabeçalhos pré\-compilados, você precisa desativar os cabeçalhos pré\-compilados ou recompilá\-los antes de compilar os outros módulos. Caso contrário, você receberá o aviso C4650 e mensagens de erro C2855. Você pode desligar cabeçalhos pré\-compilados alterando a **criar\/usar cabeçalho pré\-compilado** definindo no **\< projeto \> propriedades** caixa de diálogo \(**Propriedades de configuração** pasta, **C\/C\+\+** subpasta **cabeçalhos pré\-compilados** categoria\).  
  
7.  Do **criar** menu, selecione **criar** para recriar os arquivos de projeto que estão desatualizados.  
  
 Como uma alternativa à técnica descrita neste tópico, você pode usar um makefile externo para definir as opções individuais para cada arquivo. Nesse caso, para vincular com as bibliotecas de depuração MFC, você deve definir o [Debug](/visual-cpp/c-runtime-library/debug) sinalizador para cada módulo. Se você quiser usar bibliotecas de versão MFC, você deve definir NDEBUG. Para obter mais informações sobre como escrever makefiles externos, consulte o [referência a NMAKE](/visual-cpp/build/running-nmake).  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
## Consulte também  
 [Depuração do Visual C\+\+](../debugger/debugging-native-code.md)