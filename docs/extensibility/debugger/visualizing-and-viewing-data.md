---
title: Visualizando e exibindo dados | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 3f2317abd4bfaf6ebf8151812cf15541a1c94ecf
ms.contentlocale: pt-br
ms.lasthandoff: 04/05/2017

---
# <a name="visualizing-and-viewing-data"></a>Visualizando e exibindo dados
Visualizadores de tipo e apresentar dados visualizadores personalizados de forma que seja significativo rapidamente para um desenvolvedor. O avaliador de expressão (EE) pode dar suporte a visualizadores de tipo de terceiros bem como fornecer seus próprio visualizadores personalizados.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Determina quantos visualizadores de tipo e os visualizadores personalizados estão associados com o tipo do objeto chamando o [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) método. Se houver Visualizador de pelo menos um tipo ou o visualizador personalizado, o Visual Studio chama o [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) método para recuperar uma lista desses visualizadores e visualizadores (na verdade, uma lista de `CLSID`que implementam o visualizadores e visualizadores) e apresenta ao usuário.  
  
## <a name="supporting-type-visualizers"></a>Suporte a visualizadores de tipo  
 Há um número de interfaces que o EE deve implementar para dar suporte a visualizadores de tipo. Essas interfaces podem ser divididas em duas amplas categorias: aqueles que lista os visualizadores de tipo e aqueles que acessam os dados de propriedade.  
  
### <a name="listing-type-visualizers"></a>Visualizadores de tipo de listagem  
 O EE dá suporte à lista de visualizadores de tipo em sua implementação de `IDebugProperty3::GetCustomViewerCount` e `IDebugProperty3::GetCustomViewerList`. Esses métodos passam a chamada para os métodos correspondentes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 O [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) é obtido chamando [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Esse método requer o [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) interface, que é obtida a [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interface passado para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService`também requer o [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) e [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interfaces que foram passados para `IDebugParsedExpression::EvaluateSync`. A interface final necessária para criar o `IEEVisualizerService` interface é a [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface, que implementa o EE. Essa interface permite que as alterações sejam feitas para a propriedade sendo visualizada. Todos os dados de propriedade é encapsulado em um [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) interface, que também é implementado pelo EE.  
  
### <a name="accessing-property-data"></a>Acessando dados de propriedade  
 Acessando dados de propriedade é feito por meio de [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) interface. Para obter essa interface, o Visual Studio chama [QueryInterface](/cpp/atl/queryinterface) no objeto de propriedade para obter o [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) interface (implementado no mesmo objeto que implementa o [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) interface) e, em seguida, chama o [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) método para obter o `IPropertyProxyEESide` interface.  
  
 Todos os dados passados dentro e fora do `IPropertyProxyEESide` interface é encapsulada no [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) interface. Essa interface representa uma matriz de bytes e é implementada pelo Visual Studio e o EE. Quando dados uma propriedade dos será alterado, o Visual Studio cria um `IEEDataStorage` objeto contém os novos dados e chamadas [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) com esse objeto de dados para obter um novo `IEEDataStorage` objeto que, por sua vez, é passado para [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) para atualizar os dados da propriedade. `IPropertyProxyEESide::CreateReplacementObject`permite que o EE criar uma instância de sua própria classe que implementa o `IEEDataStorage` interface.  
  
## <a name="supporting-custom-viewers"></a>Suporte a visualizadores personalizados  
 O sinalizador `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` é definido no `dwAttrib` campo o [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estrutura (retornado por uma chamada para [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) para indicar que o objeto tem um visualizador personalizado associado a ele. Quando esse sinalizador é definido, o Visual Studio obterá o [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) de interface do [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface usando [QueryInterface](/cpp/atl/queryinterface).  
  
 Se o usuário seleciona um visualizador personalizado, o Visual Studio cria o visualizador personalizado usando o visualizador `CLSID` fornecido pelo `IDebugProperty3::GetCustomViewerList` método. O Visual Studio, em seguida, chama [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) para mostrar o valor para o usuário.  
  
 Normalmente, `IDebugCustomViewer::DisplayValue` apresenta uma exibição somente leitura dos dados. Para permitir que as alterações nos dados, o EE deve implementar uma interface personalizada que dá suporte à alteração de dados em um objeto de propriedade. O `IDebugCustomViewer::DisplayValue` método usa essa interface personalizada para oferecer suporte a alteração dos dados. O método procura a interface personalizada no `IDebugProperty2` interface passado como o `pDebugProperty` argumento.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Suportando digite visualizadores e visualizadores personalizados  
 Um EE pode dar suporte a visualizadores de tipo e visualizadores personalizados no [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) métodos. Primeiro, o EE adiciona o número de visualizadores personalizados que está fornecendo para o valor retornado pelo [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) método. Segundo, o EE acrescenta o `CLSID`s dos seus próprios visualizadores personalizados para a lista retornada pelo [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)   
 [Visualizador de Tipo e Visualizador Personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
