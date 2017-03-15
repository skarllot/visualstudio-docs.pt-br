---
title: "Suporte para persist&#234;ncia de estado | Microsoft Docs"
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
  - "persistência de estado, suporte de estrutura de pacote gerenciado"
  - "estrutura de pacote gerenciado, suporte de persistência de estado"
  - "estado de persistência"
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Suporte para persist&#234;ncia de estado
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]pode manter o estado de objetos comuns.  Por exemplo, propriedades de solução e projeto são salvas e restauradas a partir de arquivos de solução e projeto.  As configurações de usuário podem ser exportadas para e importadas de arquivos de configurações.  
  
 Os VSPackages geralmente contam com armazenamento local, no registro do sistema ou na pasta de dados do aplicativo para o usuário atual ou o computador.  Valores que exigem uma pequena quantidade de espaço de armazenamento, tais como inteiros e seqüências de caracteres, são geralmente armazenados no registro do sistema.  Os valores que exigem muito espaço para armazenamento, como bitmaps, são salvos em um arquivo.  Se o caminho do arquivo pode ser salvas no registro do sistema.  O mecanismo de persistência deve ter permissão para acessar o armazenamento local.  
  
## Suporte para a localização de armazenamento Local  
 O <xref:Microsoft.VisualStudio.Shell.Package> classe fornece suporte para a localização de informações de estado na pasta do sistema do registro ou o aplicativo de dados para o usuário atual ou o computador.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Retorna o caminho da raiz do registro do computador local para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por exemplo, HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\8.0Exp.  
  
 A raiz do Registro local é obtida a partir do <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> service.  Se isso não estiver disponível, ele é obtido o <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> o VSPackage atributo.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Retorna o caminho para o usuário atual \(por computador\) raiz do registro para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por exemplo, HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp.  
  
 A raiz do Registro local é obtida a partir do <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> service.  Se isso não estiver disponível, ele é obtido o atributo DefaultLocalRegistryRoot o VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Retorna o caminho do diretório que serve como um repositório comum para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dados para o atual usuário móvel, por exemplo, C:\\Documents and Settings \\*YourAccountName*\\Application Data\\Microsoft\\VisualStudio\\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Retorna o caminho do diretório que serve como um repositório comum para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dados não\-móveis usuário atual, por exemplo, C:\\Documents and Settings \\*YourAccountName*\\Local Settings\\Application Data\\Microsoft\\VisualStudio\\8.0Exp.  
  
## Consulte também  
 [Estado de VSPackage](/visual-cpp/misc/vspackage-state)