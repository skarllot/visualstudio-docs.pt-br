---
title: "Persist&#234;ncia de estado e o IDE do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Configurações de IDE, persistência de estado"
  - "persistência de configurações de usuário [Visual Studio SDK]"
  - "Ferramentas de persistir configurações de páginas de opções [Visual Studio SDK]"
  - "IDE, persistência de estado"
  - "persistência, configurações de usuário"
ms.assetid: fdd49bb1-ed3b-4428-b685-de65c3215c1c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Persist&#234;ncia de estado e o IDE do Visual Studio
O  **Configurações de importação\/exportação** comando o  **Ferramentas** menu do ambiente de desenvolvimento integrado \(IDE\) importa e exporta as personalizações da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente.  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] configurações APIs na [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permitem a um VSPackage definir uma ou mais categorias de configurações \(grupos de variáveis de estado\) a ser mantido quando um usuário escolhe o  **Configurações de importação\/exportação** comando.  
  
 Um GUID identifica cada categoria de configurações e é definido em sua própria entrada de registro, conhecida como um  *Ponto de configurações personalizadas*.  
  
> [!NOTE]
>  As implementações padrão a  **FerramentasOpções** páginas, o  **caixa de ferramentas**e o `Microsoft.VisualStudio.Shell.DialogPage` automaticamente oferecem suporte para persistência.  A API de configurações pode substituir o mecanismo padrão.  Para obter mais informações, consulte [Estendendo a caixa de ferramentas](../misc/extending-the-toolbox.md),  [Páginas de opções](../misc/options-pages.md) e <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
## Nesta seção  
 [Suporte para configurações de usuário](../extensibility/internals/support-for-user-settings.md)  
 Descreve as configurações do registro \(ponto de configurações personalizadas\) e os atributos usados para especificar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementação de configurações usada por um determinado VSPackage.  
  
 [Como: exportar configurações usando Assemblies de interoperabilidade](../misc/how-to-export-settings-by-using-interop-assemblies.md)  
 Fornece uma descrição detalhada de como implementar o suporte para salvar dados de configuração usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mecanismo de configurações para o assembly de interoperabilidade com base em VSPackages.  
  
 [Como: usar Assemblies de interoperabilidade para importar configurações](../misc/how-to-use-interop-assemblies-to-import-settings.md)  
 Fornece uma descrição detalhada de como implementar o suporte para recuperar dados de configuração usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mecanismo de configurações para o assembly de interoperabilidade com base em VSPackages.  
  
 [Exportando configurações](../misc/exporting-settings.md)  
 Inclui uma descrição detalhada de como implementar o suporte para salvar dados de configuração usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mecanismo de configurações para a estrutura de pacote gerenciado baseia VSPackages.  
  
 [Importando configurações](/visual-cpp/misc/importing-settings)  
 Fornece uma descrição detalhada de como implementar o suporte para recuperar dados de configuração usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mecanismo de configurações para a estrutura de pacote gerenciado baseia VSPackages.  
  
## Seções relacionadas  
 [Working with Settings](http://msdn.microsoft.com/pt-br/4c0a56ab-6091-4ebc-9dc7-52c40846bacb)  
 Descreve como gerenciar as seções de exportação e importação do IDE.  
  
 [Páginas de opções](../misc/options-pages.md)  
 Descreve o suporte que o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece automaticamente para o gerenciamento existente ou criar novos  **FerramentasOpções** páginas.  
  
 [Estendendo a caixa de ferramentas](../misc/extending-the-toolbox.md)  
 Explica o suporte que o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece automaticamente para gerenciamento ou estendendo o  **caixa de ferramentas**.  
  
 [Opções e configurações de usuário estendendo](../extensibility/extending-user-settings-and-options.md)  
 Descreve como programar o VSPackage obter e preservar as preferências do usuário.