---
title: "Atualizando itens de projeto | Microsoft Docs"
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
  - "Atualizando itens de projeto"
  - "projetos [Visual Studio SDK], Atualizando itens"
  - "atualização de itens de projeto [Visual Studio]"
ms.assetid: 8af29dd4-eaf1-4b3c-b602-198e1a3dff23
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Atualizando itens de projeto
Se você adicionar ou gerenciar itens dentro de sistemas de projeto que você não implemente, talvez você precise participar do processo de atualização do projeto.  Crystal Reports é um exemplo de um item que pode ser adicionado ao sistema de projeto.  
  
 Normalmente, os implementadores de item de projeto desejam aproveitar um projeto já totalmente instanciado e atualizado, pois eles precisam saber que o projeto referências estão e quais outras propriedades do projeto são lá tomar uma decisão de atualização.  
  
### Para obter a notificação de atualização do projeto  
  
1.  Definir o <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> sinalizador \(definida em vsshell80.idl\) na implementação de item do projeto.  Isso faz com que o item de projeto VSPackage automaticamente carregado quando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell determina que um sistema de projeto está em processo de atualização.  
  
2.  Avise o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> por meio da interface do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> método.  
  
3.  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é acionado após a implementação de sistema do projeto completar suas operações de atualização e criação de novo projeto atualizado.  Dependendo do cenário, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é acionado após a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, ou o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> métodos.  
  
### Para atualizar os arquivos de item de projeto  
  
1.  Cuidadosamente, você deve gerenciar o processo de backup do arquivo na sua implementação de item de projeto.  Isso se aplica especificamente para backup de um lado a lado, onde o `fUpgradeFlag` parâmetro da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método está definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, onde os arquivos que tinham sido feitos o backup são posicionados ao longo de arquivos do lado que são designados como ". old".  Arquivos do backup mais antigos que a hora do sistema quando o projeto foi atualizado podem ser designados como desatualizados.  Além disso, eles podem ser sobrescritos a menos que você executar etapas específicas para evitar isso.  
  
2.  No momento o seu item de projeto recebe uma notificação de atualização de projeto, o  **Visual Studio Assistente de conversão de** ainda é exibido.  Portanto, você deve usar os métodos da <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interface para fornecer mensagens de atualização para o Assistente de interface do usuário.  
  
## Consulte também  
 [Visual Studio Conversion Wizard](http://msdn.microsoft.com/pt-br/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Atualizando projetos personalizados](../misc/upgrading-custom-projects.md)