---
title: "Como: adicionar modelos &#224; caixa de di&#225;logo Novo projeto | Microsoft Docs"
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
  - "caixas de diálogo, adicionando modelos de projeto"
  - "projetos [Visual Studio SDK], adicionando modelos de caixa de diálogo"
  - "modelos [Visual Studio], adicionando a caixa de diálogo do projeto"
ms.assetid: fd044681-e666-410d-815c-33db923ed888
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# Como: adicionar modelos &#224; caixa de di&#225;logo Novo projeto
Um número de modelos de projeto predefinidos é instalado durante a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] instalação. Para obter uma lista completa de modelos de projeto predefinidos, consulte [PONTA Criando projetos de modelos](http://msdn.microsoft.com/pt-br/7c36d86a-6b79-4480-8228-0f925f1204b2). Além dos modelos de projeto padrão, você pode criar modelos de projeto personalizados ou subtipo específico. Por exemplo, o **Smart Device** subtipo fornece seus próprios modelos para [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projetos. Para obter instruções sobre como criar um modelo personalizado, consulte [Como criar modelos de projeto](../ide/how-to-create-project-templates.md).  
  
## Adicionando um modelo para a caixa de diálogo Novo projeto  
  
#### Para adicionar um modelo para a caixa de diálogo Novo projeto  
  
1.  Crie um modelo, incluindo o arquivo MyTemplate vstemplate.  
  
2.  Selecione os arquivos no seu modelo \(incluindo o arquivo. vstemplate\), clique com botão direito\-los, clique em **Enviar para**, e, em seguida, clique em **pasta compactada \(zipada\)**. Os arquivos que você extraiu anteriormente são compactados em um arquivo. zip.  
  
 Colocar o arquivo de modelo. zip em **%USERPROFILE%\\Documents\\Visual Studio 2015\\Templates\\ProjectTemplates**.  
  
## Consulte também  
 [Project Subtypes](d235b47b-cf11-4d47-a63f-e33d9d16105d2044a030-0795-4940-bd65-a6e44de98a0f)   
 [PONTA: Modelos do Visual Studio](http://msdn.microsoft.com/pt-br/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Contribuindo para a caixa de diálogo Novo Item adicionar](../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)