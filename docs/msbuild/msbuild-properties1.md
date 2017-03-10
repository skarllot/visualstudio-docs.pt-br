---
title: "Properties1 do MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, propriedades"
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Properties1 do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Propriedades são pares nome-valor que podem ser usados para configurar compilações. Propriedades são úteis para passar valores para tarefas de avaliação das condições e armazenar os valores que serão referenciados em todo o arquivo de projeto.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>Definindo e referenciando propriedades em um arquivo de projeto  
 Propriedades são declaradas com a criação de um elemento que tem o nome da propriedade como um filho de um [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elemento. Por exemplo, o XML a seguir cria uma propriedade chamada `BuildDir` que tem um valor de `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Em todo o arquivo de projeto, as propriedades são referenciadas usando a sintaxe $(`PropertyName`). Por exemplo, a propriedade no exemplo anterior é referenciada usando $(BuildDir).  
  
 Valores de propriedade podem ser alterados, redefinindo a propriedade. O `BuildDir` propriedade pode receber um novo valor usando este XML:  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 As propriedades são avaliadas na ordem em que aparecem no arquivo de projeto. O novo valor de `BuildDir` deve ser declarado depois que é atribuído o valor antigo.  
  
## <a name="reserved-properties"></a>Propriedades Reservadas  
 MSBuild reserva alguns nomes de propriedades para armazenar informações sobre o arquivo de projeto e os binários do MSBuild. Essas propriedades são referenciadas usando a notação de $, assim como qualquer outra propriedade. Por exemplo, $(MSBuildProjectFile) retorna o nome de arquivo completo do arquivo de projeto, incluindo a extensão de nome de arquivo.  
  
 Para obter mais informações, consulte [como: referenciar o nome ou local do arquivo de projeto](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md) e [MSBuild reservadas e conhecidas propriedades](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Propriedades de ambiente  
 Você pode referenciar variáveis de ambiente em arquivos de projeto como referência propriedades reservadas. Por exemplo, para usar o `PATH` variável de ambiente em seu arquivo de projeto, use $(caminho). Se o projeto contém uma definição de propriedade que tem o mesmo nome que uma propriedade de ambiente, a propriedade do projeto substitui o valor da variável de ambiente.  
  
 Cada projeto do MSBuild tem um bloco de ambiente isolado: apenas observa leituras e gravações em seu próprio bloco.  MSBuild somente lê as variáveis de ambiente quando ele inicializa a coleção de propriedades antes do arquivo de projeto é avaliado ou criado. Depois disso, propriedades de ambiente são estáticas, ou seja, cada ferramenta gerada começa com os mesmos nomes e valores.  
  
 Para obter o valor atual de variáveis de ambiente de uma ferramenta gerada, use o [funções de propriedade](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. O método preferido, no entanto, é usar o parâmetro de tarefa <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Propriedades de ambiente definidas nesta matriz de cadeia de caracteres podem ser passadas para a ferramenta gerada sem afetar as variáveis de ambiente do sistema.  
  
> [!TIP]
>  Nem todas as variáveis de ambiente são lidas em se torne propriedades iniciais. Qualquer variável de ambiente cujo nome é não uma válido MSBuild nomes de propriedade, como "386" será ignorado.  
  
 Para obter mais informações, consulte [como: Use variáveis de ambiente em uma compilação](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md).  
  
## <a name="registry-properties"></a>Propriedades de registro  
 Você pode ler valores do registro de sistema usando a seguinte sintaxe, onde `Hive` é o hive do registro (por exemplo, HKEY_LOCAL_MACHINE), `Key` é o nome da chave, `SubKey` é o nome da subchave, e `Value` é o valor da subchave.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Para obter o valor da subchave padrão, omita o `Value`.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Esse valor do registro pode ser usado para inicializar uma propriedade de compilação. Por exemplo, para criar uma propriedade de compilação que representa a home page do navegador do Visual Studio web, use este código:  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Propriedades globais  
 MSBuild permite que você defina propriedades na linha de comando usando o **/property** (ou **/p**) alternar. Esses valores de propriedade global substituem os valores de propriedade são definidos no arquivo de projeto. Isso inclui propriedades de ambiente, mas não inclui propriedades reservadas, que não podem ser alteradas.  
  
 O exemplo a seguir define global `Configuration` propriedade `DEBUG`.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 Propriedades globais também podem ser definidas ou modificadas para projetos filho em uma compilação de vários projeto usando o `Properties` atributo da tarefa MSBuild. Para obter mais informações, consulte [tarefa MSBuild](../msbuild/msbuild-task.md).  
  
 Se você especificar uma propriedade usando o `TreatAsLocalProperty` atributo em uma marca de projeto, que o valor da propriedade global não substitui o valor da propriedade que é definido no arquivo de projeto. Para obter mais informações, consulte [elemento Project (MSBuild)](../msbuild/project-element-msbuild.md) e [como: compilar os mesmos arquivos de origem com opções diferentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Funções de propriedade  
 A partir do .NET Framework versão 4, você pode usar funções de propriedade para avaliar seus scripts MSBuild. Você pode ler a hora do sistema, comparar cadeias de caracteres, combinar expressões regulares e executar muitas outras ações em seu script de compilação sem usar tarefas do MSBuild.  
  
 Você pode usar métodos de cadeia de caracteres (instância) para operar em qualquer valor de propriedade, e você pode chamar os métodos estáticos de muitas classes de sistema. Por exemplo, você pode definir uma propriedade de compilação a data de hoje da seguinte maneira.  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Para obter mais informações e uma lista de funções de propriedade, consulte [funções de propriedade](../msbuild/property-functions.md).  
  
## <a name="creating-properties-during-execution"></a>Criando propriedades durante a execução  
 Propriedades posicionados fora `Target` elementos são atribuídos valores durante a fase de avaliação de uma compilação. Durante a fase de execução subsequentes, propriedades podem ser criadas ou modificadas da seguinte maneira:  
  
-   Uma propriedade pode ser emitida por uma tarefa. A emissão de uma propriedade, o [tarefa](../msbuild/task-element-msbuild.md) elemento deve ter um filho [saída](../msbuild/output-element-msbuild.md) elemento que possui um `PropertyName` atributo.  
  
-   Uma propriedade pode ser emitida pelo [CreateProperty](../msbuild/createproperty-task.md) tarefa. Esse uso é preterido.  
  
-   A partir do .NET Framework 3.5, `Target` podem conter elementos `PropertyGroup` elementos que podem conter declarações de propriedade.  
  
## <a name="storing-xml-in-properties"></a>Armazenamento de XML em Propriedades  
 Propriedades podem conter XML arbitrário, que pode ajudar a passar valores para tarefas ou exibir informações de log. A exemplo a seguir mostra o `ConfigTemplate` propriedade, que tem um valor que contém o XML e outras propriedades referências. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] substitui as referências de propriedade usando valores de suas respectivas propriedades. Valores de propriedade são atribuídos na ordem em que aparecem. Portanto, no exemplo, `$(MySupportedVersion)`, `$(MyRequiredVersion)`, e `$(MySafeMode)` deve já foram definidos.  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)  
 [Como: usar variáveis de ambiente em uma compilação](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)   
 [Como: referenciar o nome ou local do arquivo de projeto](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md)   
 [Como: compilar os mesmos arquivos de origem com opções diferentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild propriedades reservadas e conhecidas](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)