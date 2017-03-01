---
title: "Sequência de inicialização do projeto subtipos | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
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
ms.openlocfilehash: d73ece600a90c73b9b07372e533b6b72681ae1d4
ms.lasthandoff: 02/22/2017

---
# <a name="initialization-sequence-of-project-subtypes"></a>Sequência de inicialização do projeto subtipos
O ambiente constrói um projeto, chamando a implementação de fábrica de projeto base do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> A construção de um subtipo de projeto começa quando o ambiente determina que a lista GUID de tipo de projeto para a extensão de um arquivo de projeto não está vazia. A extensão de arquivo de projeto e o GUID do projeto especificam se o projeto é um [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tipo de projeto. Por exemplo, a extensão. vbproj e {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identificar um [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeto.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Inicialização do ambiente de subtipos de projeto  
 O procedimento a seguir detalha a sequência de inicialização para um sistema de projeto agregada por vários subtipos de projeto.  
  
1.  O ambiente chama o projeto base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, e enquanto o projeto analisa o arquivo de projeto descobre que o tipo de projeto de agregação lista de GUIDs não é `null`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> O projeto interrompe diretamente a criação de seu projeto.  
  
2.  As chamadas de projeto `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>serviço para criar um subtipo de projeto usando a implementação do ambiente do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> Dentro desse método, o ambiente faz chamadas de função recursiva para suas implementações de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>métodos enquanto ele é percorrer a lista de projeto tipo GUIDs, começando com o subtipo de projeto externo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>  
  
     A tabela a seguir detalha as etapas de inicialização.  
  
    1.  A implementação do ambiente do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>chamadas de método ' HrCreateInnerProj ' ' método com a seguinte declaração de função:</xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         Quando essa função é chamada pela primeira vez, ou seja, para o subtipo de projeto externo, os parâmetros `pOuter` e `pOwner` são passados como `null` e a função define o subtipo de projeto externo `IUnknown` para `pOuter`.  
  
    2.  Em seguida chama o ambiente `HrCreateInnerProj` função com o segundo tipo de projeto GUID na lista. Esse GUID corresponde ao segundo subtipo projeto interna revisão para o projeto base na sequência de agregação.  
  
    3.  O `pOuter` agora está apontando para o `IUnknown` do subtipo do projeto externo, e `HrCreateInnerProj` chama sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>seguido por uma chamada para a implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> Em <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>método você passa o controle `IUnknown` do subtipo do projeto externo, `pOuter`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> O projeto de propriedade (subtipo de projeto interno) precisa criar seu objeto de projeto de agregação aqui. No <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>implementação do método que você passe um ponteiro para o `IUnknown` do projeto interno que está sendo agregado.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> Esses dois métodos criam o objeto de agregação e suas implementações devem seguir as regras de agregação para garantir que um subtipo de projeto não acabar mantém uma contagem de referência a mesma.  
  
    4.  `HrCreateInnerProj`chama a sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> Nesse método, o subtipo de projeto faz seu trabalho de inicialização. Por exemplo, você pode registrar eventos de solução em <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>  
  
    5.  `HrCreateInnerProj`é chamado repetidamente até o último GUID (no projeto base) na lista. Para cada uma dessas chamadas, as etapas c a d, são repetidas. `pOuter`aponta para o subtipo de projeto externo `IUnknown` para cada nível de agregação.  
  
 O exemplo a seguir detalha o processo de programação em uma representação aproximado do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>método como ele é implementado pelo ambiente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> O código é apenas um exemplo; não se destina a ser compilado e a verificação de todos os erros tiverem sido removidas por motivos de clareza.  
  
## <a name="example"></a>Exemplo  
  
### <a name="code"></a>Código  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Flavor></xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)
