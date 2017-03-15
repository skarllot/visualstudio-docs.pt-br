---
title: "Falha no registro de interoperabilidade COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_register_com2"
ms.assetid: d1b81f8e-66d7-4cfc-96ff-f1436a8f854a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Falha no registro de interoperabilidade COM
Há uma falha no registro de um assembly que expõe a funcionalidade para clientes COM.  O processo de compilação falhará se esse erro ocorre.  
  
 Assemblies podem expor objetos para clientes COM.  O sistema de projeto fornece uma propriedade para registrar classes expostas para interoperabilidade COM, bem como para gerar e registrar uma biblioteca de tipos para que essas classes são utilizáveis de linguagens de script, bem como Visual Basic 6.  
  
 Consulte o  **Build** página de propriedade no  **Propriedades de configuração** pasta para acessar o  **Register for COM Interop** propriedade.  
  
 Alguns possíveis motivos de falha incluem:  
  
-   Incapacidade para gerar uma biblioteca de tipos do assembly.  Isso pode ser um problema de espaço em disco ou um arquivo de bloqueio problema onde a biblioteca de tipos está bloqueada por Visual Studio ou algum outro processo.  Além disso, as bibliotecas de tipos para assemblies referenciados podem não estar registradas corretamente no seu sistema.  
  
-   Incapacidade para registrar a biblioteca de tipos gerados.  Isso pode ser um problema de permissões no registro.  
  
-   Incapacidade para registrar classes no assembly.  Isso pode ser um problema de permissões no registro.  
  
 **Para corrigir este erro**  
  
-   Crie espaço livre em disco no seu computador.  
  
-   Se houver um problema de bloqueio de arquivo, reinicie o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Certifique\-se de que você fez logon como administrador ou como membro de um grupo que tenha permissão para acessar o registro.  
  
## Consulte também  
 [Interoperabilidade COM em aplicativos .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)