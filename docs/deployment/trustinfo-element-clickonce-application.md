---
title: "&lt; TrustInfo &gt; elemento (aplicativo ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#IPermission"
  - "urn:schemas-microsoft-com:asm.v2#PermissionSet"
  - "urn:schemas-microsoft-com:asm.v2#assemblyRequest"
  - "urn:schemas-microsoft-com:asm.v2#trustInfo"
  - "urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest"
  - "urn:schemas-microsoft-com:asm.v2#security"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "manifestos ClickOnce, elemento trustInfo"
  - "elemento < trustInfo > [manifesto de aplicativo ClickOnce]"
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; TrustInfo &gt; elemento (aplicativo ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Descreve as permissões de segurança mínimas necessárias para o aplicativo seja executado no computador cliente.  
  
## Sintaxe  
  
```  
  
<trustInfo>  
   <security>  
      <applicationRequestMinimum>  
         <PermissionSet  
            ID  
            Unrestricted>  
            <IPermission  
               class  
               version  
               Unrestricted  
            />  
         </PermissionSet>  
         <defaultAssemblyRequest  
            permissionSetReference  
         />  
         <assemblyRequest  
            name  
            permissionSetReference  
         />  
      </applicationRequestMinimum>  
      <requestedPrivileges>  
         <requestedExecutionLevel  
            level  
            uiAccess  
         />  
      </requestedPrivileges>  
   </security>  
</trustInfo>  
  
```  
  
## Elementos e atributos  
 O `trustInfo` elemento é necessário e está no `asm.v2` namespace. Ele não tem atributos e contém os seguintes elementos.  
  
## segurança  
 Obrigatório. Esse elemento é um filho de `trustInfo` elemento. Ele contém o `applicationRequestMinimum` elemento e não tem nenhum atributo.  
  
## applicationRequestMinimum  
 Obrigatório. Esse elemento é um filho de `security` elemento e contém o `PermissionSet`, `assemblyRequest`, e `defaultAssemblyRequest`elementos. Esse elemento não tem atributos.  
  
## PermissionSet  
 Obrigatório. Esse elemento é um filho de `applicationRequestMinimum` elemento e contém o `IPermission` elemento. Este elemento tem os seguintes atributos.  
  
-   `ID`  
  
     Obrigatório. Identifica o conjunto de permissões. Esse atributo pode ser qualquer valor. A ID é referenciada na `defaultAssemblyRequest` e `assemblyRequest` atributos.  
  
-   `version`  
  
     Obrigatório. Identifica a versão da permissão. Normalmente, esse valor é `1`.  
  
## IPermission  
 Opcional. Esse elemento é um filho de `PermissionSet` elemento. O `IPermission` elemento totalmente identifica uma classe de permissão no [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. O `IPermission` elemento tem os seguintes atributos, mas pode ter atributos adicionais que correspondem às propriedades da classe de permissão. Para obter a sintaxe para uma permissão específica, consulte os exemplos listados no arquivo config.  
  
-   `class`  
  
     Obrigatório. Identifica a classe de permissão por nome forte. Por exemplo, o código a seguir identifica as `FileDialogPermission` tipo.  
  
     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
-   `version`  
  
     Obrigatório. Identifica a versão da permissão. Normalmente esse valor é `1`.  
  
-   `Unrestricted`  
  
     Obrigatório. Identifica se o aplicativo precisa de uma concessão irrestrita dessa permissão. Se `true`, a concessão de permissão é incondicional. Se `false`, ou se esse atributo for indefinido, ele é restrito de acordo com os atributos de permissão específica definidos no `IPermission` marca. Execute as seguintes permissões:  
  
    ```  
    <IPermission  
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Read="USERNAME" />  
    <IPermission  
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Unrestricted="true" />  
    ```  
  
     Neste exemplo, a declaração <xref:System.Security.Permissions.EnvironmentPermission> restringe o aplicativo para ler somente a variável de ambiente USERNAME, enquanto que a declaração <xref:System.Security.Permissions.FileDialogPermission> permite o uso do aplicativo irrestrito de todos os <xref:System.Windows.Forms.FileDialog> classes.  
  
## defaultAssemblyRequest  
 Opcional. Identifica o conjunto de permissões concedidas a todos os assemblies. Esse elemento é um filho de `applicationRequestMinimum` elemento e tem o seguinte atributo.  
  
-   `permissionSetReference`  
  
     Obrigatório. Identifica a ID do conjunto de permissões que é a permissão padrão. O conjunto de permissões é declarado na `PermissionSet` elemento.  
  
## assemblyRequest  
 Opcional. Identifica as permissões para um assembly específico. Esse elemento é um filho de `applicationRequestMinimum` elemento e tem os seguintes atributos.  
  
-   `Name`  
  
     Obrigatório. Identifica o nome do assembly.  
  
-   `permissionSetReference`  
  
     Obrigatório. Identifica a ID do conjunto de permissões que requer esse assembly. O conjunto de permissões é declarado na `PermissionSet` elemento.  
  
## requestedPrivileges  
 Opcional. Esse elemento é um filho de `security` elemento e contém o `requestedExecutionLevel` elemento. Esse elemento não tem atributos.  
  
## requestedExecutionLevel  
 Opcional. Identifica o nível de segurança no qual o aplicativo solicita a ser executado. Esse elemento não tem filhos e tem os seguintes atributos.  
  
-   `Level`  
  
     Obrigatório. Indica que o nível de segurança do aplicativo está solicitando. Os valores possíveis são:  
  
     `asInvoker`, não solicitando nenhuma permissão adicional. Este nível exige que não solicita que nenhuma relação de confiança adicional.  
  
     `highestAvailable`, solicitando as permissões mais altas disponíveis para o processo pai.  
  
     `requireAdministrator`, solicitando permissões de administrador completo.  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalará apenas com um valor de `asInvoker`. Haverá falha na instalação com qualquer outro valor.  
  
-   `uiAccess`  
  
     Opcional. Indica se o aplicativo requer acesso aos elementos de interface do usuário protegido. Valores são `true` ou `false`, e o padrão é false. Somente os aplicativos assinados devem ter um valor de true.  
  
## Comentários  
 Se um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo solicita mais permissões do que o computador cliente concederá por padrão, a linguagem comum de Gerenciador tempo de execução de confiança solicitará ao usuário se ele deseja conceder ao aplicativo nesse alto nível de confiança. Se ela diz não, o aplicativo não será executado; Caso contrário, ele será executado com as permissões solicitadas.  
  
 Todas as permissões solicitadas usando `defaultAssemblyRequest` e `assemblyRequest` será concedido sem nenhum aviso ao usuário se o manifesto de implantação tiver uma licença válida de confiança.  
  
 Para obter mais informações sobre a elevação de permissões, consulte [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md). Para obter mais informações sobre a implantação de política, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
## Exemplos  
 O código de três exemplos a seguir ilustra `trustInfo` elementos para o padrão chamado zonas de segurança — Internet LocalIntranet e FullTrust — para uso em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto do aplicativo da implantação.  
  
 O primeiro exemplo ilustra o `trustInfo` elemento para as permissões padrão disponíveis na zona de segurança da Internet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="Internet">  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Access="Open" />  
          <IPermission  
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"  
            Allowed="DomainIsolationByUser"  
            UserQuota="10240" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Flags="Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Window="SafeTopLevelWindows"  
            Clipboard="OwnClipboard" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"   
            Level="SafePrinting" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="Internet" />  
      </applicationRequestMinimum>  
    </security>  
  </trustInfo>  
```  
  
 O segundo exemplo ilustra o `trustInfo` elemento para as permissões padrão disponíveis na zona de segurança LocalIntranet.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="LocalIntranet">  
          <IPermission  
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Read="USERNAME" />  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Allowed="AssemblyIsolationByUser"  
            UserQuota="9223372036854775807"  
            Expiry="9223372036854775807"  
            Permanent="True" />  
          <IPermission  
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="ReflectionEmit" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="Assertion, Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"  
            Level="DefaultPrinting" />  
          <IPermission  
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />  
      </applicationRequestMinimum>  
    </security>  
</trustInfo>  
```  
  
 O terceiro exemplo ilustra o `trustInfo` elemento para as permissões padrão disponíveis na zona de segurança FullTrust.  
  
```  
<trustInfo>  
  <security>  
    <applicationRequestMinimum>  
      <PermissionSet ID="FullTrust" Unrestricted="true" />  
      <defaultAssemblyRequest permissionSetReference="FullTrust" />  
    </applicationRequestMinimum>  
  </security>  
</trustInfo>  
```  
  
## Consulte também  
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)