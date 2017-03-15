---
title: "Implementando os VSPackages usando a biblioteca do Visual Studio | Microsoft Docs"
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
  - "Biblioteca do Visual Studio, Implementando os VSPackages"
ms.assetid: 4cbac13f-2a9d-4955-b411-dad79081fdeb
caps.latest.revision: 7
caps.handback.revision: 7
manager: "douge"
---
# Implementando os VSPackages usando a biblioteca do Visual Studio
O `IVsPackageImpl` classe na biblioteca do Visual Studio fornece uma implementação mínima da <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interface.  `IVsPackageImpl`cuida da maioria dos métodos de manutenção <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  Outros métodos que você pode precisar substituir para fornecer uma implementação significativa incluem:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.CreateTool%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>  
  
    > [!NOTE]
    >  O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de pacote gera todo o código discutido aqui.  Você pode economizar tempo usando o modelo para gerar um VSPackage para você.  
  
 Pacotes que são implementadas usando a biblioteca de Visual Studio normalmente herdam uma classe de VSPackage da ATL [Classe de CComObjectRootEx](/visual-cpp/atl/reference/ccomobjectrootex-class) e [Classe de CComCoClass](/visual-cpp/atl/reference/ccomcoclass-class) e IVsPackageImpl da biblioteca do Visual Studio.  Por exemplo, a seguinte é a declaração de classe do exemplo Reference.Package VSPackage:  
  
```  
class ATL_NO_VTABLE BasicPackage :   
    public CComObjectRootEx<CComSingleThreadModel>,  
    public CComCoClass<BasicPackage, &CLSID_BasicPackage>,  
    public IVsPackageImpl<BasicPackage, &CLSID_BasicPackage>,  
    ...  
```  
  
 O `IVsPackageImpl` parâmetros de modelo mostrados são a própria classe VSPackage e um ponteiro para o GUID que identifica o VSPackage.  
  
## Com o suporte de QueryInterface com mapas COM  
 Para obter suporte da ATL para `QueryInterface`, seu mapa COM deve listar as interfaces que a classe implementa.  Por exemplo, a seguinte é o mapa de COM para a classe VSPackage no exemplo de Reference.Package:  
  
```  
BEGIN_COM_MAP(BasicPackage)  
    COM_INTERFACE_ENTRY(IVsPackage)  
    ...  
END_COM_MAP()  
```  
  
 Para obter mais informações sobre COM mapas, consulte [Implementando CComObjectRootEx](/visual-cpp/atl/implementing-ccomobjectrootex) e [Macros de COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20Macros.md).  
  
## Suporte de registro com mapas de registro  
 Biblioteca de Visual Studio usa o estilo ATL.Arquivos RGS para oferecer suporte ao registro de objetos COM.  Para oferecer suporte a token substituição na.Arquivo RGS, biblioteca de Visual Studio usa os mapas de registro.  Símbolos da lista a ser substituído e suporte ao uso de IDs para recursos de tabela de cadeia de caracteres de mapas de registro.  
  
 Por exemplo, a seguir está o mapa de registro para a classe VSPackage no exemplo de Reference.Package:  
  
```  
VSL_BEGIN_REGISTRY_MAP(IDR_BASICPACKAGE_RGS)  
    VSL_REGISTRY_MAP_GUID_ENTRY(CLSID_BasicPackage)  
    VSL_REGISTRY_RESOURCE_STRING_ENTRY(IDS_BASICPACKAGE_REGISTRY_NAME)  
    ...  
VSL_END_REGISTRY_MAP()  
```  
  
## Consulte também  
 [Exemplos VSSDK](../misc/vssdk-samples.md)