---
title: "N&#227;o foi poss&#237;vel encontrar a ferramenta personalizada &#39;ferramenta personalizada&#39; neste sistema. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_instantiate_generator1"
ms.assetid: 51fe9bec-b8bc-4a4c-94aa-15a1f7cc8b6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel encontrar a ferramenta personalizada &#39;ferramenta personalizada&#39; neste sistema.
A ferramenta personalizada não pode ser criada pelo sistema de projeto. A ferramenta personalizada solicitada não será executada porque o sistema do projeto não tem como instanciá\-la. Certifique\-se de que a ferramenta personalizada está corretamente instalada e registrada.  
  
 Esse erro pode ter sido causado por especificando um nome inválido de ferramenta personalizada para o `CustomTool` propriedade para um arquivo específico. Também é possível que o arquivo de projeto \(.vbproj\/.csproj\) foi editado, tornando o valor o `CustomTool` propriedade inválida. Ou talvez você esteja usando um projeto desenvolvido em outro computador, que tem a ferramenta personalizada, mas a ferramenta personalizada não está instalada no seu computador. Para obter mais informações sobre o `CustomTool` propriedade, consulte [Propriedades de arquivo](http://msdn.microsoft.com/pt-br/013c4aed-08d6-4dce-a124-ca807ca08959).  
  
 Esse erro também pode ocorrer se [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) Falha da ferramenta personalizada. Por exemplo, talvez não esteja registrado ou uma DLL necessário pode estar ausente.  
  
## Consulte também  
 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)