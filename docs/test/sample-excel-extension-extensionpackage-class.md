---
title: "Extensão de amostra do Excel: Classe ExtensionPackage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
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
ms.openlocfilehash: f8f8608204c6bf33e04d2dd18d09f0dad98f9def

---
# <a name="sample-excel-extension-extensionpackage-class"></a>Extensão de exemplo do Excel: classe ExtensionPackage
Essa classe estende a classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> e fornece o ponto de entrada para a extensão de teste de IU codificado. que está testando uma Planilha [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## <a name="assembly-attribute"></a>Atributos do Assembly  
 O arquivo começa com um atributo de assembly que identifica o assembly como uma extensão de teste de interface do usuário.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Esse atributo declara o nome de classe base, o nome da classe de pacote e o nome de classe totalmente qualificado da classe de pacote de extensão personalizada.  
  
## <a name="simple-properties"></a>Propriedades Simples  
 Essa classe tem propriedades que fornecem valores que são usados pela estrutura de teste da interface do usuário codificada para identificar e descrever a extensão e o assembly. Consulte os comentários do código para obter mais informações.  
  
## <a name="getservice-method"></a>Método GetService  
 O método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> é o único ponto de entrada usado pela estrutura de teste de interface do usuário codificada para obter acesso ao gerente de tecnologia, o provedor de propriedade e ao filtro de ação, conforme identificado pela classe base de cada objeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Estendendo testes de IU codificados e gravações da ação para dar suporte ao Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)


<!--HONumber=Feb17_HO4-->


