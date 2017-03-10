---
title: Atualizar testes de IU codificados no Visual Studio 2010 |Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 33
ms.author: mlearned
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ce287b916a088c35689cf56a58f9635112fd0d88
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Atualizando testes de IU codificados a partir do Visual Studio 2010
Projetos de teste que contêm testes de IU codificados criados no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 são reparados silenciosamente quando abertos no Visual Studio 2012. Se os Projetos de teste forem inseridos no controle do código-fonte, os arquivos do projeto serão verificados para realização desse reparo. Após o reparo, esses projetos de teste que contêm testes de IU codificados podem ser usados no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 e no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
> [!NOTE]
>  O Visual Studio inclui mais de um tipo de projeto de teste. Se você criar um novo teste de IU codificado, ele será criado em um tipo de projeto de teste de IU codificado. Para saber mais, consulte [Atualizar testes de versões anteriores do Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).  
  
> [!WARNING]
> Projetos de teste do  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] que contêm testes de IU codificados devem ser recriados ao abri-los no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ou no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] lado a lado com [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
> [!WARNING]
>  Quando um projeto de teste criado no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e que contém somente os testes de unidade é aberto no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], não é possível adicionar testes de IU codificados a ele. Da mesma forma, não é possível adicionar um teste de IU codificado a um projeto de teste de unidade que foi criado no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Problemas de compatibilidade entre o Visual Studio 2010 e o Visual Studio 2012  
 A tabela a seguir lista os problemas dos quais você deve estar ciente ao migrar testes de IU codificados entre o [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e o [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
> [!CAUTION]
>  Há um problema conhecido no qual as referências em projetos de teste de IU codificados não aparecem no Gerenciador de soluções. Para saber mais, consulte o arquivo Leiame na mídia de instalação do [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
|Funcionalidade de IU codificada|Problema|Solução|  
|----------------------------|-----------|--------------|  
|Não há suporte para o Teste de IU do Silverlight no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**Haverá falha na compilação**<br /><br /> Se você tiver o [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 e tiver criado Projetos de teste de IU codificado para aplicativos do Silverlight, esses projetos não poderão ser abertos no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Recomendamos o gerenciamento desses projetos apenas no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2.|  
|Não há suporte para o Teste de IU do Firefox no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**A compilação terá êxito, haverá falha na execução do teste**<br /><br /> Se você tiver o [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 e tiver criado Projetos de teste de IU codificado para aplicativos Web do Firefox, esses projetos não poderão ser abertos no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Recomendamos o gerenciamento desses projetos apenas no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2.|  
|Novas APIs de teste de código de IU foram adicionadas ao [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**Haverá falha na compilação**<br /><br /> Se você criar Testes de IU codificados usando a nova API de teste de IU no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], esses projetos não poderão ser abertos no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].|Os projetos que usam a nova API devem ser gerenciados somente no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|  
|No [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], foram adicionadas referências dentro de uma instrução ‘Choose’ no arquivo csproj. No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], estamos usando um arquivo de destino de Comentários para incluir referências ao Assembly de Teste de IU codificado.|No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], não é possível adicionar um Teste de IU codificado a um Projeto de teste criado no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] (ou SP1) que não continha um Teste de IU codificado.<br /><br /> O processo de reparação adiciona o arquivo de destino e a instrução Choose. Se um Teste de IU codificado não estiver no Projeto de teste, o projeto será marcado como reparado e as referências apropriadas não serão adicionadas na adição do Teste de IU codificado no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Será necessário criar um novo Projeto de teste na mesma solução usando o [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] e adicionar o novo Teste de IU codificado a ele. Como alternativa, adicione Testes de IU codificados ao Projeto de teste no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 e abra esse projeto no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|  
  
##  <a name="UpgradingCodedUIFromVS2010_Update"></a> Atualização do Visual Studio 2010 SP1  
 Uma atualização para o [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 com suporte de compatibilidade para o Visual Studio 2012 e o Windows 8 está disponível para download no [Centro de Download da Microsoft](http://www.microsoft.com/download/details.aspx?id=34677) e também como uma atualização do Visual Studio.  
  
 Depois de aplicar a atualização, os seguintes recursos de ferramenta de teste de IU codificado do [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1 serão aprimorados para o Windows 8:  
  
-   Você pode executar um Teste de IU codificado para os controles do WPF (Windows Presentation Foundation) baseados no Microsoft .NET Framework 4.5 em um computador que está executando o Windows 8.  
  
-   Você pode executar um Teste de IU codificado para o Internet Explorer 10 de 64 bits (x64) em um computador que está executando o Windows 8.  
  
 A atualização também contém correções para os seguintes problemas:  
  
-   **Cobertura de código:** impossibilidade de abrir um arquivo de cobertura de código (.coverage) criado pelo Visual Studio 2012 no [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] SP1.  
  
-   **Artefatos de teste presos:** sua equipe tem um artefato de teste que é atribuído a um usuário inválido no Team Foundation Server (TFS) 2010. Por exemplo, um usuário saiu da empresa, mas ainda tem um caso de teste atribuído a ele. Atualize o TFS 2010 para TFS 2012. Você usa o [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 para se conectar ao servidor TFS atualizado. Não é possível atribuir o artefato de teste a qualquer usuário do TFS usando [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010.  
  
-   **Teste de carga:** quando você executa um teste de carga junto com um tipo de rede que não é o perfil de rede local (LAN) em um computador com o Windows 8, o driver do emulador de rede faz com que o sistema operacional falhe. Para obter mais detalhes, consulte o [Artigo KB 2736182](http://support.microsoft.com/kb/2736182).  
  
## <a name="see-also"></a>Consulte também  
 [Portabilidade, migração e atualização de projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Atualizar Testes de Versões Anteriores do Visual Studio](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Usar a automação de interface do usuário para testar o código](../test/use-ui-automation-to-test-your-code.md)   
 [Gerar um Teste de IU Codificado de uma gravação da ação existente](/devops-test-docs/test/generating-a-coded-ui-test-from-an-existing-action-recording)   
 [Configurações e plataformas com suporte para testes de IU codificados e gravações das ações](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
