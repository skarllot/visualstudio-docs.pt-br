---
title: Carregando os VSPackages | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
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
ms.openlocfilehash: 8f4d4716fbb6b40fd59e3f9daf8ca3d4693f01c5
ms.lasthandoff: 02/22/2017

---
# <a name="loading-vspackages"></a>Carregando os VSPackages
Os VSPackages são carregados no Visual Studio apenas quando sua funcionalidade é necessária. Por exemplo, um VSPackage é carregado quando o Visual Studio usa uma fábrica de projeto ou um serviço que implementa o VSPackage. Esse recurso é chamado de carregamento atrasado, que é usado sempre que possível para melhorar o desempenho.  
  
> [!NOTE]
>  O Visual Studio pode determinar algumas informações de VSPackage, como os comandos que oferece um VSPackage, sem carregar o VSPackage.  
  
 Os VSPackages pode ser definidos como autoload em um contexto de (UI) de interface de usuário específico, por exemplo, quando uma solução estiver aberta. O <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>atributo define neste contexto.</xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Realiza o carregamento automático um VSPackage em um contexto específico  
  
-   Adicionar o `ProvideAutoLoad` atributo para os atributos do VSPackage:  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Consulte os campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>para obter uma lista de contextos de interface do usuário e seus valores GUID.</xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>  
  
-   Definir um ponto de interrupção no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>método.</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>  
  
-   Compile o VSPackage e iniciar a depuração.  
  
-   Carregar uma solução ou criar um.  
  
     O VSPackage carrega e para no ponto de interrupção.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forçar um VSPackage carregar  
 Em algumas circunstâncias, um VSPackage talvez precise forçar VSPackage outro a ser carregado. Por exemplo, um VSPackage leve pode carregar um VSPackage maior em um contexto que não está disponível como um CMDUIContext.  
  
 Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>método para forçar um VSPackage carregar.</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>  
  
-   Inserir este código para o <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>método do VSPackage que força o VSPackage outro carregar:</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Quando o VSPackage é inicializado, ele forçará `PackageToBeLoaded` para carregar.  
  
     Carregamento de equipe não deve ser usado para comunicação de VSPackage. Use [usando e fornecer serviços](../extensibility/using-and-providing-services.md) em vez disso.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Usando um atributo personalizado para registrar um VSPackage  
 Em alguns casos, talvez seja necessário criar um novo atributo de registro para a sua extensão. Você pode usar atributos do registro para adicionar novas chaves de registro ou para adicionar novos valores para as chaves existentes. O novo atributo deve derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, e ele deve substituir o <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A>e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>métodos.</xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> </xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> </xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>  
  
## <a name="creating-a-registry-key"></a>Criar uma chave do registro  
 No código a seguir, o atributo personalizado cria um **personalizado** subchave sob a chave para o VSPackage que está sendo registrado.  
  
```c#  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Criando um novo valor em uma chave do registro existente  
 Você pode adicionar valores personalizados para uma chave existente. O código a seguir mostra como adicionar um novo valor a uma chave de registro de VSPackage.  
  
```c#  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)
