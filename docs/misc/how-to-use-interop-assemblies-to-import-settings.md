---
title: "Como: usar Assemblies de interoperabilidade para importar configura&#231;&#245;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Configurações de IDE, importando usando assemblies de interoperabilidade"
  - "IDE, importando as configurações usando assemblies de interoperabilidade"
  - "configurações do usuário [Visual Studio SDK] Importando usando assemblies de interoperabilidade"
ms.assetid: 8a43dbe2-fdc0-471b-8235-3f489b77db0f
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# Como: usar Assemblies de interoperabilidade para importar configura&#231;&#245;es
Um VSPackage pode importar configurações de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado \(IDE\). O IDE usa a implementação do VSPackage do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface para determinar como a configuração do VSPackage deve ser recuperado.  
  
> [!NOTE]
>  Estrutura de pacote gerenciado \(MPF\) fornece um conjunto de classes gerenciadas para facilitar a criação de extensões do Visual Studio. Para executar essa tarefa usando o MPF, consulte [Importando configurações](/visual-cpp/misc/importing-settings).  
  
### Para implementar a importação de configurações em um VSPackage  
  
1.  Implementar o suporte básico para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mecanismo de configurações.  
  
    -   Registre o VSPackage como compatíveis com o mecanismo de configurações definindo um ou mais pontos de configurações personalizadas.  
  
         Para obter mais informações, consulte [Suporte para configurações de usuário](../extensibility/internals/support-for-user-settings.md).  
  
    -   Declarar que o VSPackage implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface, por exemplo:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Certifique\-se de que o VSPackage implementação o <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> método fornece uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface quando chamado com `IID_IVsUserSettings`. Por exemplo:  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Recupere informações de configurações.  
  
     Para recuperar informações de configuração, um VSPackage deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> método.  
  
     Para ler dados, implementação de um VSPackage o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface deve usar os dois primeiros argumentos passados pelo IDE: o GUID da categoria do ponto que configurações personalizadas e um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> interface.  
  
    1.  Implementação do VSPackage o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> método deve verificar a categoria GUID passado e escolha o mecanismo correto para o estado de recuperação.  
  
         No exemplo abaixo, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> método chama uma implementação diferente para recuperar o estado da barra de comando em vez de recuperar o estado de associação de chave.  
  
    2.  Um VSPackage deve usar fornecido <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> interface para recuperar dados para o arquivo de configurações.  
  
        > [!NOTE]
        >  Se altera as informações de configuração como uma função de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versão, a implementação do VSPackage o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> método deve usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> método antes de ler dados para verificar a versão do IDE.  
  
         A interface fornece métodos para diferentes tipos de dados de leitura do arquivo de configurações.  
  
         `interface IVsSettingsReader : IUnknown`  
  
         `{`  
  
         `HRESULT ReadSettingString(WCHAR *pszSettingName, BSTR *pbstrSettingValue);`  
  
         `HRESULT ReadSettingLong(WCHAR *pszSettingName, long *plSettingValue);`  
  
         `HRESULT ReadSettingBoolean(WCHAR *pszSettingName, BOOL *pfSettingValue);`  
  
         `HRESULT ReadSettingAttribute(LPCOLESTR pszSettingName,LPCOLESTR pszAttributeName, BSTR *pbstrSettingValue);  //Internal use only`  
  
         `HRESULT ReadSettingBytes(WCHAR *pszSettingName, BYTE *pSettingValue, long *plDataLength, long lDataMax);`  
  
         `HRESULT ReadVersion(int *pnMajor, int *pnMinor, int *pnBuild);`  
  
         `HRESULT ReportError(WCHAR *pszError);`  
  
         `};`  
  
     O arquivo de configurações oferece suporte a acesso a dados aleatórios, a ordem de leitura e gravação de operações de configurações não é importante.  
  
     Isso é ilustrado na exportação e importação de estado da barra de comando \(`ExportSettings_CommandBa`r e `ImportSettings_CommandBar`\) da implementação no exemplo a seguir.  
  
3.  Valide os dados recuperados.  
  
     As informações de configurações estão contidas em arquivos XML, que podem ser editados manualmente.  
  
> [!IMPORTANT]
>  As informações de configurações podem ficar corrompidas no disco, podem conter configurações específicas da versão e pode ser usadas como um veículo de ataques mal\-intencionados. A validade de cada item de dados retornado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> método deve ser validado.  
  
-   Para verificar o suporte da versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usado para produzir as configurações recuperadas, chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> método para recuperar a versão.  
  
-   Para fazer com que o IDE notificar um usuário que não valida a um elemento de dados importados, um VSPackage chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A> método.  
  
1.  Aplica as informações de configurações.  
  
    1.  A implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> método deve respeitar o valor do terceiro argumento que o IDE passado para ele. Os valores com suporte são membros do <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags> enumeração. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>.  
  
         No exemplo abaixo, a implementação para importar as configurações da barra de comando \(`ImportSettings_Commandbar`\) usa o valor deste argumento para determinar se deve aplicar as configurações para substituir valores existentes ou additively atualizá\-los.  
  
    2.  Você deve implementar uma metodologia de cache write\-through quando aplicar importado configurações.  
  
         As informações de estado no registro ou no sistema de arquivos devem ser atualizadas ao mesmo tempo, como as configurações são aplicadas ao IDE. Isso garante a coerência de configuração e oferece suporte a cenários IDE com várias instâncias.  
  
2.  Como lidar com a importação de configurações de alerta IDE.  
  
     Use retornado `pfRestartRequired` argumento o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> método para informar o IDE se uma reinicialização é necessária para aplicar as configurações importadas.  
  
     Se a implementação do VSPackage do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> método retorna `true`, o usuário é solicitado a reiniciar o IDE.  
  
## Exemplo  
 Este exemplo demonstra como importar e exportar dados de configurações.  
  
```  
static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export and import //    Delegate to the right shell object based on the category GUID // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether to import as an additive operation or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## Consulte também  
 [Como: exportar configurações usando Assemblies de interoperabilidade](../misc/how-to-export-settings-by-using-interop-assemblies.md)   
 [Suporte para configurações de usuário](../extensibility/internals/support-for-user-settings.md)   
 [Opções e configurações de usuário estendendo](../extensibility/extending-user-settings-and-options.md)   
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3)