---
title: "Erro MSB3155 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.ProductNotFound"
helpviewer_keywords: 
  - "MSB3155"
ms.assetid: 59bf2293-ef13-4bb1-8f29-5d6966bbe313
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3155 (MSBuild)
**Erro MSB3155 MSBuild: O item “\<package\>” não pôde ser localizado em “\<path\>”**  
  
 Esse erro ocorre quando um conjunto com <xref:Microsoft.Build.Tasks.Deployment.Bootstrapper.Product.ProductCode%2A> especificado não pode ser encontrado no cache bootstrapper.  
  
> [!NOTE]
>  Microsoft Data Access Components \(MDAC\) não é incluído como um pacote bootstrapper.  Podem ser [Atualização do Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=86676) baixados do site.  
  
### Para corrigir este erro  
  
-   Remova o pacote de lista de pacotes para a instalação, ou adicione o pacote para o cache.  Além de isso, certifique\-se que o manifesto é formatado corretamente com as marcas XML válidos.  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)   
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)   
 [Caixa de diálogo Pré\-requisitos](../ide/reference/prerequisites-dialog-box.md)   
 [Criando pacotes de bootstrapper](../deployment/creating-bootstrapper-packages.md)