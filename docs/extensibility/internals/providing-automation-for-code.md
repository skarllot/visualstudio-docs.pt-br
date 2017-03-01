---
title: "Oferecendo automação para código | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 34f98092a5417ea22f8f2d3ec9183adb4624532e
ms.lasthandoff: 02/22/2017

---
# <a name="providing-automation-for-code"></a>Fornece automação de código
Não é necessário criar um modelo de automação para seu código. O SDK de ambiente não fornece um exemplo para fazê-lo. Para obter informações sobre modelos de código, consulte o <xref:EnvDTE.CodeModel>objeto.</xref:EnvDTE.CodeModel>  
  
 Para implementar um modelo de código, você deve implementar quaisquer interfaces que são determinadas pela sua estrutura de dados interna. Os objetos devem ser derivados de `IDispatch` classe.  
  
 Os objetos que você pode estender, <xref:EnvDTE.CodeModel>e <xref:EnvDTE.FileCodeModel>, estão disponíveis no <xref:EnvDTE.Project>de objeto e a seguinte aparência:</xref:EnvDTE.Project> </xref:EnvDTE.FileCodeModel> </xref:EnvDTE.CodeModel>  
  
 <xref:EnvDTE.Project.CodeModel%2A></xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A></xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Você pode optar por implementar apenas a `CodeModel` ou `FileCodeModel` interface no objeto de retorno de seu `Project` e <xref:EnvDTE.ProjectItem>objetos.</xref:EnvDTE.ProjectItem> Forneça qualquer funcionalidade a partir dessa interface é apropriada para seu sistema de projeto.  
  
 Se você quiser adicionar recursos, como métodos ou propriedades, que não estão disponíveis no padrão `CodeModel` e `FileCodeModel` interfaces, crie sua própria interface que herda do padrão. Certifique-se de documentá-lo com o sistema de projeto para que os usuários finais Saiba procurá-lo. Retornar a interface padrão, mas o usuário pode chamar o `QueryInterface` método ou conversão para sua interface, se ele é conhecido por existir.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)
