---
title: "Estendendo a caixa de ferramentas | Microsoft Docs"
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
  - "ferramentas [Visual Studio], caixa de ferramentas"
  - "Caixa de ferramentas [Visual Studio SDK]"
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
caps.handback.revision: 38
manager: "douge"
---
# Estendendo a caixa de ferramentas
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Toolbox** fornece uma coleção de objetos que fornecem funcionalidade para designers e editores por meio do mecanismo de arrastar e soltar do IDE.  
  
 Há duas maneiras básicas no qual um VSPackage funciona com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Toolbox**:  
  
-   Um VSPackage pode adicionar novos itens de dados e controles para o **Toolbox**.  
  
-   Um VSPackage pode ser um destino ou um consumidor de existentes **Toolbox** funcionalidade, dando suporte as operações de arrastar\-e\-soltar e configurar o **Toolbox**da aparência.  
  
## Nesta seção  
 [Como: criar um controle de caixa de ferramentas que usa o Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Descreve a saída para criar um controle de caixa de ferramentas usando o modelo de controle de caixa de ferramentas do Windows Forms.  
  
 [Criando um controle de caixa de ferramentas do WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Descreve a saída para criar um controle de caixa de ferramentas usando o modelo de controle de caixa de ferramentas do WPF.  
  
 [Gerenciando a caixa de ferramentas](/visual-cpp/misc/managing-the-toolbox)  
 Descreve como um VSPackage pode gerenciar o conteúdo e a aparência do **Toolbox**.  
  
## Seções relacionadas  
 [Como: gerenciar a janela caixa de ferramentas](http://msdn.microsoft.com/pt-br/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Descreve como trabalhar com o **Toolbox** no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\).  
  
 [How to: Control the Toolbox](../Topic/How%20to:%20Control%20the%20Toolbox.md)  
 Descreve como gerenciar o **Toolbox** usando o modelo de programação de automação.  
  
 [Estendendo a outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Serviços para criar elementos de interface do usuário que correspondem ao restante da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].