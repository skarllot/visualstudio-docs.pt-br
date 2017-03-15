---
title: 'Como: registrar tipos de arquivo do Editor | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
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
ms.openlocfilehash: 80b17b10d4c0451a6522f2457ebac05dc8152b3f
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-register-editor-file-types"></a>Como: registrar tipos de arquivo do Editor
A maneira mais fácil de registrar tipos de arquivo do editor é usando os atributos de registro fornecidos como parte do [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] pacote (MPF) framework classes gerenciadas. Se você estiver implementando seu pacote no formato nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], você também pode escrever um script de registro que registra seu editor e aos ramais associados.  
  
## <a name="registration-using-mpf-classes"></a>Usando Classes MPF de registro  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Para registrar tipos de arquivo do editor usando classes MPF  
  
1.  Forneça o <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>classe com os parâmetros adequados para seu editor na classe o VSPackage.</xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Onde ". Exemplo"é a extensão que está registrada para este editor e"32"é o nível de prioridade.  
  
     O `projectGuid` é o GUID para tipos de arquivo diverso, definidos em <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>.</xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject> O tipo de arquivo diverso é fornecido, o arquivo resultante não vai ser uma parte do processo de compilação.  
  
     `TemplateDir`representa a pasta que contém os arquivos de modelo são incluídos com o exemplo editor básico gerenciado.  
  
     `NameResourceID`é definido no arquivo do projeto BasicEditorUI Resources.h e identifica o editor como "Meu Editor".  
  
2.  Substituir o <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>método.</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>  
  
     Na implementação do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>método, chame o <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>método e passar a instância de sua fábrica de editor, como demonstrada abaixo.</xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> </xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Esta etapa registra a fábrica do editor e as extensões de arquivo do editor.  
  
3.  Cancelar o registro de fábricas de editor.  
  
     Fábricas de editor são canceladas automaticamente quando o VSPackage é descartado. Se o objeto de fábrica de editor implementar o <xref:System.IDisposable>interface, seu `Dispose` método é chamado após a fábrica foi não registrada com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].</xref:System.IDisposable>  
  
## <a name="registration-using-a-registry-script"></a>Registro usando um Script de registro  
 Registrando fábricas e tipos de arquivo no formato nativo [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] é feito usando um script de registro para gravar no registro do windows, como ilustrado a seguir.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Para registrar tipos de arquivo do editor usando um script de registro  
  
1.  Em seu script de registro, definir a fábrica do editor e a fábrica de editor de cadeia de caracteres do GUID conforme o `GUID_BscEditorFactory` seção do script de registro a seguir. Além disso, defina a extensão e a prioridade da extensão do editor:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     A extensão de arquivo do editor neste exemplo é identificada como ". rtf" e sua prioridade é "50". As cadeias de caracteres do GUID são definidas no arquivo Resource.h do projeto de exemplo BscEdit.  
  
2.  Registre o VSPackage.  
  
3.  Registre a fábrica do editor.  
  
     A fábrica do editor é registrada o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>implementação.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     As cadeias de caracteres do GUID são definidas no arquivo Resource.h do projeto BscEdit.
