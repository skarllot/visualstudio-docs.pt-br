---
title: "Práticas recomendadas para implementar um plug-in de controle de origem | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6f2280fce0fe197bfd3d2dfba421e6e2c1c3272d
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Práticas recomendadas para implementar um plug-in de controle de origem
Os seguintes detalhes técnicos podem ajudá-lo a implementar confiável um plug-in de controle de origem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Problemas de gerenciamento de memória  
 Na maioria dos casos, o ambiente de desenvolvimento integrado (IDE), que é o chamador, libera e aloca memória. O plug-in de controle de origem retorna cadeias de caracteres e outros itens em buffers alocados pelo chamador. Exceções são observadas nas descrições de funções específicas quando eles ocorrerem.  
  
## <a name="arrays-of-file-names"></a>Matrizes de nomes de arquivo  
 Quando uma matriz de arquivos for passada, ela não é passada como uma matriz de contígua de nomes de arquivo. Ela é passada como uma matriz de ponteiros para nomes de arquivo. Por exemplo, no [SccGet](../extensibility/sccget-function.md), os nomes de arquivo são passados pelo `lpFileNames` parâmetro, onde `lpFileNames` é, na verdade, um ponteiro para um `char **`. `lpFileNames`[0] é um ponteiro para o nome, `lpFileNames`[1] é um ponteiro para o nome da segunda e assim por diante.  
  
## <a name="large-model"></a>Modelo grande  
 Todos os ponteiros são de 32 bits, mesmo em sistemas operacionais de 16 bits.  
  
## <a name="fully-qualified-paths"></a>Caminhos totalmente qualificados  
 Onde os nomes de arquivos ou diretórios são especificados como argumentos, eles devem ser caminhos totalmente qualificados ou caminhos UNC, sem as barras invertidas final. É responsabilidade do controle da fonte de plug-in para converter esses caminhos relativos se que é um requisito do sistema de controle de origem subjacente.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Especifique um caminho totalmente qualificado para a DLL registrada  
 O IDE não carrega DLLs de caminhos relativos (por exemplo,.\NewProvider.dll). Especifique um caminho completo da DLL (por exemplo, C:\Providers\NewProvider.dll). Esse requisito fortalece a segurança do IDE, impedindo o carregamento de controle de origem não autorizados ou representado DLLs.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Verificar se há um plug-in de VSSCI existente ao instalar o plug-in de controle de origem  
 Um usuário que planeja instalar o plug-in de controle de origem já pode ter um fonte controle existente plug-in instalado no computador. O programa de instalação do plug-in que você criar deve determinar se há valores existentes para as chaves do Registro relevantes. Se essas chaves já estiverem definidas, o programa de instalação deve perguntar ao usuário se registre seu plug-in como plug-in de controle de origem padrão e substituir aquele que já está instalado.  
  
## <a name="error-result-codes-and-reporting"></a>Códigos de resultado de erro e a emissão de relatórios  
 O `SCC_OK` retornar o código para uma função de controle de origem indica que a operação foi bem-sucedida para todos os arquivos. Se a operação falhar, ele deve retornar o último código de erro.  
  
 A regra para emissão de relatórios é que, se ocorrer um erro no IDE, o IDE é responsável por reportá-lo. Se ocorrer um erro no sistema de controle de origem, o plug-in de controle de origem é responsável por reportá-lo. Por exemplo, "nenhum arquivo está selecionado atualmente" seria relatado pelo IDE, ao passo que "Este arquivo já fez check-out" seria relatado pelo plug-in.  
  
## <a name="the-context-structure"></a>A estrutura de contexto  
 Durante a chamada para o [SccInitialize](../extensibility/sccinitialize-function.md), a chamador passa o `ppvContext` parâmetro, que é um identificador não inicializado para uma lacuna. O plug-in de controle de origem pode ignorar esse parâmetro ou pode alocar uma estrutura de qualquer tipo e colocam um ponteiro para essa estrutura no ponteiro passado. O IDE não compreende essa estrutura, mas ele passa um ponteiro para essa estrutura em todas as outras chamadas no plug-in. Isso fornece informações de cache de contexto valiosas para o plug-in que ele pode usar para manter informações de estado global que persiste nas chamadas de função sem o uso de variáveis globais. O plug-in é responsável por liberar a estrutura em uma chamada para o [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Se o plug-in define o `SCC_CAP_REENTRANT` bit no [SccInitialize](../extensibility/sccinitialize-function.md) (especificamente, no `lpSccCaps` parâmetro), várias estruturas de contexto são usadas para controlar todos os projetos que estão abertos.  
  
## <a name="bitflags-and-other-command-options"></a>Os sinalizadores de bit e outras opções de comando  
 Para cada comando, como o [SccGet](../extensibility/sccget-function.md), o IDE pode especificar várias opções que alteram o comportamento do comando.  
  
 A API oferece suporte a configuração de determinadas opções pelo IDE por meio de `fOptions` parâmetro. Essas opções são descritas na [os sinalizadores de bit usados pelos comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) junto com os comandos que eles afetam. Em geral, estas são opções para o qual o usuário não será avisado.  
  
 Mais opções de configuração configuráveis pelo usuário não são definidas dessa forma, porque eles variam amplamente entre plug-ins de controle de origem. Portanto, o mecanismo recomendado é um **avançado** botão. Por exemplo, no **obter** caixa de diálogo, o IDE exibe apenas as informações que ele entende, mas ela também exibe um **avançado** botão se o plug-in tem opções para este comando. Quando o usuário clica o **avançado** botão, o IDE chama o [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) para habilitar o plug-in para solicitar ao usuário informações, como os sinalizadores de bit ou um valor de data/hora de controle de origem. O plug-in retorna essas informações em uma estrutura que é passada durante a `SccGet` comando.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [Criando um controle da fonte de plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)
