---
title: Managed Extensibility Framework no Editor | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 10
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 6a5cb0ae0f8da6af939588ad358e6b5b1b3b108e
ms.lasthandoff: 02/22/2017

---
# <a name="managed-extensibility-framework-in-the-editor"></a>Managed Extensibility Framework no Editor
O editor é criado usando componentes Managed Extensibility Framework (MEF). Você pode criar seus próprios componentes MEF para estender o editor, e seu código pode consumir componentes do editor também.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Visão geral do Managed Extensibility Framework  
 O MEF é uma biblioteca .NET que permite adicionar e modificar recursos de um aplicativo ou componente que segue o modelo de programação de MEF. Editor do Visual Studio pode fornecer e consumir componentes do MEF.  
  
 O MEF está contido no assembly do .NET Framework versão 4 System.ComponentModel.Composition.dll.  
  
 Para obter mais informações sobre o MEF, consulte [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Componentes e contêineres de composição  
 Uma parte do componente é uma classe ou membro de uma classe que pode fazer uma (ou ambas) das seguintes opções:  
  
-   Consumir outro componente  
  
-   Ser consumida por outro componente  
  
 Por exemplo, considere um aplicativo de compras que tem um componente de entrada de ordem que depende de dados de disponibilidade do produto fornecidos por um componente de estoque do depósito. Em termos MEF, a parte de inventário pode *exportar* dados de disponibilidade do produto e a lata de parte de entrada de ordem *importar* os dados. A parte de entrada de ordem e a parte de inventário não precisa saber sobre outros; o *contêiner de composição* (fornecido pelo aplicativo host) é responsável por manter o conjunto de exportações e resolvendo o exporta e importa.  
  
 O contêiner de composição, <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, normalmente é de propriedade pelo host.</xref:System.ComponentModel.Composition.Hosting.CompositionContainer> O contêiner de composição mantém um *catálogo* componentes exportado.  
  
### <a name="exporting-and-importing-component-parts"></a>Exportando e importando componentes  
 Você pode exportar qualquer funcionalidade, como ele é implementado como uma classe pública ou um membro público de uma classe (propriedade ou método). Você não precisa derivar sua parte do componente de <xref:System.ComponentModel.Composition.Primitives.ComposablePart>.</xref:System.ComponentModel.Composition.Primitives.ComposablePart> Em vez disso, você deve adicionar um <xref:System.ComponentModel.Composition.ExportAttribute>de atributo para a classe ou membro da classe que você deseja exportar.</xref:System.ComponentModel.Composition.ExportAttribute> Este atributo especifica a *contrato* pelo qual componente outra parte pode importar sua funcionalidade.  
  
### <a name="the-export-contract"></a>O contrato de exportação  
 O <xref:System.ComponentModel.Composition.ExportAttribute>define a entidade (classe, interface ou estrutura) que está sendo exportada.</xref:System.ComponentModel.Composition.ExportAttribute> Normalmente, o atributo export leva um parâmetro que especifica o tipo da exportação.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Por padrão, o <xref:System.ComponentModel.Composition.ExportAttribute>atributo define um contrato que é o tipo de classe da exportação.</xref:System.ComponentModel.Composition.ExportAttribute>  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 No exemplo, o padrão `[Export]` atributo equivale a `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Você também pode exportar uma propriedade ou método, conforme mostrado no exemplo a seguir.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>Importando uma exportação MEF  
 Quando você deseja consumir uma exportação MEF, você deve saber o contrato (geralmente o tipo) pelo qual ele foi exportado e adicione um <xref:System.ComponentModel.Composition.ImportAttribute>atributo que tem esse valor.</xref:System.ComponentModel.Composition.ImportAttribute> Por padrão, o atributo import assume um parâmetro, que é o tipo da classe que ele modifica. As seguintes linhas de importação de código do <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>tipo.</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Obtendo a funcionalidade do Editor de uma parte do componente MEF  
 Se seu código existente é uma parte do componente MEF, você pode usar MEF metadados para consumir componentes do editor.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Consumir funcionalidade do editor de uma parte do componente MEF  
  
1.  Adicione referências para System.Composition.ComponentModel.dll, que está no cache de assembly global (GAC), e os assemblies do editor.  
  
2.  Adicionar o relevantes usando as instruções.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Adicionar o `[Import]` atributo à sua interface de serviço, da seguinte maneira.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Quando você tiver obtido o serviço, você pode utilizar qualquer um de seus componentes.  
  
5.  Quando você tiver compilado seu assembly, colocá-lo na... Pasta \Common7\IDE\Components\ de sua instalação do Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)
