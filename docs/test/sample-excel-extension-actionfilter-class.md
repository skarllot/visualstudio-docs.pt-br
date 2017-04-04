---
title: "Extensão de amostra do Excel: classe ActionFilter | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 0efcdc317463dc0eaa5ae7d806a0c3cad4a2ac8a
ms.lasthandoff: 02/22/2017

---
# <a name="sample-excel-extension-actionfilter-class"></a>Extensão de exemplo do Excel: classe ActionFilter
Essa classe interna estende a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> e representa um filtro para as ações do teste em um elemento [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## <a name="simple-properties"></a>Propriedades Simples  
 Essas propriedades somente leitura permitem ao desenvolvedor especificar como esse filtro de ação de teste deve ser executado pelo framework de teste de IU codificado. Por exemplo, a propriedade <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fornece o nome do filtro de ação. Outras propriedades obtém o <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> do filtro de ações, o <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, o nome <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> para as ações de teste que são filtradas por esse filtro de ações de teste. Outros indicam se <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> e também se a ação de teste é <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>Método ProcessRule  
 Esse método é chamado pelo framework de teste de IU codificado e executa o filtro no <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> fornecido. Essa substituição específica remove uma ação de escolha do mouse em uma célula quando a próxima ação na pilha enviar pressionamentos de teclas para a célula. Em seguida, ele retorna `false`.  
  
## <a name="private-methods"></a>Métodos privados  
 O método `IsLeftClick` determina se a ação fornecida representa um clique com o botão esquerdo do mouse. O método `AreActionsOnSameExcelCell` determina se duas fornecidas ações são executadas na mesma célula do Excel.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

