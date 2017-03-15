---
title: "Exportando configura&#231;&#245;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE, exportando as configurações usando a estrutura de pacote gerenciado"
  - "estrutura de pacote gerenciado, exportar configurações de ambiente"
  - "as configurações do usuário [Visual Studio SDK] exportar usando gerenciado a estrutura de pacote"
  - "Configurações de IDE, exportar usando gerenciadas estrutura de pacote"
ms.assetid: cb3ddb38-4e75-4f05-a83a-8396345bc36c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Exportando configura&#231;&#245;es
O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado \(IDE\) usa classes que implementam o <xref:Microsoft.VisualStudio.Shell.IProfileManager> interface e classes que estão registrados como uma determinada implementação VSPackage para salvar o estado de um VSPackage de suporte.  
  
 Porque o IDE cria uma instância da classe que implementa o <xref:Microsoft.VisualStudio.Shell.IProfileManager> interface para oferecer suporte as configurações, <xref:Microsoft.VisualStudio.Shell.IProfileManager> deve ser implementado em uma classe independente.  
  
> [!NOTE]
>  Não implementam <xref:Microsoft.VisualStudio.Shell.IProfileManager> na classe que implementa <xref:Microsoft.VisualStudio.Shell.Package>.  
  
### Para implementar a exportação de configurações  
  
1.  Declara a classe que implementa o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] as configurações.  
  
     Declarar uma classe que implementar a <xref:Microsoft.VisualStudio.Shell.IProfileManager> interface e fornecê\-lo com um GUID.  
  
    > [!NOTE]
    >  Classes que implementam <xref:Microsoft.VisualStudio.Shell.IProfileManager> também deve implementar <xref:System.ComponentModel.IComponent>.  Isso pode ser feito, derivando da classe de <xref:System.ComponentModel.Component>.  
  
     Por exemplo:  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  Certifique\-se de que a classe que implementa as configurações obtém informações de estado correto.  Este procedimento é específico para cada VSPackage e pode envolver obtendo estado de automação, consultando as chaves do registro ou consultando o VSPackage.  
  
     Normalmente, como no exemplo a seguir usa a implementação da <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> método para validar e testar as informações de estado VSPackage.  
  
    > [!NOTE]
    >  O <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> método também é chamado pelo IDE quando inicializar o VSPackage que ele suporta.  
  
     Neste caso, a implementação de <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> método faz essas coisas:  
  
    -   Obtém o acesso a informações sobre o estado na configuração atual VSPackage e informações de configuração armazenadas no registro.  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   Dependendo do valor retornado pela `MakeCurrentSettingTheDefault` método do VSPackage, ele as configurações do Registro atualiza ou usando o estado atual do VSPackage ou o estado, usando as configurações do registro.  
  
        ```vb#  
        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
        Else   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
        }else{  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
        }  
        ```  
  
         Para manter a simplicidade neste exemplo, a menos que o `MakeCurrentSettingsTheDefault` método retorna `true`, o estado atual é sempre redefinido como o padrão que é armazenado no registro.  
  
3.  Certifique\-se de que a classe que implementa as configurações também persiste o estado em disco.  
  
     A gravação real de informações de estado para o arquivo de configurações de disco sempre deve ser executada pela implementação da classe de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> método.  As especificidades de uma operação de gravador configurações dependem da implementação.  
  
     No entanto, a classe deve obter acesso às informações de estado e deve usar o fornecido <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> interface para salvar dados no arquivo de configuração.  
  
     Normalmente, como no exemplo a seguir, a implementação de <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> método não valida as informações de estado.  A validação é executada na <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> método.  Em vez disso, a implementação simplesmente obtém acesso às informações de estado e grava\-lo, nesse caso, como dados de seqüência de caracteres.  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        ' Information is stored in a StateObject   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
        writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
    End If  
  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
    if (mySvc != null) {  
      // Information is stored in a StateObject  
      StateObject myState = mySvc.MyPackage.packageState;  
     writer.WriteSettingString(   
                                "PbrsAlpha",   
                                (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
      writer.WriteSettingString(   
                                "PbrsShowDesc",   
                                (myState.HelpVisible ? "1" : "0"));  
    }  
    ```  
  
     Detalhes de implementação são:  
  
    -   Com dados explicitamente por escrito e transparentes para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> a implementação de método, a API de configurações também salva [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] as informações de versão.  Portanto, a configurações salvas podem ser comparadas com a versão do IDE que as gerou durante a importação de configurações.  
  
    -   O valor da `pszSettingName` argumento fornecido para um método para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> interface deve identificar com exclusividade cada elemento de dados salvo em uma categoria de configurações.  
  
        > [!NOTE]
        >  Nomes só devem ser exclusivos dentro do escopo da implementação da classe.  O IDE usa o GUID da classe que implementa as configurações e o valor de `pszSettingName` para identificar cada configuração salva.  Se mais de um <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> método que tenham as mesmas `pszSettingName` são chamados de valor, o valor original é substituído no arquivo de configurações.  
  
    -   O arquivo de configurações oferece suporte ao acesso de dados aleatórios, portanto, a ordem de leitura e gravação de operações não é importante.  No exemplo a seguir, a ordem das operações de gravador na implementação da <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> método é oposto das operações de leitura na <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> método.  
  
    -   Se a implementação pode mapear os dados em um dos quatro formatos com suporte, não há nenhuma restrição sobre como muito, ou que tipo de dados pode ser gravado.  
  
        > [!NOTE]
        >  A divisão de trabalho entre o <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> e <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> é um tanto arbitrários e depende da implementação de métodos.  Por exemplo, a implementação poderia ser reescrita usando uma implementação vazia a <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> método e fazendo com que todas as consultas de registro e o estado é executada na <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> método.  
  
4.  Registre as configurações de implementação da classe como fornecer suporte a um VSPackage.  
  
     Aplicar uma instância de <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> que é criada usando o <xref:System.Type> da classe que implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> para o VSPackage <xref:Microsoft.VisualStudio.Shell.Package> implementação.  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     Nesse caso, o atributo informa o IDE que o `MyPackageProfileManager` classe fornece uma implementação de configurações para o `MyPackage` classe.  O ponto de configurações personalizadas do registro é criado em HKLM\\Software\\Microsoft\\VisualStudio\\*versão*\\UserSettings\\ CoreUI\_MyPackage, onde  *versão* é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por exemplo, 10.0.  
  
     Para obter mais informações, consulte [Suporte para configurações de usuário](../extensibility/internals/support-for-user-settings.md) e <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Exemplo  
 O exemplo a seguir implementa <xref:Microsoft.VisualStudio.Shell.IProfileManager> em uma classe.  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First, check if data is obtained from the correct major version   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace   
  
Convert C# to VB.NET  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First, check if data is obtained from the correct major version   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## Consulte também  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [Importando configurações](/visual-cpp/misc/importing-settings)   
 [Suporte para configurações de usuário](../extensibility/internals/support-for-user-settings.md)