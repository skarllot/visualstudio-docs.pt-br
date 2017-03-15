---
title: "How to: Create an XML Schema from an XML Document | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create an XML Schema from an XML Document
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O Editor de XML permite que você crie uma linguagem XSD \(definição de esquema XML\) de um documento XML.  O documento de instância XML determina como o esquema é gerado da seguinte maneira:  
  
-   Se o documento XML não tiver nenhum esquema ou DTD \(definição de tipo de documento\) associado a ele, os dados no documento XML serão usados para inferir um novo esquema XML.  
  
-   Se o documento XML contiver um DTD associado, o DTD externo e o subconjunto interno serão convertidos em um esquema XML correspondente.  
  
-   Se o documento XML contiver dados internos com um esquema XDR reduzido de dados XML, o esquema XDR será convertido em um esquema XML correspondente.  
  
 Os esquemas que são criados são, em seguida, usados para fornecer o IntelliSense para o documento XML.  
  
 Para obter mais informações sobre o mecanismo de inferência do esquema, consulte [Inferring an XML Schema](../Topic/Inferring%20an%20XML%20Schema.md).  
  
### Para criar um esquema XML  
  
1.  Carregue um documento de instância XML no Editor de XML.  
  
2.  Clique no botão **Criar Esquema** da **Barra de Ferramentas**.  
  
     Um documento de esquema XML é criado e aberto para cada namespace encontrado no documento de instância XML.  Cada esquema é aberto como um arquivo variado temporário.  
  
     Os esquemas podem ser salvos no disco, adicionados ao seu projeto ou descartados.  
  
    > [!NOTE]
    >  O comando **Criar Esquema** também está disponível no menu de atalho do Editor de XML e no menu **XML**.  
  
## Consulte também  
 [XML Editor](../xml-tools/xml-editor.md)