---
title: "Configura&#231;&#245;es padr&#227;o e personalizadas do Toolset | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, configurações personalizadas do toolset"
  - "MSBuild, msbuild.exe.config"
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 31
caps.handback.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configura&#231;&#245;es padr&#227;o e personalizadas do Toolset
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild Conjunto De Ferramentas contém referências às tarefas, a alvo, e ferramentas que você pode usar para criar um projeto de aplicativo.  MSBuild inclui Conjunto De Ferramentas padrão, mas você também pode criar conjuntos de ferramentas personalizadas.  Para obter informações sobre como especificar Conjunto De Ferramentas, consulte [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)  
  
## Configurações padrão de Conjunto De Ferramentas  
 MSBuild 12,0 inclui os seguintes conjuntos de ferramentas padrão:  
  
|ToolsVersion|Caminho de Conjunto De Ferramentas \(como especificado na propriedade compilação de MSBuildToolsPath ou de MSBuildBinPath\)|  
|------------------|---------------------------------------------------------------------------------------------------------------------------------|  
|2.0|*Windows installation path*\\Microsoft.Net\\Framework\\v2.0.50727\\|  
|3.5|*Windows installation path*\\ Microsoft.NET \\ Framework \\ v3.5 \\|  
|4.0|*Windows installation path*\\Microsoft.NET\\Framework\\v4.0.30319\\|  
|12.0|*%ProgramFiles%*\\MSBuild\\12.0\\bin|  
  
 O valor de `ToolsVersion` determina qual Conjunto De Ferramentas é usado por um projeto que o Visual Studio gerencia.  Em [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] o valor padrão é “12,0” \(não importa o que a versão especificada no arquivo de projeto\), mas você pode substituir esse atributo usando a opção de **\/toolsversion** em um prompt de comando.  Para obter informações sobre esse atributo e outras maneiras de especificar `ToolsVersion`, consulte [Substituindo as configurações de ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 Se `ToolsVersion` não for especificado, o número de versão de\<HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\da\>chave do Registro \\ DefaultToolsVersion define `ToolsVersion`, que é sempre 2,0.  
  
 As seguintes chaves do Registro especificam o caminho da instalação do MSBuild.exe.  
  
|Chave do Registro|Nome da chave|Valor de cadeia de caracteres|  
|-----------------------|-------------------|-----------------------------------|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\2.0\\|MSBuildToolsPath|caminho de instalação do.NET Framework 2.0|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\3.5\\|MSBuildToolsPath|caminho de instalação do.NET Framework 3.5|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\4.0\\|MSBuildToolsPath|caminho de instalação do.NET Framework 4|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\12.0\\|MSBuildToolsPath|Caminho de instalação do MSBuild|  
  
### Subpropriedades conjuntos de ferramentas  
 Se a chave de Registro na tabela anterior tem uma subchave, MSBuild usa\-o para determinar o caminho de subpropriedades Conjunto de Ferramentas pode substituir o caminho no kit de ferramentas pai.  A subchave seguir é um exemplo:  
  
 \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\12.0\\12.0  
  
 Se qualquer propriedade é definida no kit de ferramentas de base e em subpropriedades Conjunto de Ferramentas selecionado, as definições de propriedade em subpropriedades Conjunto de Ferramentas são usadas.  Por exemplo, o kit de ferramentas do MSBuild 4,0 define `SDK40ToolsPath` para apontar para o 7.0A SDK, mas o kit de ferramentas 4,0 \\ 11,0 do MSBuild define a mesma propriedade para apontar para o 8.0A SDK.  Se `VisualStudioVersion` remove, `SDK40ToolsPath` apontaria a 7.0A, mas se `VisualStudioVersion` é definido como 11,0, a propriedade apontaria em vez de 8.0A.  
  
 A propriedade de compilação de `VisualStudioVersion` indica se subpropriedades Conjunto de Ferramentas se tornou ativo.  Por exemplo, um valor de `VisualStudioVersion` de “12,0” especifica MSBuild subpropriedades Conjunto de Ferramentas 12,0.  Para obter mais informações, consulte a seção de subpropriedades conjuntos de ferramentas de [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Recomendamos que você evita alterar essas configurações.  Entretanto, você pode adicionar suas próprias configurações e configurar definições personalizadas da máquina do kit de ferramentas, porque a próxima seção descreve.  
  
## Definições personalizadas de Conjunto De Ferramentas  
 Quando Conjunto De Ferramentas padrão não atende aos requisitos de compilação, você pode criar Conjunto De Ferramentas personalizado.  Por exemplo, você pode ter um cenário de laboratório de compilação em que você deve ter um sistema separado para criar projetos de [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  Usando Conjunto De Ferramentas personalizado, você pode atribuir valores personalizados para o atributo de `ToolsVersion` quando você cria projetos ou MSBuild.exe executado.  Fazendo isto, você também pode usar a propriedade de `$(MSBuildToolsPath)` para importar arquivos .targets do diretório, bem como definir suas próprias propriedades personalizadas do kit de ferramentas que podem ser usadas para qualquer projeto que usar esse conjunto de ferramentas.  
  
 Especificar Conjunto De Ferramentas personalizado no arquivo de configuração para MSBuild.exe \(ou para a ferramenta personalizada que hospeda o mecanismo de MSBuild se esse é o que você está usando\).  Por exemplo, o arquivo de configuração para MSBuild.exe pode incluir a seguinte definição de Conjunto De Ferramentas se você queria substituir o comportamento padrão de ToolsVersion 12,0.  
  
```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 `<msbuildToolsets>` também deve ser definido no arquivo de configuração, como segue.  
  
```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Para ser lido corretamente, `<configSections>` deve ser a primeira seção na seção de `<configuration>` .  
  
 `ToolsetConfigurationSection` é uma seção de configuração personalizada que pode ser usada por qualquer host do MSBuild para a configuração personalizada.  Se você usar Conjunto De Ferramentas personalizado, um host não precisa fazer nada inicializar o mecanismo de compilação exceto fornece as entradas do arquivo de configuração.  Definindo entradas no Registro, você pode especificar os conjuntos de ferramentas de máquina que se aplicam a MSBuild.exe, a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], e todos os hosts de MSBuild.  
  
> [!NOTE]
>  Se um arquivo de configuração definir as configurações para `ToolsVersion` que já está definido no Registro, as duas definições não são mescladas.  A definição no arquivo de configuração terá precedência e as configurações do Registro para esse `ToolsVersion` são ignoradas.  
  
 As seguintes propriedades são específicas para o valor de `ToolsVersion` que é usado em projetos:  
  
-   **$ \(MSBuildBinPath\)** é definido como o valor de `ToolsPath` que é especificado no Registro ou no arquivo de configuração onde `ToolsVersion` é definido.  `$(MSBuildToolsPath)` que define o Registro ou no arquivo de configuração especifica o local de tarefas e destinos principal.  No arquivo de projeto, este mapeados para a propriedade $ \(MSBuildBinPath\), e também à propriedade $ \(MSBuildToolsPath\).  
  
-   `$(MSBuildToolsPath)` é uma propriedade reservado que é fornecida pela propriedade de MSBuildToolsPath que é especificado no arquivo de configuração. \(Essa propriedade substitui `$(MSBuildBinPath)`.  No entanto, `$(MSBuildBinPath)` é levado a frente para compatibilidade.\) Um conjunto de ferramentas personalizado deve definir `$(MSBuildToolsPath)` ou `$(MSBuildBinPath)` mas não ambos, a menos que ambos têm o mesmo valor.  
  
 Você também pode adicionar o personalizado, propriedades ToolsVersion\- específicas para o arquivo de configuração usando a mesma sintaxe que você usa para adicionar a propriedade de MSBuildToolsPath.  Para tornar essas propriedades personalizadas disponíveis para o arquivo de projeto, use o mesmo nome que o nome do valor que é especificado no arquivo de configuração.  Você pode definir conjuntos de ferramentas mas não subpropriedades conjuntos de ferramentas no arquivo de configuração.  
  
## Consulte também  
 [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)