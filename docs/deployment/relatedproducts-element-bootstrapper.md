---
title: "Elemento &lt;RelatedProducts&gt; (bootstrapper) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <RelatedProducts> [bootstrapper]"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;RelatedProducts&gt; (bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O `RelatedProducts` elemento define outros produtos que dependem ou estão incluídos no produto atual.  
  
## Sintaxe  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## Elementos e atributos  
 O `RelatedProducts` elemento é filho de `Product` elemento.  Ela tem nenhum atributo.  
  
## DependsOnProduct  
 O `DependsOnProduct` elemento significa que o produto atual depende do produto identificado e que o produto identificado deve ser instalado antes do atual.  Ele é um filho do `RelatedProducts` elemento.  A `RelatedProducts` elemento pode ter um ou mais `DependsOnProduct` elementos.  
  
 `DependsOnProduct`tem o atributo a seguir.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Code`|O nome do código do produto incluído, conforme especificado pelo `ProductCode` atributo da `Product` elemento.  Para obter mais informações, consulte [Elemento \<Product\>](../deployment/product-element-bootstrapper.md).|  
  
## EitherProducts  
 O `EitherProducts` elemento define zero ou mais `DependsOnProduct` elementos, e sem atributos.  Pelo menos um `DependsOnProduct` neste conjunto deve ser instalado antes do produto atual.  A `RelatedProducts` o elemento pode ter zero ou mais `EitherProducts` elementos.  
  
## IncludesProduct  
 O `IncludesProduct` elemento significa que um produto está incluído com a instalação atual e não requer uma instalação separada.  Ele é um filho do `RelatedProducts` elemento.  A `RelatedProducts` elemento pode ter um ou mais `IncludesProduct` elementos.  
  
 `IncludesProduct`tem o atributo a seguir.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Code`|O nome do código do produto incluído, conforme especificado pelo `ProductCode` atributo da `Product` elemento.  Para obter mais informações, consulte [Elemento \<Product\>](../deployment/product-element-bootstrapper.md).|  
  
## Exemplo  
 O exemplo de código a seguir especifica que o Microsoft Installer é instalado com o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]e, portanto, não será necessário uma instalação separada.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## Consulte também  
 [Elemento \<Product\>](../deployment/product-element-bootstrapper.md)