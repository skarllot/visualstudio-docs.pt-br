---
title: "Instalando vers&#245;es do Visual Studio lado a lado | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instalações lado a lado [Visual Studio]"
  - "Ajuda [Visual Studio], instalando"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Instalando vers&#245;es do Visual Studio lado a lado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode instalar esta versão do Visual Studio em um computador que já tenha uma versão anterior instalada. Se você encontrar uma falha de instalação, você pode usar o [ferramenta de coleta de log](http://go.microsoft.com/fwlink/?LinkId=262077) para coletar informações sobre as falhas para que você possa depurar os problemas.  
  
> [!NOTE]
>  Recomendamos que você instale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versões na ordem em que elas foram lançadas. Por exemplo, instale o Visual Studio 2013 antes de instalar o Visual Studio de 2015.  
  
 Antes de instalar versões lado a lado, revise as seguintes condições:  
  
-   Se você usar o Visual Studio de 2015 para abrir uma solução criada no [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], posteriormente, você pode abrir e modificar a solução novamente na versão anterior desde que você não tenha implementado quaisquer recursos que são específicos para o Visual Studio de 2015.  
  
-   Se você tentar usar 2015 do Visual Studio para abrir uma solução criada no [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] ou uma versão anterior, talvez seja necessário modificar seus projetos e arquivos devem ser compatíveis com o Visual Studio de 2015. Para obter mais informações, consulte  [Portando, migrando e atualizando projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Se você desinstalar uma versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em um computador que tenha mais de uma versão instalada, as associações de arquivo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] são removidas para todas as versões. É possível remapear essas associações de arquivo usando o **Restaurar associações de arquivos** botão o **ambiente**, **geral** página do [opções](../ide/reference/general-environment-options-dialog-box.md) caixa de diálogo.  
  
-   O Visual Studio não atualiza automaticamente extensões porque nem todas as extensões são compatíveis. Você deve reinstalar as extensões do [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) ou o Editor do software.  
  
## Versões do .NET framework e instalações lado a lado  
  
-   Projetos do Visual Basic, Visual c\# e Visual F \# usam o **Target Framework** opção o **Project Designer** para especificar qual versão do .NET Framework usa de um projeto. Para um projeto de C\+\+, você pode alterar manualmente a estrutura de destino modificando o arquivo. vcxproj. Para obter mais informações, consulte [Compatibilidade de Versão](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md).  
  
     Quando você cria um projeto, você pode especificar qual versão do .NET Framework que o projeto for destinado a **do .NET Framework** lista o **novo projeto** caixa de diálogo.  
  
     Para obter informações específicas de idioma, consulte o tópico apropriado na tabela a seguir.  
  
    |Idioma|Tópico|  
    |------------|------------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[Página de Aplicativo, Designer de Projeto \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C\#|[Página Aplicativo, Designer de Projeto \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F\#|[Configuring Projects](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../extensibility/debugger/includes/jsprjscript_md.md)]|[Executando um aplicativo JScript em uma versão anterior do Common Language Runtime](http://msdn.microsoft.com/pt-br/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## Consulte também  
 [Instalando o Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)   
 [Portando, migrando e atualizando projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Compatibilidade de Versão](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [Instalando várias versões de idioma do Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Compilando aplicativos isolados do C\/C\+\+ e assemblies lado a lado](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3)