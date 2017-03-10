---
title: "Detalhes da pilha de depura&#231;&#227;o CRT | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Macro _BLOCK_SUBTYPE"
  - "Macro _BLOCK_TYPE"
  - "Macro _CLIENT_BLOCK"
  - "Macro _CRT_BLOCK"
  - "Variável global _crtBreakAlloc"
  - "Função _CrtCheckMemory"
  - "Macro _CRTDBG_ALLOC_MEM_DF"
  - "Macro _CRTDBG_CHECK_ALWAYS_DF"
  - "Macro _CRTDBG_CHECK_CRT_DF"
  - "Macro _CRTDBG_DELAY_FREE_MEM_DF"
  - "Macro _CRTDBG_LEAK_CHECK_DF"
  - "Função _crtDbgFlag"
  - "Função _CrtDoForAllClientObjects"
  - "Função _CrtDumpMemoryLeaks"
  - "Função _CrtMemBlockHeader"
  - "Função _CrtMemCheckpoint"
  - "Função _CrtMemDifference"
  - "Função _CrtMemDumpAllObjectsSince"
  - "Função _CrtMemDumpStatistics"
  - "Função _CrtMemState"
  - "Função _CrtReportBlockType"
  - "Função _CrtSetBreakAlloc"
  - "Função _CrtSetDbgFlag"
  - "Função _CrtSetDumpClient"
  - "Bloco _FREE_BLOCK"
  - "Bloco _IGNORE_BLOCK"
  - "Bloco _NORMAL_BLOCK"
  - "números de solicitação de alocação"
  - "blocos, tipos de heap de depuração"
  - "blocos de cliente, especificando subtipos"
  - "Variável global crtBreakAlloc"
  - "Arquivo DBGINT.H"
  - "depurar compilações, vinculando ao heap de depuração"
  - "heap de depuração"
  - "heap de depuração, acessando"
  - "heap de depuração, CRT"
  - "heap de depuração, blocos de memória"
  - "heap de depuração, funções de relatórios"
  - "heap de depuração, resolvendo problemas de alocação de memória"
  - "heap de depuração, rastreando solicitações de alocação de heap"
  - "heap de depuração, usando de C++"
  - "depurando [C++], Suporte à depuração CRT"
  - "depurando [C++], heap de depuração"
  - "depuração [CRT], problemas relacionados a heap"
  - "depurando [Visual Studio], heap de depuração"
  - "depurando perdas de memória"
  - "Operador delete, usando heap de depuração de C++"
  - "alocação de heap, depurar"
  - "alocação de heap, rastreando solicitações"
  - "Funções heap"
  - "funções de relatórios de estado de heap"
  - "alocação de memória, heap de depuração"
  - "blocos de memória, tipos de alocação no heap de depuração"
  - "blocos de memória, free"
  - "perdas de memória, Funções de biblioteca de depuração CRT"
  - "perdas de memória, acompanhando"
  - "memória, depuração"
  - "Método nBlockUse"
  - "Operador new, usando heap de depuração de C++"
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Detalhes da pilha de depura&#231;&#227;o CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico fornece um aspecto detalhado na heap de depuração de CRT.  
  
##  <a name="BKMK_Contents"></a> Conteúdo  
 [Localizar estouros de buffer com heap de depuração](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Tipos de blocos na heap de depuração](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Verifique a integridade e vazamentos de memória do heap](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Configurar o heap de depuração](#BKMK_Configure_the_debug_heap)  
  
 [novo, excluir, e _CLIENT_BLOCKs na depuração de criar C++](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Funções de relatório do estado heap](#BKMK_Heap_State_Reporting_Functions)  
  
 [Solicitações de alocação da heap de rastreamento](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Localizar estouros de buffer com heap de depuração  
 Dois dos problemas intratáveis mais comuns que os programadores encontram estão substituindo o final de um buffer alocado e os vazamentos de memória \(não liberam alocações depois que não são mais necessários.\)  O heap de depuração fornece ferramentas avançadas para resolver problemas de alocação de memória desse tipo.  
  
 As versões de depuração de funções heap chamam o padrão ou as versões de base usadas nas compilações da release.  Quando você solicita um bloco de memória, o gerenciador da heap de depuração aloca um bloco de memória ligeiramente maior do que o solicitado da heap de base e retorna um ponteiro para sua parte desse bloco.  Por exemplo, suponha que seu aplicativo contém a chamada: `malloc( 10 )`.  Em uma compilação de Versão, [malloc](/visual-cpp/c-runtime-library/reference/malloc) chamaria a rotina de alocação da heap base que solicita uma alocação de 10 bytes.  Entretanto, em uma compilação de Depuração, `malloc` chamaria [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg) que, por sua vez, chamaria a rotina de alocação de heap de base solicitando uma alocação de 10 bytes mais aproximadamente 36 bytes de memória adicional.  Todos os blocos de memória resultantes no heap de depuração estão conectados em uma única lista vinculada, ordenados de acordo com a data em que foram alocados.  
  
 Memória adicional alocada por rotinas da heap de depuração é usada para informações de contabilidade, para ponteiros que vinculam blocos de memória de depuração juntos, e para buffers pequenos em ambos os lados de seus dados para capturar substituições da região alocada.  
  
 Atualmente, a estrutura de cabeçalho de bloco usada para armazenar informações para contabilidade de heap de depuração são declaradas da seguinte forma no arquivo de cabeçalho DBGINT.H:  
  
```  
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 Os buffers de `NoMansLand` em ambos os lados da área de dados do usuário do bloco estão atualmente com 4 bytes de tamanho, e são preenchidos com um valor conhecido de bytes usado por rotinas de heap de depuração para verificar se os limites do bloco de memória de usuário não foram substituídos.  O heap de depuração também preenche novos blocos de memória com um valor conhecido.  Se você optar por manter blocos liberados na lista vinculada da heap como explicado abaixo, esses blocos liberados também serão preenchidos com um valor conhecido.  Atualmente, os valores reais de bytes são usados como segue:  
  
 NoMansLand \(0xFD\)  
 Os buffers de “NoMansLand” em ambos os lados de memória usados pelo aplicativo são preenchidos com 0xFD atualmente.  
  
 Blocos liberados \(0xDD\)  
 Os blocos liberados mantidos não usados na lista vinculada da heap de depuração quando o sinalizador de `_CRTDBG_DELAY_FREE_MEM_DF` for ajustado serão preenchidos com 0xDD atualmente.  
  
 Novos objetos \(0xCD\)  
 Novos objetos são preenchidos com 0xCD quando são alocados.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Tipos de blocos na heap de depuração  
 Cada bloco de memória no heap de depuração é atribuído a um dos cinco tipos de alocação.  Esses tipos são controlados e relatados de maneira diferente para fins de relatórios de estado e de detecção de vazamento.  Você pode especificar o tipo de bloco atribuindo\-o e usando uma chamada direta para uma das funções de alocação do heap de depuração como [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  Os cinco tipos de blocos de memória no heap de depuração \(definido no membro de **nBlockUse** da estrutura de **\_CrtMemBlockHeader**\) são:  
  
 **\_NORMAL\_BLOCK**  
 Uma chamada para [malloc](/visual-cpp/c-runtime-library/reference/malloc) ou a [calloc](/visual-cpp/c-runtime-library/reference/calloc) cria um bloco normal.  Se você pretende usar somente os blocos Normais, e se não tiver necessidade de blocos Clientes, talvez queira definir [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc), que fará com que todas as chamadas de alocação de heap sejam mapeadas para os equivalentes de depuração em compilações de Depuração.  Isso permitirá que informações de número de linha e de nome de arquivo sobre cada chamada de alocação sejam armazenadas no cabeçalho de bloco correspondente.  
  
 `_CRT_BLOCK`  
 Os blocos de memória alocados internamente por muitas funções da biblioteca em tempo de execução são marcados como blocos de CRT para que possam ser tratados separadamente.  Como resultado, a detecção de escape e outras operações não precisam ser afetadas por eles.  Uma alocação nunca deve atribuir, realocar ou liberar qualquer bloco do tipo CRT.  
  
 `_CLIENT_BLOCK`  
 Um aplicativo pode manter um acompanhamento especial de um determinado grupo de alocações para fins de depuração alocando\-as como esse tipo de bloco de memória, usando chamadas explícitas para funções de heap de depuração.  O MFC, por exemplo, aloca qualquer **CObjects** como blocos de Cliente; outros aplicativos podem manter objetos diferentes de memória em blocos de Cliente.  Os subtipos de blocos de cliente também podem ser especificados para maior granularidade de rastreamento.  Para especificar subtipos de blocos de cliente, desloque o número à esquerda por 16 bits e `OR` com `_CLIENT_BLOCK`.  Por exemplo:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Uma função de cliente fornecida pelo cliente para despejar objetos armazenados em blocos de clientes pode ser instalada usando [\_CrtSetDumpClient](/visual-cpp/c-runtime-library/reference/crtsetdumpclient) e será chamada sempre que um bloco do cliente for despejado por uma função de depuração.  Além disso, [\_CrtDoForAllClientObjects](/visual-cpp/c-runtime-library/reference/crtdoforallclientobjects) pode ser usado para chamar uma função determinada fornecida pelo aplicativo para cada bloco de cliente no heap de depuração.  
  
 **\_FREE\_BLOCK**  
 Normalmente, os blocos liberados são removidos da lista.  Para verificar se a memória liberada ainda não está sendo gravada ou para simular condições de memória baixa, você optar por manter os blocos liberados na lista vinculada, marcados como livres e preenchidos com um valor conhecido de byte \(atualmente 0xDD\).  
  
 **\_IGNORE\_BLOCK**  
 É possível desativar as operações de heap de depuração por um período.  Durante este momento, blocos de memória são mantidos na lista, mas marcados como blocos Ignorar.  
  
 Para determinar o tipo e o subtipo de um bloco determinado, use a função [\_CrtReportBlockType](/visual-cpp/c-runtime-library/reference/crtreportblocktype) e as macros **\_BLOCK\_TYPE** e **\_BLOCK\_SUBTYPE**.  As macros são definidas \(em crtdbg.h\), como a seguir:  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Verifique a integridade e vazamentos de memória do heap  
 Vários dos recursos da heap de depuração devem ser acessados de dentro de seu código.  A seção a seguir descreve alguns dos recursos e como usá\-los.  
  
 `_CrtCheckMemory`  
 Você pode usar uma chamada para [\_CrtCheckMemory](/visual-cpp/c-runtime-library/reference/crtcheckmemory), por exemplo, para verificar a integridade do heap a qualquer momento.  Essa função inspeciona cada bloco de memória na heap, verifica se as informações de cabeçalho do bloco de memória são válidas, e confirma que os buffers não foram alterados.  
  
 `_CrtSetDbgFlag`  
 Você pode controlar como o heap de depuração acompanha as alocações usando um sinalizador interno, [\_crtDbgFlag](/visual-cpp/c-runtime-library/crtdbgflag), que pode ser lido e definido usando a função [\_CrtSetDbgFlag](/visual-cpp/c-runtime-library/reference/crtsetdbgflag).  Alterando este sinalizador, você pode instruir o heap de depuração para verificar vazamentos de memória quando o programa encerra e relata todos os vazamentos detectados.  Da mesma forma, você pode especificar se blocos de memória liberados não serão removidos da lista vinculada, para simular situações de memória baixa.  Quando a heap é verificada, esses blocos liberados são inspecionados em sua totalidade para garantir que não estão perturbados.  
  
 O sinalizador de **\_crtDbgFlag** contém os seguintes campos de bits:  
  
|Campo de bits|Padrão<br /><br /> Valor|Descrição|  
|-------------------|----------------------|---------------|  
|**\_CRTDBG\_ALLOC\_MEM\_DF**|On|Ativa a alocação de depuração.  Quando esse bit está desativado, as alocações permanecem encadeadas juntas, mas seu tipo de bloco é **\_IGNORE\_BLOCK**.|  
|**\_CRTDBG\_DELAY\_FREE\_MEM\_DF**|Off|Impede que a memória seja liberada realmente para simular condições de memória baixa.  Quando esse bit estiver ativado, os blocos liberados são mantidos na lista vinculada da heap de depuração, mas são marcados como **\_FREE\_BLOCK** e preenchidos com um valor especial de byte.|  
|**\_CRTDBG\_CHECK\_ALWAYS\_DF**|Off|Faz com que **\_CrtCheckMemory** seja chamado em cada alocação e desalocação.  Isso deixa a execução lenta, mas captura os erros rapidamente.|  
|**\_CRTDBG\_CHECK\_CRT\_DF**|Off|Faz com que blocos marcados como o tipo **\_CRT\_BLOCK** sejam inclusos em operações de detecção de escape e diferença de estado.  Quando esse bit está desativado, a memória usada internamente pela biblioteca em tempo de execução é ignorada durante essas operações.|  
|**\_CRTDBG\_LEAK\_CHECK\_DF**|Off|Faz com que a verificação de escape seja executada na saída do programa através de uma chamada a **\_CrtDumpMemoryLeaks**.  Um relatório de erro é gerado se o aplicativo não liberou qualquer memória atribuída.|  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Configurar o heap de depuração  
 Todas as chamadas para funções heap, como `malloc`, `free`, `calloc`, `realloc`, `new` e `delete` resolvem depurar versões dessas funções que operam no heap de depuração.  Quando você libera um bloco de memória, a heap de depuração verifica automaticamente a integridade dos buffers em ambos os lados de sua área atribuída e emite um relatório de erro case a substituição tenha ocorrido.  
  
 **Para usar a heap de depuração**  
  
-   Vincule a compilação de depuração de seu aplicativo a uma versão de depuração da biblioteca em tempo de execução do C.  
  
 **Para alterar um ou mais campos de bits \_crtDbgFlag e criar um novo estado para o sinalizador**  
  
1.  Chamar `_CrtSetDbgFlag` com o parâmetro `newFlag` definido como `_CRTDBG_REPORT_FLAG` \(para obter o estado atual de `_crtDbgFlag`\) e armazenar o valor retornado em uma variável temporária.  
  
2.  Ative todos os bits usando o operador `OR`\(bit a bit &#124; símbolo\) na variável temporária com as máscaras de bits correspondentes \(representadas no código do aplicativo por constantes de manifesto\).  
  
3.  Desative os outros bits usando o operador `AND` \(símbolo & bit a bit\) na variável com o operador `NOT` \(símbolo ~bit a bit\) das máscaras de bits apropriadas.  
  
4.  Chamar `_CrtSetDbgFlag` com o parâmetro de `newFlag` definido como o valor armazenado na variável temporária para criar o novo estado para `_crtDbgFlag`.  
  
 Por exemplo, as seguintes linhas de código ativam detecção automática de escape e desativam a verificação de blocos de tipo `_CRT_BLOCK`:  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> novo, excluir, e \_CLIENT\_BLOCKs na depuração de criar C\+\+  
 As versões de depuração de biblioteca em tempo de execução de C contêm versões de depuração do C\+\+ `new` e operadores de `delete`.  Se você usar o tipo de alocação `_CLIENT_BLOCK`, deverá chamar a versão de depuração do operador `new` diretamente ou criar macros que substituam o operador `new` no modo de depuração, como mostrado no exemplo a seguir:  
  
```  
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 A versão de depuração do operador `delete` funciona com todos os tipos de bloco e não requer nenhuma alteração em seu programa quando você compilar uma versão de lançamento.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Funções de relatório do estado heap  
 **\_CrtMemState**  
  
 Para capturar um instantâneo de resumo do estado da heap em um determinado momento, use a estrutura \_CrtMemState definida em CRTDBG.H:  
  
```  
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 Essa estrutura salva um ponteiro para o primeiro bloco \(recentemente atribuído\) na lista vinculada da heap de depuração.  Em seguida, em duas matrizes, ele registra quanto de cada tipo de bloco de memória \(\_NORMAL\_BLOCK, `_CLIENT_BLOCK`, \_FREE\_BLOCK, e assim por diante\) está na lista e o número de bytes atribuídos em cada tipo de bloco.  Finalmente, registra o maior número de bytes atribuídos no heap como um todo até esse ponto, e o número de bytes atribuídos no momento.  
  
 **Outras Funções de Relatório do CRT**  
  
 As funções a seguir informam o estado e o conteúdo da heap e usam as informações para ajudar a detectar vazamentos de memória e outros problemas.  
  
|Função|Descrição|  
|------------|---------------|  
|[\_CrtMemCheckpoint](/visual-cpp/c-runtime-library/reference/crtmemcheckpoint)|Salva um instantâneo da heap em uma estrutura de **\_CrtMemState** fornecida pelo aplicativo.|  
|[\_CrtMemDifference](/visual-cpp/c-runtime-library/reference/crtmemdifference)|Compara duas estruturas de estado de memória, salva a diferença entre elas em uma estrutura de estado e retorna VERDADEIRO se os dois estados forem diferentes.|  
|[\_CrtMemDumpStatistics](/visual-cpp/c-runtime-library/reference/crtmemdumpstatistics)|Despeja uma determinada estrutura **\_CrtMemState**.  A estrutura pode conter um instantâneo de estado da heap de depuração em um determinado momento ou a diferença entre os dois instantâneos.|  
|[\_CrtMemDumpAllObjectsSince](/visual-cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Despeja informações sobre todos os objetos atribuídos como um instantâneo determinado extraído do heap do início de execução.  Cada vez que despeja um bloco **\_CLIENT\_BLOCK**, uma função de hook fornecida pelo aplicativo é chamada, se uma foi instalada usando **\_CrtSetDumpClient**.|  
|[\_CrtDumpMemoryLeaks](/visual-cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Determina se qualquer vazamento de memória ocorreu desde o início da execução do programa e, em caso afirmativo, despeja todos os objetos atribuídos.  Cada vez que **\_CrtDumpMemoryLeaks** despeja um bloco **\_CLIENT\_BLOCK**, uma função de hook fornecida pelo aplicativo é chamada, se uma foi instalada usando **\_CrtSetDumpClient**.|  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Solicitações de alocação da heap de rastreamento  
 Apesar de localizar o nome do arquivo de origem e o número da linha, no qual uma declaração ou uma macro de relatório executa, é geralmente muito útil localizar a causa de um problema, provavelmente o mesmo não é verdade para funções de alocação do heap.  Quando macros podem ser inseridas em vários pontos apropriados na árvore de lógica de um aplicativo, uma alocação geralmente é ocultada em uma rotina especial que é chamada de vários locais diferentes em muitas vezes diferentes.  A pergunta geralmente não é qual linha de código fez uma alocação incorreta, mas qual das milhares de alocações feitas por essa linha de código está incorreta e porque.  
  
 **Números de solicitação de alocação exclusiva e \_crtBreakAlloc**  
  
 A maneira mais simples de identificar a chamada específica de alocação da heap que não foi bem\-sucedida é aproveitar o número exclusivo de solicitação de alocação associado com cada bloco na heap de depuração.  Quando as informações sobre um bloco são relatadas por uma das funções de despejo, esse número de solicitação de alocação é colocado entre chaves \(por exemplo, “{36}"\).  
  
 Depois que souber o número de solicitação de alocação de um bloco alocado inadequado, você pode passar este número para [\_CrtSetBreakAlloc](/visual-cpp/c-runtime-library/reference/crtsetbreakalloc) para criar um ponto de interrupção.  A execução será interrompida logo após a alocação do bloco, e é possível voltar de modo a determinar que rotina foi responsável pela chamada incorreta.  Para evitar recompilar, é possível fazer a mesma coisa no depurador definindo **\_crtBreakAlloc** para o número de solicitação de alocação que você está interessado.  
  
 **Criando versões de depuração de suas rotinas de alocação**  
  
 Uma abordagem um pouco mais complicada é criar versões de depuração a partir de suas próprias rotinas de alocação, comparáveis a versões de **\_dbg** de [funções de alocação de heap](../debugger/debug-versions-of-heap-allocation-functions.md).  Você pode passar o arquivo de origem e os argumentos do número da linha para as rotinas de alocação do heap e você, e você poderá imediatamente ver onde uma alocação incorreta foi originada.  
  
 Por exemplo, suponha que seu aplicativo contém uma rotina usada com frequência semelhante à seguinte:  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 Em um arquivo de cabeçalho, você poderia adicionar código como o seguinte:  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Em seguida, você pode alterar a alocação em sua rotina de criação de registro como a seguir:  
  
```  
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 Agora o nome do arquivo de origem e o número da linha onde `addNewRecord` foi chamado serão armazenados em cada bloco resultante atribuído no heap de depuração e relatados quando esse bloco é examinado.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
## Consulte também  
 [Depurando código nativo](../debugger/debugging-native-code.md)