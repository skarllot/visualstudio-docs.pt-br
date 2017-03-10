---
title: "Atualizando testes de IU codificados a partir do Visual Studio 2010 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "mlearned"
manager: "douge"
---
# Atualizando testes de IU codificados a partir do Visual Studio 2010
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Testar projetos que contém testes de UI codificados criados na [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 são reparadas silenciosamente quando aberto no Visual Studio 2012. Se os projetos de teste são verificados no controle de origem, os arquivos de projeto são verificados para este reparo. Depois de reparar, esses projetos contendo pode de testes UI codificado de teste e ser usadas em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 e [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
> [!NOTE]
>  O Visual Studio inclui mais de um tipo de projeto de teste. Se você criar um novo teste de IU codificado, ele será criado em um tipo de projeto de teste de IU codificado. Para obter mais informações, consulte [testes atualizando de versões anteriores do Visual Studio](http://msdn.microsoft.com/pt-br/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).  
  
> [!WARNING]
>  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] projetos de teste que contém testes de UI codificados devem ser recriados quando você abrir o projeto de teste no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] ou [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] lado a lado com [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
> [!WARNING]
>  Quando um projeto de teste que foi criado em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e contém somente os testes de unidade é aberta no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], codificados testes de interface do usuário não podem ser adicionados a ele. Da mesma forma, é possível adicionar um teste de IU codificado a um projeto de teste de unidade que foi criado em [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
## Problemas de compatibilidade entre o Visual Studio 2010 e o Visual Studio 2012  
 A tabela a seguir lista os problemas para estar ciente de quando migrar IU codificados entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] e [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
> [!CAUTION]
>  Há um problema conhecido sobre referências em projetos de teste de IU codificados não aparecerem no Gerenciador de soluções. Para obter mais informações, consulte o arquivo Leiame incluído no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] mídia de instalação.  
  
|Funcionalidade UI codificada|Problema|Solução|  
|----------------------------------|--------------|-------------|  
|Teste de interface do usuário do Silverlight não tem suporte [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**Haverá falha na compilação**<br /><br /> Se você tiver [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 e tiver criado codificado projetos de teste de interface do usuário para aplicativos do Silverlight, esses projetos não podem ser abertos no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|É recomendável que você gerencia esses projetos em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] apenas Feature Pack 2.|  
|Não há suporte para testes de IU do Firefox no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**Compilação terá êxito, haverá falha na execução de teste**<br /><br /> Se você tiver [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Feature Pack 2 e tiver criado a projetos de teste de UI codificados para aplicativos web no Firefox, esses projetos não podem ser abertos no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|É recomendável que você gerencia esses projetos em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] apenas Feature Pack 2.|  
|Novo código de interface do usuário testes APIs foram adicionadas em [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|**Haverá falha na compilação**<br /><br /> Se você criar testes de UI codificados usando a API de teste de interface do usuário nova no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], esses projetos não podem ser abertos no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].|Projetos usando a nova API devem ser gerenciados [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] somente.|  
|Em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], referências foram adicionadas em uma instrução 'Escolher' no arquivo csproj. Em [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], estamos usando um arquivo de destino de comentários para incluir referências de Assembly de teste de IU codificado.|Em [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], um teste de IU codificados não pode ser adicionado a um projeto de teste criado no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] \(ou SP1\) que não continha um teste de IU codificado.<br /><br /> O processo de reparação adiciona o arquivo de destino e a instrução de escolha. Se um teste de IU codificados não está no projeto de teste, o projeto é marcado como reparado e as referências apropriadas não serão adicionadas ao adicionar o teste de IU codificado no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|Você terá que criar um novo projeto de teste na mesma solução usando [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] e adicione o novo teste de IU codificado. Como alternativa, você pode adicionar testes de IU codificados para o projeto de teste na [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] SP1 e abrir esse projeto no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|  
  
##  <a name="UpgradingCodedUIFromVS2010_Update"></a> Atualização do Visual Studio 2010 SP1  
 Uma atualização [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] SP1 com suporte de compatibilidade para o Visual Studio 2012 e o Windows 8 está disponível para download no [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=34677) e também como um Visual Studio atualize.  
  
 Depois de aplicar a atualização, o seguinte [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] SP1 codificados recursos de ferramenta de teste de interface do usuário foram aprimorados para o Windows 8:  
  
-   Você pode executar um teste de IU codificado para a Microsoft controla baseado no .NET Framework 4.5 Windows Presentation Foundation \(WPF\) em um computador que está executando o Windows 8.  
  
-   Você pode executar um teste de IU codificado para 64 bits \(x64\) o Internet Explorer 10 em um computador que está executando o Windows 8.  
  
 A atualização também contém correções para os seguintes problemas:  
  
-   **Cobertura de código:** impossibilidade de abrir um arquivo de cobertura de código \(Coverage\) criado pelo Visual Studio 2012 na [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] SP1.  
  
-   **Presos artefatos de teste:** sua equipe tem um artefato de teste que é atribuído a um usuário inválido no Team Foundation Server \(TFS\) 2010. Por exemplo, um usuário saiu da empresa, mas ainda tem um caso de teste que é atribuído a ele. Atualizar o TFS 2010 ao TFS 2012. Você usa [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010 para se conectar ao servidor TFS atualizado. Não é possível atribuir o artefato de teste para todos os usuários TFS usando [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 2010.  
  
-   **Testes de carga:** quando você executa um teste de carga juntamente com um tipo de rede que não seja o perfil de rede local \(LAN\) em um computador está executando o Windows 8, o driver do emulador de rede faz com que o sistema operacional falhar. Para obter mais detalhes, consulte [KB artigo 2736182](http://support.microsoft.com/kb/2736182).  
  
## Consulte também  
 [Portando, migrando e atualizando projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Atualizando testes de versões anteriores do Visual Studio](http://msdn.microsoft.com/pt-br/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)   
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)   
 [Gerenciando um Teste de IU Codificado a partir de uma gravação de ação existente](/devops-test-docs/test/generating-a-coded-ui-test-from-an-existing-action-recording)   
 [Configurações e plataformas compatíveis para testes de IU codificados e gravações de ações](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)