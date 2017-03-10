---
title: "Elemento &lt;InstallChecks&gt; (bootstrapper) | Microsoft Docs"
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
  - "Elemento <InstallChecks> [bootstrapper]"
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;InstallChecks&gt; (bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O `InstallChecks` elemento oferece suporte ao início de uma variedade de testes para o computador local para certificar\-se de que todos os pré\-requisitos adequados para um aplicativo tenham sido instalados.  
  
## Sintaxe  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## AssemblyCheck  
 Este é um elemento filho opcional de `InstallChecks`.  Para cada instância de `AssemblyCheck`, o bootstrapper irá se certificar que o assembly identificado pelo elemento existe no cache global de assemblies \(GAC\).  Ele não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Property`|Obrigatório.  O nome da propriedade para armazenar o resultado.  Esta propriedade pode ser referenciada a partir de um teste sob o `InstallConditions` elemento, que é um filho da `Command` elemento.  Para obter mais informações, consulte [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Obrigatório.  O nome totalmente qualificado do assembly para verificar.|  
|`PublicKeyToken`|Obrigatório.  A forma abreviada da chave pública associado a isso tem um nome de assembly.  Todos os módulos \(assemblies\) armazenados no GAC deve ter um nome, uma versão e uma chave pública.|  
|`Version`|Obrigatório.  A versão do assembly.<br /><br /> O número de versão tem o formato \<*versão principal*\>. \<*versão secundária*\>. \<*Criar versão*\>. \<*versão revisão*\>.|  
|`Language`|Opcional.  O idioma de um assembly localizado.  O padrão é  `neutra`.|  
|`ProcessorArchitecture`|Opcional.  O processador do computador alvo por esta instalação.  O padrão é  `msil`.|  
  
## ExternalCheck  
 Este é um elemento filho opcional de `InstallChecks`.  Para cada instância de `ExternalCheck`, o bootstrapper irá executar o programa externo nomeado em um processo separado e armazenar seu código de saída na propriedade indicada por `Property`.  `ExternalCheck`é útil para implementar as verificações de dependência complexos ou quando a única maneira de verificar a existência de um componente é para instanciá\-la.  
  
 `ExternalCheck`não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Property`|Obrigatório.  O nome da propriedade para armazenar o resultado.  Esta propriedade pode ser referenciada a partir de um teste sob o `InstallConditions` elemento, que é um filho da `Command` elemento.  Para obter mais informações, consulte [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Obrigatório.  O programa externo para executar.  O programa deve ser parte do pacote de distribuição do programa de instalação.|  
|`Arguments`|Opcional.  Fornece os argumentos de linha de comando para o executável nomeado por `PackageFile`.|  
  
## FileCheck  
 Este é um elemento filho opcional de `InstallChecks`.  Para cada instância de `FileCheck`, o bootstrapper determinará se o arquivo nomeado existe e retornar o número de versão do arquivo.  Se o arquivo não tiver um número de versão, o bootstrapper define a propriedade nomeada por `Property` como 0.  Se o arquivo não existir, `Property` não estiver definida como qualquer valor.  
  
 `FileCheck`não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Property`|Obrigatório.  O nome da propriedade para armazenar o resultado.  Esta propriedade pode ser referenciada a partir de um teste sob o `InstallConditions` elemento, que é um filho da `Command` elemento.  Para obter mais informações, consulte [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Obrigatório.  O nome do arquivo para localizar.|  
|`SearchPath`|Obrigatório.  O disco ou pasta na qual deseja procurar o arquivo.  Deve ser um caminho relativo se `SpecialFolder` é atribuído; Caso contrário, ele deve ser um caminho absoluto.|  
|`SpecialFolder`|Opcional.  Uma pasta que tem significado especial para o Windows ou para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  O padrão é interpretar `SearchPath` como um caminho absoluto.  Os valores válidos incluem o seguinte:<br /><br /> `AppDataFolder`.  A pasta de dados do aplicativo para este [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo; específico para o usuário atual.<br /><br /> `CommonAppDataFolder`.  A pasta de dados do aplicativo usada por todos os usuários.<br /><br /> `CommonFilesFolder`.  A pasta de arquivos comuns para o usuário atual.<br /><br /> `LocalDataAppFolder`.  A pasta de dados para aplicativos não\-móveis.<br /><br /> `ProgramFilesFolder`.  A pasta de arquivos de programa padrão para aplicativos de 32 bits.<br /><br /> `StartUpFolder`.  A pasta que contém todos os aplicativos iniciados na inicialização do sistema.<br /><br /> `SystemFolder`.  A pasta que contém as DLLs do sistema de 32 bits.<br /><br /> `WindowsFolder`.  A pasta que contém a instalação de sistema do Windows.<br /><br /> `WindowsVolume`.  A unidade ou partição que contém a instalação de sistema do Windows.|  
|`SearchDepth`|Opcional.  A profundidade na qual se deseja pesquisar subpastas para o arquivo nomeado.  A pesquisa está começando.  O padrão é 0, o que restringe a pesquisa para a pasta de nível superior especificada por `SpecialFolder` e  **SearchPath**.|  
  
## MsiProductCheck  
 Este é um elemento filho opcional de `InstallChecks`.  Para cada instância de `MsiProductCheck`, o bootstrapper verifica se a instalação de Microsoft Windows Installer especificado foi executado até que ela seja concluída.  O valor da propriedade é definido, dependendo do estado do produto instalado.  Um valor positivo indica que o produto está instalado, 0 ou \-1 indica que ele não está instalado.  \(Consulte a função do SDK do Windows Installer MsiQueryFeatureState para obter mais informações\). .  Se o Windows Installer não está instalado no computador, `Property` não está definido.  
  
 `MsiProductCheck`não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Property`|Obrigatório.  O nome da propriedade para armazenar o resultado.  Esta propriedade pode ser referenciada a partir de um teste sob o `InstallConditions` elemento, que é um filho da `Command` elemento.  Para obter mais informações, consulte [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Obrigatório.  O GUID do produto instalado.|  
|`Feature`|Opcional.  O GUID para um recurso específico do aplicativo instalado.|  
  
## RegistryCheck  
 Este é um elemento filho opcional de `InstallChecks`.  Para cada instância de `RegistryCheck`, o bootstrapper verifica se a chave do Registro especificada existe ou se ele tem o valor indicado.  
  
 `RegistryCheck`não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Property`|Obrigatório.  O nome da propriedade para armazenar o resultado.  Esta propriedade pode ser referenciada a partir de um teste sob o `InstallConditions` elemento, que é um filho da `Command` elemento.  Para obter mais informações, consulte [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obrigatório.  O nome da chave do registro.|  
|`Value`|Opcional.  O nome do valor do registro para recuperar.  O padrão é para retornar o texto do valor padrão.  `Value`deve ser uma seqüência de caracteres ou uma DWORD.|  
  
## RegistryFileCheck  
 Este é um elemento filho opcional de `InstallChecks`.  Para cada instância de `RegistryFileCheck`, o bootstrapper recupera a versão do arquivo especificado, a primeira tentativa de recuperar o caminho para o arquivo da chave do Registro especificada.  Isso é particularmente útil se você quiser pesquisar um arquivo em um diretório especificado como um valor no registro.  
  
 `RegistryFileCheck`não contém elementos e tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Property`|Obrigatório.  O nome da propriedade para armazenar o resultado.  Esta propriedade pode ser referenciada a partir de um teste sob o `InstallConditions` elemento, que é um filho da `Command` elemento.  Para obter mais informações, consulte [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obrigatório.  O nome da chave do registro.  Seu valor é interpretado como o caminho para um arquivo, a menos que o `File` atributo está definido.  Se esta chave não existir, `Property` não está definido.|  
|`Value`|Opcional.  O nome do valor do registro para recuperar.  O padrão é para retornar o texto do valor padrão.  `Value`deve ser uma seqüência de caracteres.|  
|`FileName`|Opcional.  O nome de um arquivo.  Se especificado, o valor obtido da chave do registro é considerado um caminho de diretório, e esse nome é acrescentado a ele.  Se não especificado, o valor retornado do registro é considerado o caminho completo para um arquivo.|  
|`SearchDepth`|Opcional.  A profundidade na qual se deseja pesquisar subpastas para o arquivo nomeado.  A pesquisa está começando.  O padrão é 0, o que restringe a pesquisa para a pasta de nível superior especificada pelo valor da chave do registro.|  
  
## Comentários  
 Enquanto os elementos sob `InstallChecks` definir os testes a serem executados, eles não executá\-los.  Para executar os testes, você deve criar `Command` elementos sob o `Commands` elemento.  
  
## Exemplo  
 O exemplo de código a seguir demonstra o `InstallChecks` elemento como ele é usado no arquivo do produto para o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## InstallConditions  
 Quando `InstallChecks` são avaliadas, eles produzem propriedades.  As propriedades são usadas por `InstallConditions` para determinar se um pacote deve instalar, ignorar ou falhar.  A tabela a seguir lista os `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Se houver `FailIf` condição for avaliada como true, o pacote falhará.  O restante das condições não será avaliado.|  
|`BypassIf`|Se houver `BypassIf` condição for avaliada como true, o pacote será ignorado.  O restante das condições não será avaliado.|  
  
## Propriedades predefinidas  
 A tabela a seguir lista os `BypassIf` e `FailIf` elementos:  
  
|Propriedade|Anotações|Valores possíveis|  
|-----------------|---------------|-----------------------|  
|`Version9X`|Número de versão do sistema operacional Windows 9 X.|4.10 \= Windows 98|  
|`VersionNT`|Número de versão do sistema operacional baseado em Windows NT.|Major.Minor.ServicePack<br /><br /> 5.0 \= O Windows 2000<br /><br /> 5.1.0 \= O Windows XP<br /><br /> 5.1.2 \= O Windows XP Professional SP2<br /><br /> 5.2.0 \= O Windows Server 2003|  
|`VersionNT64`|Número de versão de um sistema de operacional de 64 bits com base em Windows NT.|O mesmo como mencionado anteriormente.|  
|`VersionMsi`|Número de versão do serviço Windows Installer.|2.0 \= Windows Installer 2.0|  
|`AdminUser`|Especifica se um usuário tem privilégios de administrador em um sistema operacional Windows NT.|0 \= sem privilégios de administrador<br /><br /> 1 \= privilégios de administrador|  
  
 Por exemplo, para bloquear a instalação em um computador executando o Windows 95, use o código como o seguinte:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## Consulte também  
 [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)