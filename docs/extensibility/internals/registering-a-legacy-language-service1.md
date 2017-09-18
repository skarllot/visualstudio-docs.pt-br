---
title: Registrando um Service1 de idioma herdado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 22
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
ms.openlocfilehash: 78a13e2725bdf749f5e0cfddc373bdd6f9e8cffb
ms.lasthandoff: 02/22/2017

---
# <a name="registering-a-legacy-language-service"></a>Registrar um serviço de linguagem herdado
Na estrutura de pacote gerenciado (MPF), o serviço de linguagem é dedicaram por um VSPackage (consulte [VSPackages](../../extensibility/internals/vspackages.md)) e é registrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adicionando chaves do registro e entradas. Esse processo de registro é feito parcialmente durante a instalação e parcialmente em tempo de execução.  
  
## <a name="register-the-language-service-by-using-attributes"></a>Registrar o serviço de linguagem, usando atributos  
 Os seguintes atributos são usados para registrar um serviço de linguagem.  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute></xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute></xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute></xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute></xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
-   <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute></xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
 Esses atributos são explicados abaixo  
  
### <a name="provideserviceattribute"></a>ProvideServiceAttribute  
 Esse atributo registra seu serviço de idioma como um serviço.  
  
### <a name="example"></a>Exemplo  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute  
 Esse atributo registra seu serviço de linguagem especificamente como um serviço de linguagem. Ele permite que você defina opções que especificam os recursos que oferece o serviço de linguagem. O exemplo mostra um subconjunto das opções que pode fornecer um serviço de linguagem. Para o conjunto completo de opções de serviço de linguagem, consulte <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
### <a name="example"></a>Exemplo  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute  
 Esse atributo associa o seu serviço de linguagem com uma extensão de arquivo. Sempre que um arquivo com a extensão é carregado em qualquer projeto, o serviço de linguagem é iniciado e usado para exibir o conteúdo do arquivo.  
  
### <a name="example"></a>Exemplo  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute  
 Esse atributo registra um local do qual código expansão ou trecho modelos são obtidos. Essas informações são usadas pelo **navegador de trechos de código** e pelo editor quando um trecho de código é inserido no arquivo de origem.  
  
### <a name="example"></a>Exemplo  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute  
 Esse atributo registra uma página de propriedades a serem exibidos no **opções** caixa de diálogo sob o **Editor de texto** categoria. Use um desses atributos para cada página a ser exibido para o serviço de linguagem. Se você precisar organizar páginas em uma estrutura de árvore, use os atributos adicionais para definir cada nó da árvore.  
  
### <a name="example"></a>Exemplo  
 Este exemplo mostra duas páginas de propriedade, **opções** e **recuo**e um nó que contém a segunda página de propriedade.  
  
```c#  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## <a name="proffer-the-language-service-at-runtime"></a>Oferecer o serviço de linguagem em tempo de execução  
 Quando o pacote de idioma é carregado, você deve informar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que seu serviço de linguagem está pronto. Para fazer isso, proffering o serviço. Isso é feito o <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>método.</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Além disso, você precisa iniciar um timer que chama o seu serviço de linguagem durante períodos de inatividade para que análise do plano de fundo pode ser realizada. O timer de ociosidade também é usado para atualizar propriedades do documento, se você tiver implementado um por meio de <xref:Microsoft.VisualStudio.Package.DocumentProperties>classe.</xref:Microsoft.VisualStudio.Package.DocumentProperties> Para suportar um timer, o pacote deve implementar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent>interface (somente o <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A>método precisa ser totalmente implementadas; os métodos restantes podem retornar valores padrão).</xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent>  
  
### <a name="example"></a>Exemplo  
 Este exemplo mostra uma abordagem típica para proffering um serviço e fornecer um timer de ociosidade.  
  
```c#  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal     |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```
