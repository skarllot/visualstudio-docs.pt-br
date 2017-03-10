---
title: "Analisador de extens&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, analisador de falhas de carga"
ms.assetid: 8d2bcc4e-9feb-45a5-8d8e-470346f0d39e
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Analisador de extens&#227;o
O **Analisador de extensão** captura e registra falhas de carregamento de extensão mais comuns. O **Analisador de extensão** é executado em sua própria janela de ferramenta. O analyzer relata o motivo de uma falha e sugestões sobre como corrigi\-lo.  
  
 O [Analisador de extensão](http://go.microsoft.com/fwlink/?LinkId=205840) pode ser baixado da Galeria do Visual Studio. O **Analisador de extensão** assemblies são instalados no \<*caminho de instalação do Visual Studio*\> \\Common7\\IDE\\PrivateAssemblies\\.  
  
## Navegador  
 Depois de ter instalado o **Analisador de extensão**, no **ferramentas** menu clique em **Analisador de extensão**, em seguida, **navegador**. É exibida uma janela que lista todas as extensões são registradas no computador. Há diferentes guias para VSIX, VSPackages, PkgDef arquivos e componentes do MEF. Você pode classificar a lista por qualquer um dos nomes de coluna.  
  
1.  Na guia VSIX exibe informações sobre extensões VSIX instaladas. Você pode incluir os componentes do sistema selecionando o **Mostrar componentes de sistema** caixa de seleção. Nessa guia, você pode navegar para entradas de log para o VSIX, abra o manifesto VSIX no editor de XML do Visual Studio e abra a pasta em que a extensão do VSIX está instalada.  
  
2.  A guia VS pacotes exibe informações sobre os VSPackages são conhecidos no momento para o Visual Studio, se eles são carregados ou não. Essa informação inclui o identificador do VSIX, o arquivo pkgdef e o GUID do VSPackage. Você pode incluir sistema VSPackages selecionando o **Mostrar pacotes de sistema** caixa de seleção. Nessa guia, você pode navegar para entradas de log, consulte que VSIX listados na guia VSIX, consulte o arquivo pkgdef na guia PkgDef arquivos e analisar o VSPackage. Os resultados da análise são mostrados no **saída** painel.  
  
3.  A guia arquivos PkgDef exibe informações sobre os arquivos. pkgdef para extensões conhecidas para o Visual Studio. Essas informações incluem o identificador do VSIX e o caminho da extensão. Você pode navegar para o log ou a guia VSIX e você pode exibir o arquivo pkgdef no editor.  
  
4.  A guia componentes do MEF exibe informações sobre componentes do MEF que são conhecidos para o Visual Studio. Esta informação inclui o identificador do VSIX e o caminho em que a extensão está instalada. Você pode incluir os componentes do sistema selecionando o **Mostrar componentes de sistema** caixa de seleção. Você também pode navegar para o local em que a extensão foi instalada, o arquivo pkgdef e a entrada correspondente do VSIX.  
  
> [!WARNING]
>  Você pode receber uma mensagem pedindo\-lhe para ativar o log de fusão. Para fazer isso, selecione um local para os arquivos de log. Você pode ser solicitado a reiniciar todas as instâncias do Visual Studio antes de continuar.  
  
## Visualizador de log  
 Você pode ver mensagens de log com o **Visualizador de Log de extensão** se você estiver executando um projeto com o log ativado \(adicionando \/log argumentos de linha de comando do projeto\). Para obter mais informações, consulte [\/Log](../ide/reference/log-devenv-exe.md). O **Visualizador de Log de extensão** janela exibe a data, o ouvinte, o tipo de entrada \(tipo de mensagem\), o tipo de erro, informações de classe\/interface e a mensagem de log. Você pode classificar e filtrar as informações.  
  
## Problemas comuns de carregamento de extensão  
 Falha no carregamento do algumas das razões comuns para uma extensão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] são:  
  
-   Problemas de dependência. Uma extensão pode foram implantada de forma que os assemblies dependentes não foi encontrados.  
  
-   Exceções. Quando um VSPackage é carregado, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método. Se esse método lançará uma exceção, a carga de VSPackage falhará. É a melhor forma de isolar esse problema para percorrer o código SetSite.  
  
-   Registro incorreto. Verifique se a extensão está assinada corretamente e que o VSPackage é registrado usando a chave pública correta.  
  
## Consulte também  
 [Gerenciando os VSPackages](../extensibility/managing-vspackages.md)