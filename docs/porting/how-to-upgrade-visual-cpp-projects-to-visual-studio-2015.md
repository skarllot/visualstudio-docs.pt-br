---
title: "Como: atualizar projetos do Visual C++ para o Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projetos [C++], atualizando"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como: atualizar projetos do Visual C++ para o Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você abre um projeto do Visual C\+\+ que foi criado em uma versão anterior do Visual Studio pela primeira vez, pode ser solicitado para atualizar o projeto. A mensagem pergunta se você deseja atualizar para a versão mais recente do compilador do Visual C\+\+ e bibliotecas. As opções de atualização dependem da versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que foi usada para criar o projeto.  
  
 Você pode usar [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] para abrir, editar e criar [!INCLUDE[win8](../debugger/includes/win8_md.md)] projetos que foram criados no [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], mas para criar um novo [!INCLUDE[win8](../debugger/includes/win8_md.md)] projeto, você deve usar [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]. \(Para criar um [!INCLUDE[win81](../debugger/includes/win81_md.md)] projeto, você deve usar [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].\)  
  
 Para criar um projeto Windows 10, você deve usar [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)].  
  
 Se você não será solicitado a atualizar o projeto, você não terá que fazer nada para atualizar o projeto. Para obter mais informações, consulte [Portando, migrando e atualizando projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Se o projeto \(. vcproj\) foi criado em uma versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mais antiga do que [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], você deve atualizar o projeto.  
  
-   Se o projeto \(. vcxproj\) foi criado em [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)],  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], ou [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] você tem duas opções:  
  
    -   Você pode pular a atualização.[!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] carregará o projeto sem fazer alterações, se ele tem acesso a ferramentas do Visual C\+\+ no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] com SP1,  [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], ou [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]. Você pode fornecer esse acesso instalando a versão do Visual Studio que o projeto foi criado na mesma máquina que tenha [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)]. Para obter mais informações, consulte [Instalando versões do Visual Studio lado a lado](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md).  
  
    -   Você pode atualizar o projeto permitindo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para fazer as alterações que são descritas neste tópico. Se você tiver mais de um projeto do Visual C\+\+ em sua solução, você deve atualizar todos eles.  
  
        > [!NOTE]
        >  Se você recusar a atualização quando solicitado pela primeira vez, você pode atualizar o projeto mais tarde escolhendo **Atualizar projeto VC \+ \+** sobre o **projeto** menu. Se o comando não aparecer, a atualização não será necessária.  
  
## Atualizando um projeto do Visual C\+\+  
 Se você permitir que [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] para atualizar automaticamente o projeto, essas alterações são feitas:  
  
-   Altera o projeto para que ele use o [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)] compilador e bibliotecas \(PlatformToolset \= VisualStudio v140\).  
  
-   Para [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)] projetos, muda a TargetFrameworkVersion para .NET Framework 4.5.2.  
  
## Continuar a trabalhar com um PlatformToolset personalizado  
 Se você deseja continuar a trabalhar com um PlatformToolset personalizado no [!INCLUDE[vs_dev14](../porting/includes/vs_dev14_md.md)], o conjunto de ferramentas deve estar localizado em %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ em um x86, ou da máquina em % ProgramFiles \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ em x64 máquina. Para obter informações sobre como criar um PlatformToolset personalizado, consulte [C\+\+ nativo multiplataforma](http://go.microsoft.com/fwlink/?LinkId=248587) no blog da equipe do Visual C\+\+.  
  
## Consulte também  
 [Portando, migrando e atualizando projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)