---
title: "Determinando o Namespace padr&#227;o de um projeto | Microsoft Docs"
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
  - "ferramentas personalizadas, computação namespace padrão"
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# Determinando o Namespace padr&#227;o de um projeto
Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], se a `CustomToolNamespace` propriedade é definida no arquivo de entrada, em seguida, o valor de `CustomToolNamespace` se torna o valor do parâmetro de namespace padrão passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método.  Caso contrário, o `wszDefaultNamespace` parâmetro passado para `Generate` é sempre igual ao namespace raiz.  Para obter mais informações sobre namespaces, consulte [Palavras\-chave de namespace](/dotnet/csharp/language-reference/keywords/namespace-keywords).  
  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]usa os namespaces baseados em pasta.  Ou seja, o espaço para nome consiste o namespace raiz, além de nomes de qualquer pasta que contém a ferramenta personalizada.  Cada nome de pasta é convertido em um identificador válido e períodos separam todos os nomes.  Por exemplo, se o arquivo de entrada é FolderA\\FolderB\\FolderC\\MyInput.txt e o namespace raiz for CL9, em seguida, o namespace padrão computada seria **CL9.FolderA.FolderB.FolderC**.  
  
 Uma exceção a essa regra ocorre quando a cadeia de hierarquia contém uma pasta de referência da Web.  Por exemplo, se:  
  
-   FolderC foram uma pasta de referência da Web, o espaço para nome seria **CL9.FolderC**.  
  
-   PastaB foram uma pasta de referência da Web, o espaço para nome seria **CL9.FolderB.FolderC**.  
  
 Ou seja, o namespace usa o seguinte formato:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## Consulte também  
 [Implementando geradores de arquivo único](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrar geradores de arquivo único](../extensibility/internals/registering-single-file-generators.md)   
 [Expondo tipos de Designers visuais](../extensibility/internals/exposing-types-to-visual-designers.md)