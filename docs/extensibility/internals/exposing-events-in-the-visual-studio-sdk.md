---
title: Expondo eventos no Visual Studio SDK | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 16
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
ms.openlocfilehash: 582c6d868855d1d2e6d0ad502e57bb30dc95f7d9
ms.lasthandoff: 02/22/2017

---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Expondo eventos no Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]permite que você da fonte de eventos usando a automação. É recomendável que a fonte de eventos para projetos e itens de projeto.  
  
 Eventos são recuperados pelos consumidores de automação do <xref:EnvDTE.DTEClass.Events%2A>objeto ou <xref:EnvDTE.DTEClass.GetObject%2A>("EventObjectName").</xref:EnvDTE.DTEClass.GetObject%2A> </xref:EnvDTE.DTEClass.Events%2A> O ambiente chama `IDispatch::Invoke` usando o `DISPATCH_METHOD` ou `DISPATCH_PROPERTYGET` sinalizadores para retornar um evento.  
  
 O processo a seguir explica como os eventos específicos de VSPackage são retornados.  
  
1.  O ambiente é iniciado.  
  
2.  Ele lê a partir do registro todos os nomes de valores das chaves de automação, AutomationEvents e AutomationProperties de todos os VSPackages e armazena esses nomes em uma tabela.  
  
3.  Chama um consumidor de automação, neste exemplo, `DTE.Events.AutomationProjectsEvents` ou `DTE.Events.AutomationProjectItemsEvents`.  
  
4.  O ambiente localiza o parâmetro de cadeia de caracteres na tabela e carrega o VSPackage correspondente.  
  
5.  O ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>método usando o nome passado na chamada; neste exemplo, AutomationProjectsEvents ou AutomationProjectItemsEvents.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
6.  O VSPackage cria um objeto de raiz que tem métodos como `get_AutomationProjectsEvents` e `get_AutomationProjectItemEvents` e, em seguida, retorna um ponteiro de IDispatch ao objeto.  
  
7.  O ambiente chama o método apropriado com base no nome passado para a chamada de automação.  
  
8.  O `get_` método cria outro objeto IDispatch com base em eventos que implementa o `IConnectionPointContainer` interface e o `IConnectionPoint` da interface e retorna um IDispatchpointer ao objeto.  
  
 Para expor um evento por meio da automação, você deve responder para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>e procure as cadeias de caracteres que você adiciona ao registro.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> No exemplo de projeto básico, as cadeias de caracteres são "BscProjectsEvents" e "BscProjectItemsEvents".  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Entradas de registro de exemplo de projeto básico  
 Esta seção mostra onde adicionar valores de automação de evento no registro.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<>\>\AutomationEvents]  
  
 "AutomationProjectEvents"="retorna o objeto AutomationProjectEvents"  
  
 "AutomationProjectItemEvents"="retorna o objeto AutomationProjectItemsEvents"  
  
|Nome|Tipo|Intervalo|Descrição|  
|----------|----------|-----------|-----------------|  
|Padrão (@)|REG_SZ|Não usado|Não utilizado. Você pode usar o campo de dados para obter a documentação.|  
|AutomationProjectsEvents|REG_SZ|Nome do seu objeto de evento.|Somente o nome da chave é relevante. Você pode usar o campo de dados para obter a documentação.<br /><br /> Este exemplo vem da amostra de projeto básico.|  
|AutomationProjectItemEvents|REG_SZ|Nome do seu objeto de evento|Somente o nome da chave é relevante. Você pode usar o campo de dados para obter a documentação.<br /><br /> Este exemplo vem da amostra de projeto básico.|  
  
 Quando qualquer um dos seus objetos de evento são solicitados por um consumidor de automação, cria um objeto de raiz que tem métodos para qualquer evento que suporta o VSPackage. O ambiente chama apropriado `get_` método nesse objeto. Por exemplo, se `DTE.Events.AutomationProjectsEvents` é chamado, o `get_AutomationProjectsEvents` método no objeto raiz é invocado.  
  
 ![Eventos de projeto do Visual Studio](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Modelo de automação de eventos  
  
 A classe `CProjectEventsContainer` representa o objeto de origem para BscProjectsEvents, enquanto `CProjectItemsEventsContainer` representa o objeto de origem para BscProjectItemsEvents.  
  
 Na maioria dos casos, você deve retornar um novo objeto para cada solicitação de evento como a maioria dos objetos de evento usa um objeto de filtro. Quando você acionar o evento, verifica esse filtro para verificar que o manipulador de eventos está sendo chamado.  
  
 AutomationEvents.h e AutomationEvents.cpp contêm declarações e implementações de classes na tabela a seguir.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|`CAutomationEvents`|Implementa um objeto de raiz do evento, obtido a `DTE.Events` objeto.|  
|`CProjectsEventsContainer` e `CProjectItemsEventsContainer`|Implemente os objetos de fonte de eventos que acionam os eventos correspondentes.|  
  
 O exemplo de código a seguir mostra como responder a uma solicitação para um objeto de evento.  
  
```cpp#  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 No código acima, `g_wszAutomationProjects` é o nome de sua coleção de projeto ("FigProjects"), `g_wszAutomationProjectsEvents` ("FigProjectsEvents") e `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") são os nomes dos eventos do projeto e itens de projeto eventos que são originados de sua implementação de VSPackage.  
  
 Objetos de evento são recuperados do mesmo local central, o `DTE.Events` objeto. Dessa forma, todos os objetos de evento são agrupados juntos para que um usuário final não precisa procurar o modelo de objeto inteiro para localizar um evento específico. Isso também permite fornecer seus objetos de VSPackage específicos, em vez de exigir que você implemente seu próprio código para eventos de todo o sistema. No entanto, para o usuário final, que deve encontrar um evento para o `ProjectItem` interface, não é imediatamente clara de onde esse objeto é recuperado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [Exemplos de VSSDK](../../misc/vssdk-samples.md)
