---
title: "Extensão de teste de IU codificado de exemplo para Excel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 13
ms.author: mlearned
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
ms.openlocfilehash: 477122449be01eb66f97044368f9c07cc29bf5c8

---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Extensão de teste de IU codificado de amostra para Excel
O componente de extensão da amostra é executado no processo de teste de IU codificado do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e é ligeiramente hierárquico com a classe `ExtensionPackage` na base. As classes `TechnologyManager`, `ActionFilter` e `PropertyProvider` estão no próximo nível, com os elementos de controle no nível superior.  
  
 ![Arquitetura de extensão de teste do Excel](../test/media/excel_extarch.png "Excel_ExtArch")  
Arquitetura de extensão do Excel  
  
## <a name="extension-points"></a>Pontos de extensão  
 Essas classes representam os pontos de extensão implementados na amostra para habilitar o teste para de IU codificado para [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
### <a name="extensionpackage"></a>ExtensionPackage  
 Herdado da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, este é o ponto de entrada para a extensão de teste de IU codificado. A implementação dessa classe abstrata fornece o acesso interno ao framework de teste de IU codificado para seu gerente de tecnologia de teste de IU personalizado, provedor de propriedade de teste de IU e o filtro de ação de teste de IU para testar a nova IU. Para obter mais informações, consulte [Classe ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).  
  
### <a name="technologymanager"></a>TechnologyManager  
 Herdado da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, essa classe fornece um gerente de tecnologia para teste de gravação e reprodução. Para obter mais informações, consulte [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).  
  
### <a name="actionfilter"></a>ActionFilter  
 Herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, essa classe fornece uma classe base para agregar resultados de ações de teste semelhantes em um único resultado do teste. Para obter mais informações, consulte [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md).  
  
### <a name="technology-elements"></a>Elementos de tecnologia  
 Uma classe base herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> fornece a base para os elementos de tecnologia em seus testes de IU que podem ser registrados e reproduzidos. Para obter mais informações, consulte [Classes de Elemento](../test/sample-excel-extension-element-classes.md).  
  
### <a name="propertyprovider"></a>PropertyProvider  
 Herdada da classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>, essa classe fornece uma classe base para dar suporte às propriedades dos elementos de interface do usuário para gravação e reprodução de teste. Para obter mais informações, consulte [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [ExtensionPackage Class](../test/sample-excel-extension-extensionpackage-class.md)   
 [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)   
 [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md)   
 [Classes de elementos](../test/sample-excel-extension-element-classes.md)   
 [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md)


<!--HONumber=Feb17_HO4-->


