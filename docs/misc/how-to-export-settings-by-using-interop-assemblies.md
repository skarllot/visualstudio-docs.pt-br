---
title: "Como: exportar configura&#231;&#245;es usando Assemblies de interoperabilidade | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Configurações de IDE, exportar usando assemblies de interoperabilidade"
  - "configurações do usuário [Visual Studio SDK] exportar usando assemblies de interoperabilidade"
  - "IDE, exportando configurações usando assemblies de interoperabilidade"
ms.assetid: d470d4f9-3006-40c3-99db-21abcd5003b8
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Como: exportar configura&#231;&#245;es usando Assemblies de interoperabilidade
Um VSPackage pode exportar as configurações do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\). O IDE usa a implementação do VSPackage do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface. Se o pacote também fornece o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> interface, então o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> interface é usada para determinar como configuração do VSPackage deve ser salvo.  
  
> [!NOTE]
>  Estrutura de pacote gerenciado \(MPF\) fornece um conjunto de classes gerenciadas para facilitar a criação de extensões do Visual Studio. Para executar essa tarefa usando o MPF, consulte [Exportando configurações](../misc/exporting-settings.md).  
  
### Para implementar configurações de exportação em um VSPackage  
  
1.  Implementar o suporte básico para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mecanismo de configurações.  
  
    -   Registre o VSPackage como compatíveis com o mecanismo de configurações definindo um ou mais pontos de configurações personalizadas.  
  
         Para obter mais informações, consulte [Suporte para configurações de usuário](../extensibility/internals/support-for-user-settings.md).  
  
    -   Declarar que implementa o VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>. Se desejar, também pode implementar o VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> interface. Por exemplo:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Certifique\-se de que o VSPackage implementação o <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> método fornece uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface quando chamado com `IID_IVsUserSettings`.  
  
         Opcionalmente, `QueryInterface` pode fornecer um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> interface quando chamado com o `IID_IVsUserSettingsQuery` interface.  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Opcionalmente, o IDE da necessidade de exportar uma determinada configuração de alerta.  
  
     Um VSPackage pode optar por salvar condicionalmente uma configuração que define o estado do ponto de configurações personalizado. Por exemplo, salve apenas se o usuário indica explicitamente uma configuração a ser salvo.  
  
     Nesse caso, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> interface deve ser implementada.  
  
     Se um VSPackage não implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery>, todas as suas informações de estado são salvas durante uma exportação de configurações.  
  
     Um VSPackage pode dar suporte a mais de um ponto de configurações personalizado \(configurações de categoria\). Implementações de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery.NeedExport%2A> método deve verificar o argumento de categoria GUID ou configurações do ponto fornecido personalizar configurações para determinar se um determinado grupo de configurações deve ser salvo.  
  
     No exemplo abaixo, o VSPackage sempre solicita que o estado da barra de comando é salva, mas somente solicitações que seu estado de associação de chave será salvo se um sinalizador foi definido.  
  
3.  Gravar dados de configuração para o arquivo de configurações.  
  
     Para oferecer suporte a configurações de exportação, um VSPackage sempre deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> método.  
  
     A implementação deve lidar com os argumentos passados pelo IDE, o GUID da categoria do ponto que configurações personalizadas e um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> interface.  
  
    1.  Um VSPackage pode dar suporte a mais de um ponto de configurações personalizado \(configurações de categoria\). No exemplo abaixo, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> método chama uma implementação diferente para persistir estado da barra de comando em vez de persistir o estado de associação de chave.  
  
    2.  Um VSPackage deve usar fornecido <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> interface para salvar dados no arquivo de configuração.  
  
         `interface IVsSettingsWriter : IUnknown`  
  
         `{`  
  
         `HRESULT WriteSettingString( LPCOLESTR pszSettingName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingLong( LPCOLESTR pszSettingName, long lSettingValue);`  
  
         `HRESULT WriteSettingBoolean( LPCOLESTR pszSettingName, BOOL fSettingValue);`  
  
         `HRESULT WriteSettingBytes( LPCOLESTR pszSettingName, BYTE *pSettingValue, long lDataLength);`  
  
         `HRESULT WriteSettingAttribute( LPCOLESTR pszSettingName, LPCOLESTR pszAttributeName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingXml( IUnknown *pIXMLDOMNode);`  
  
         `HRESULT WriteSettingXmlFromString( LPCOLESTR szXML);`  
  
         `HRESULT ReportError( LPCOLESTR pszError, VSSETTINGSERRORTYPES dwErrorType);`  
  
         `};`  
  
         O valor de `pszSettingName` argumento fornecido para um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> interface deve identificar exclusivamente cada elemento de dados salvo em uma categoria de configurações.  
  
        > [!NOTE]
        >  Nomes devem ser exclusivos dentro de um ponto de configurações personalizado porque o IDE usa seu GUID e o valor de `pszSettingName` para identificar cada configuração salva. Se mais de um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> método for chamado com o mesmo valor de `pszSettingName`, o valor original é substituído no arquivo de configurações.  
  
         O arquivo de configurações dá suporte ao acesso de dados aleatórios. Conseqüentemente, a ordem de leitura e gravação a operações de configurações não é importante.  
  
         Isso é ilustrado nas implementações de exportação e importação de estado da barra de comando \(`ExportSettings_CommandBa`r e `ImportSettings_CommandBar`\) no exemplo a seguir.  
  
         Se a implementação pode mapear dados para um dos quatro formatos com suporte, há nenhuma restrição sobre como muito ou que tipo de dados pode ser gravado.  
  
        > [!NOTE]
        >  Além dos dados explicitamente escritos e transparentes para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> implementação, a API de configurações também salva [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] informações de versão. Configurações salvas podem ser comparadas com a versão do IDE que gerou durante a importação de configurações.  
  
## Exemplo  
 O exemplo a seguir demonstra como importar e exportar dados de configurações.  
  
```  
// -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export. //    Delegate to the right shell object based on the category GUID. // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to treat import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning, these settings should immediately //             be applied to your personal settings store, //             whether in the registry or the file system. // This write-through cache methodology is essential to to work //             in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether import can be treated as an additive // operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: Before returning, these settings should immediately //             be applied to your personal settings //             store, whether in the registry or the file system. // This write-through cache methodology is essential to allow us //             to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## Consulte também  
 [Suporte para configurações de usuário](../extensibility/internals/support-for-user-settings.md)   
 [Opções e configurações de usuário estendendo](../extensibility/extending-user-settings-and-options.md)   
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Como: usar Assemblies de interoperabilidade para importar configurações](../misc/how-to-use-interop-assemblies-to-import-settings.md)