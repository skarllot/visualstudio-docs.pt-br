---
title: "Elemento &lt;Commands&gt; (bootstrapper) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <Commands> [bootstrapper]"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;Commands&gt; (bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O `Commands` elemento implementa os testes descritos pelos elementos sob o `InstallChecks` elemento e declara os qual pacote o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bootstrapper deve instalar, se o teste falhar.  
  
## Sintaxe  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## Elementos e atributos  
 O `Commands` elemento é obrigatório.  O elemento tem o atributo a seguir.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Reboot`|Opcional.  Determina se o sistema deve ser reiniciado se qualquer um dos pacotes retornar um código de saída de reinicialização.  A lista a seguir mostra os valores válidos:<br /><br /> `Adiar`.  A reinicialização é adiada até algum momento futuro.<br /><br /> `Imediata`.  Faz com que uma reinicialização imediata se um dos pacotes retornado um código de saída de reinicialização.<br /><br /> `Nenhum`.  Faz com que todas as solicitações de reinício seja ignorado.<br /><br /> O padrão é  `imediata`.|  
  
## Comando  
 Um elemento `Command` é um filho do elemento `Commands`.  A `Commands` o elemento pode ter um ou mais `Command` elementos.  O elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`PackageFile`|Obrigatório.  O nome do pacote para instalar deve uma ou mais das condições especificadas por `InstallConditions` retornar false.  O pacote deve ser definido no mesmo arquivo usando um `PackageFile` elemento.|  
|`Arguments`|Opcional.  Um conjunto de argumentos de linha de comando para passar para o arquivo de pacote.|  
|`EstimatedInstallSeconds`|Opcional.  A estimativa de tempo, em segundos, ele levará para instalar o pacote.  Esse valor determina o tamanho da barra de progresso que o bootstrapper exibe para o usuário.  O padrão é 0, caso em que não há tempo a estimativa for especificada.|  
|`EstimatedDiskBytes`|Opcional.  A quantidade estimada de espaço em disco, em bytes, que o pacote ocupará após a instalação estará concluída.  Esse valor é usado em requisitos de espaço em disco rígido que o bootstrapper exibe para o usuário.  O padrão é 0, nesse caso o bootstrapper não exibe quaisquer requisitos de espaço em disco rígido.|  
|`EstimatedTempBytes`|Opcional.  A quantidade estimada de espaço temporário em disco, em bytes, que exigirá o pacote.|  
|`Log`|Opcional.  O caminho para o arquivo de log que o pacote gera, relativo ao diretório raiz do pacote.|  
  
## InstallConditions  
 O `InstallConditions` elemento é filho de `Command` elemento.  Cada `Command` o elemento pode ter no máximo uma `InstallConditions` elemento.  Se nenhum `InstallConditions` elemento existir, o pacote especificado por `Condition` serão sempre executados.  
  
## BypassIf  
 O `BypassIf` elemento é filho do `InstallConditions` elemento e descreve uma condição positiva sob a qual o comando não deve ser executado.  Cada `InstallConditions` o elemento pode ter zero ou mais `BypassIf` elementos.  
  
 `BypassIf`tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Property`|Obrigatório.  O nome da propriedade para testar.  A propriedade deve anteriormente foram definida por um filho do `InstallChecks` elemento.  Para obter mais informações, consulte [Elemento \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obrigatório.  O tipo de comparação a ser executada.  A lista a seguir mostra os valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obrigatório.  O valor para comparar com a propriedade.|  
|`Schedule`|Opcional.  O nome de um `Schedule` tag que define quando esta regra deve ser avaliada.|  
  
## FailIf  
 O `FailIf` elemento é filho da `InstallConditions` elemento e descreve uma condição positiva sob a qual a instalação deve parar.  Cada `InstallConditions` o elemento pode ter zero ou mais `FailIf` elementos.  
  
 `FailIf`tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Property`|Obrigatório.  O nome da propriedade para testar.  A propriedade deve anteriormente foram definida por um filho do `InstallChecks` elemento.  Para obter mais informações, consulte [Elemento \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obrigatório.  O tipo de comparação a ser executada.  A lista a seguir mostra os valores válidos:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obrigatório.  O valor para comparar com a propriedade.|  
|`String`|Opcional.  O texto será exibido para o usuário em caso de falha.|  
|`Schedule`|Opcional.  O nome de um `Schedule` tag que define quando esta regra deve ser avaliada.|  
  
## ExitCodes  
 O `ExitCodes` elemento é filho de `Command` elemento.  O `ExitCodes` elemento contém um ou mais `ExitCode` elementos, que determinam o que deve fazer a instalação em resposta a um código de saída de um pacote.  Pode haver um opcional `ExitCode` elemento sob um `Command` elemento.  `ExitCodes`tem sem atributos.  
  
## Código\_de\_saída  
 O `ExitCode` elemento é filho de `ExitCodes` elemento.  O `ExitCode` elemento determina o que deve fazer a instalação em resposta a um código de saída de um pacote.  `ExitCode`contém nenhum elemento filho e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Value`|Obrigatório.  O valor do código de saída ao qual o `ExitCode` elemento aplica.|  
|`Result`|Obrigatório.  Como a instalação deve reagir a este código de saída.  A lista a seguir mostra os valores válidos:<br /><br /> `Sucesso`.  Sinalizadores do pacote instalado como com êxito.<br /><br /> `SuccessReboot`.  Sinaliza o pacote instalado como com êxito e instrui o sistema seja reiniciado.<br /><br /> `Falha`.  O pacote de sinalizadores com falha.<br /><br /> `FailReboot`.  O pacote de sinalizadores com falha e instrui o sistema seja reiniciado.|  
|`String`|Opcional.  O valor seja exibido para o usuário em resposta a este código de saída.|  
|`FormatMessageFromSystem`|Opcional.  Determina se deve usar a mensagem de erro fornecidos pelo sistema correspondente ao código de saída ou usar o valor fornecido em `String`.  Os valores válidos são  `true`, que significa o erro fornecido pelo sistema, de usar e  `false`, que significa usar a seqüência de caracteres fornecida pelo `String`.  O padrão é `false`.  Se essa propriedade for  `false`, mas `String` não estiver definida, o erro fornecido pelo sistema será usado.|  
  
## Exemplo  
 O exemplo de código a seguir define os comandos para instalar o.NET Framework 2.0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## Consulte também  
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)   
 [Elemento \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md)