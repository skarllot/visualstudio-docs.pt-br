---
title: Expondo objetos do projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
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
ms.openlocfilehash: 00c29645e8c4516d0a4c30a5e2c249e1fbffca19
ms.lasthandoff: 02/22/2017

---
# <a name="exposing-project-objects"></a>Expondo objetos do projeto
Tipos de projeto personalizado podem fornecer objetos de automação para permitir acesso ao projeto usando interfaces de automação. Cada tipo de projeto é esperado para fornecer o padrão <xref:EnvDTE.Project>objeto de automação que é acessado de <xref:EnvDTE.Solution>, que contém uma coleção de todos os projetos que estão abertos no IDE.</xref:EnvDTE.Solution> </xref:EnvDTE.Project> Cada item no projeto deve ser exposta por um <xref:EnvDTE.ProjectItem>objeto é acessado com <xref:Project.ProjectItems>.</xref:Project.ProjectItems> </xref:EnvDTE.ProjectItem> Além desses objetos de automação padrão, projetos podem optar por oferecer objetos de automação específicos do projeto.  
  
 Você pode criar objetos de automação de nível raiz personalizada que você pode acessar tardia da raiz DTE objeto usando `DTE.<customeObjectName>` ou `DTE.GetObject(“<customObjectName>”)`. Por exemplo, Visual C++ cria a coleção de projeto específicos do projeto C++ chamada "VCProjects" que você pode acessar usando DTE. VCProjects ou DTE. GetObject("VCProjects"). Você também pode criar um Project.Object, que é exclusivo para o tipo de projeto, um Project.CodeModel, que pode ser consultado para seu objeto mais derivado, um item de projeto, que expõe ProjectItem.Object e um ProjectItem.FileCodeModel.  
  
 É uma convenção comum para projetos para expor uma coleção de projeto personalizados, específicos do projeto. Por exemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] cria uma coleção de projeto específico de C++ que você pode acessar usando `DTE.VCProjects` ou `DTE.GetObject("VCProjects")`. Você também pode criar um `Project.Object`, que é exclusivo para o tipo de projeto, um `Project.CodeModel`, que pode ser consultado para seu objeto mais derivado, uma `ProjectItem`, que expõe `ProjectItem.Object`e um `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Para contribuir com um objeto de VSPackage específico para um projeto  
  
1.  Adicione as chaves apropriadas para o arquivo pkgdef do VSPackage.  
  
     Por exemplo, aqui estão as configurações de pkgdef para o projeto de linguagem C++:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Implementar o código de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>método, como no exemplo a seguir.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     No código, `g_wszAutomationProjects` é o nome da sua coleção de projeto. O `GetAutomationProjects` método cria um objeto que implementa o `Projects` interface e retorna um `IDispatch` ponteiro para o objeto de chamada, conforme mostrado no exemplo de código a seguir.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Você deve escolher um nome exclusivo para o objeto de automação. Conflitos de nome serão imprevisíveis e colisões fará um nome de objeto conflitante arbitrariamente gerado se vários tipos de projeto usam o mesmo nome. Você deve incluir o nome da sua empresa ou alguns aspectos exclusivos do seu nome de produto no nome do objeto de automação.  
  
     Personalizado `Projects` objeto da coleção é um ponto de entrada de conveniência para a parte restante do seu modelo de projeto de automação. O objeto de projeto também é acessível a partir de <xref:EnvDTE.Solution>coleção de projeto.</xref:EnvDTE.Solution> Depois de ter criado as entradas apropriadas de código e do registro que fornecem os consumidores com `Projects` objetos de coleção, sua implementação deve fornecer o restante objetos padrão para o modelo de projeto. Para obter mais informações, consulte [projeto de modelagem](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
