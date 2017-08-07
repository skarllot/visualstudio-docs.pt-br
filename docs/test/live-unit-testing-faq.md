---
title: Perguntas frequentes sobre o Live Unit Testing | Microsoft Docs
ms.date: 2017-03-13
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
ms.assetid: 61baf3bb-646f-4c5a-b7c0-a6bdff68f21c
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 2a58b84403189d824494af85bc732a1b8cf3d0b6
ms.contentlocale: pt-br
ms.lasthandoff: 07/11/2017

---
# <a name="live-unit-testing-frequently-asked-questions"></a>Perguntas frequentes sobre o Live Unit Testing

## <a name="does-live-unit-testing-work-with-net-core"></a>O Live Unit Testing funciona com o .NET Core?  

**Resposta:**

Sim. O Live Unit Testing funciona com o .NET Core e .NET Frameworks. O suporte ao .NET Core foi adicionado recentemente ao Visual Studio 2017 versão 15.3 Versão Prévia. 

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>Por que o Live Unit Testing não funciona ao ser ligado? 

**Resposta:** 

A **Janela de Saída** (quando o menu suspenso Live Unit Testing está selecionado) deve informar por que o Live Unit Testing não funciona. O Live Unit Testing poderá não funcionar por um dos seguintes motivos: 

- Se os pacotes NuGet referenciados pelos projetos na solução não tiverem sido restaurados, o Live Unit Testing não funcionará. Fazer um build explícito da solução ou restaurar os pacotes NuGet na solução antes de ativar o Live Unit Testing deverá resolver esse problema. 

- Se estiver usando testes baseados no MSTest nos projetos, lembre-se de remover a referência a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` e adicionar referências aos últimos pacotes NuGet do MSTest: `MSTest.TestAdapter` (uma versão mínima de 1.1.11 é necessária) e `MSTest.TestFramework` (uma versão mínima de 1.1.11 é necessária). Para obter mais informações, consulte a seção “Estruturas de teste com suporte” do tópico [Usar o Live Unit Testing no Visual Studio 2017 Enterprise Edition](live-unit-testing.md#supported-test-frameworks).
 
- No mínimo, um projeto na solução deve ter uma referência ao NuGet ou uma referência direta à estrutura de teste do xUnit, NUnit ou MSTest. Esse projeto também deve referenciar um pacote NuGet de adaptadores de teste do Visual Studio correspondente. O adaptador de teste do Visual Studio também pode ser referenciado por meio de um arquivo `.runsettings`. O arquivo `.runsettings` deve ter uma entrada como a mostrada abaixo: 

   ```xml
    <RunSettings> 
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration> 
    </RunSettings> 
   ``` 

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>Por que o Live Unit Testing mostra uma cobertura incorreta depois de atualizar o adaptador de teste referenciado nos Projetos do Visual Studio para a versão com suporte?

**Resposta:**

- Se vários projetos na solução referenciarem o pacote do adaptador de teste NuGet, cada um deles deverá ser atualizado para a versão com suporte.

- Verifique se o arquivo MSBuild.props importado do pacote do adaptador de teste é atualizado corretamente também. Verifique a versão e o caminho da importação do pacote NuGet, que geralmente podem ser encontrados próximo à parte superior do arquivo de projeto, da seguinte forma:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>Posso personalizar meus builds do Live Unit Testing? 

**Resposta:**

Se a solução exigir etapas personalizadas para compilar para instrumentação (Live Unit Testing) que não serão necessárias para o build não instrumentado “normal”, será possível adicionar código ao projeto ou arquivos .targets que verificam a propriedade `BuildingForLiveUnitTesting` e executam etapas de pré/pós-build personalizadas. Também é possível optar por remover algumas etapas de build (como publicar ou gerar pacotes) ou adicionar etapas de build (como copiar pré-requisitos) a um build do Live Unit Testing baseado na propriedade desse projeto. Isso não alterará o build normal de nenhuma forma e afetará apenas os builds do Live Unit Testing. 

Por exemplo, pode haver um destino que produz pacotes NuGet durante um build normal. Provavelmente, você não desejará que os pacotes NuGet sejam gerados após cada edição feita. Portanto, é possível desabilitar esse destino no build do Live Unit Testing fazendo algo semelhante ao seguinte:   

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'"> 
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/> 
</Target> 
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Mensagens de erro com &lt;OutputPath&gt; ou &lt;OutDir&gt;

**Por que recebo este erro quando o Live Unit Testing tenta criar minha solução: “... parece definir `<OutputPath>` ou `<OutDir>` incondicionalmente. O Live Unit Testing não executará testes do assembly de saída”?**

**Resposta:**

Isso pode ocorrer se o processo de build da solução substitui `<OutputPath>` ou `<OutDir>` incondicionalmente, para que ele não seja um subdiretório de `<BaseOutputPath>`. Nesses casos, o Live Unit Testing não funcionará, pois ele também os substitui, a fim de garantir que os artefatos de build são soltos em uma pasta em `<BaseOutputPath>`. Se precisar substituir a localização em que você deseja que os artefatos de build sejam soltos em um build normal, substitua o `<OutputPath>` condicionalmente com base em `<BaseOutputPath>`. 

Por exemplo, se o build substituir o `<OutputPath>`, conforme mostrado abaixo: 

```xml 
<Project> 
  <PropertyGroup> 
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath> 
  </PropertyGroup> 
</Project> 
```

é possível substituí-lo pelo seguinte: 

```xml 
<Project> 
  <PropertyGroup> 
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath> 
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath> 
  </PropertyGroup> 
</Project> 
```
 
Isso garante que `<OutputPath>` reside na pasta `<BaseOutputPath>`. 
 
Não substitua `<OutDir>` diretamente no processo de build; em vez disso, substitua `<OutputPath>` para soltar os artefatos de build em uma localização específica.
  
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>Configurando a localização dos artefatos de build do Live Unit Testing

**Quero que os artefatos de um build do Live Unit Testing sejam encaminhados para uma localização específica em vez da localização padrão na pasta `.vs`. Como fazer para alterar isso?**
 
**Resposta:**

Defina a variável de ambiente em nível de usuário `LiveUnitTesting_BuildRoot` com o caminho no qual você deseja que os artefatos de build do Live Unit Testing sejam soltos.  

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>Qual a diferença entre a execução de testes na janela Gerenciador de Testes e a execução de testes no Live Unit Testing? 

**Resposta:**

Há várias diferenças: 

- A execução ou depuração de testes na janela Gerenciador de Testes executa binários regulares, ao passo que o Live Unit Testing executa binários instrumentados. Se você desejar depurar binários instrumentados, a adição de uma chamada de método [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) ao método de teste faz com que o depurador seja iniciado sempre que o método é executado (incluindo quando ele é executado pelo Live Unit Testing). Em seguida, é possível anexar e depurar o binário instrumentado. No entanto, esperamos que a instrumentação seja transparente para você na maioria dos cenários de usuário e que você não precise depurar binários instrumentados. 

- O Live Unit Testing não cria um novo domínio de aplicativo para executar testes, mas os testes executados na janela Gerenciador de Testes criam um novo domínio de aplicativo. 

- O Live Unit Testing executa testes em cada assembly de teste sequencialmente, ao passo que se você executar vários testes na janela Gerenciador de Testes e tiver selecionado o botão **Executar Testes em Paralelo**, eles serão executados em paralelo. 

- A descoberta e a execução de testes no Live Unit Testing usam a versão 2 do `TestPlatform`, enquanto a janela Gerenciador de Testes usa a versão 1. No entanto, você não deverá observar nenhuma diferença na maioria dos casos.  

- Atualmente, o Gerenciador de Testes executa testes em um STA (Single-Threaded Apartment) por padrão, enquanto o Live Unit Testing executa testes em um MTA (Multi-Threaded Apartment). Para executar testes do MSTest no STA no Live Unit Testing, decore o método de teste ou a classe recipiente com o atributo `<STATestMethod>` ou `<STATestClass>` que pode ser encontrado no pacote NuGet `MSTest.STAExtensions 1.0.3-beta`. Para o NUnit, decore o método de teste com o atributo `<RequiresThread(ApartmentState.STA)>` e para o xUnit, com o atributo `<STAFact>`.
 
## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>Como fazer para excluir testes de fazer parte do Live Unit Testing?

**Resposta:**

Consulte a seção “Incluindo e excluindo projetos e métodos de teste” do tópico [Usar o Live Unit Testing no Visual Studio 2017 Enterprise Edition](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods) para obter a configuração específica ao usuário. Isso é extremamente útil quando você deseja executar um conjunto específico de testes em uma sessão de edição específica ou para persistir suas próprias preferências pessoais.
  
Para configurações específicas da solução, você pode aplicar o atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> programaticamente para excluir métodos, propriedades, classes ou estruturas de serem instrumentados pelo by Live Unit Testing. Além disso, também é possível definir a propriedade `<ExcludeFromCodeCoverage>` como `true` no arquivo de projeto para excluir todo o projeto de ser instrumentado. O Live Unit Testing ainda executará os testes que não foram instrumentados, mas sua cobertura não será visualizada.

Também é possível verificar se `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` foi carregado no domínio de aplicativo atual e desabilitar testes com base nele. Por exemplo, você pode fazer algo semelhante ao seguinte com o xUnit:

```cs
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name == 
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>Por que os cabeçalhos do Win32 PE são diferentes em assemblies instrumentados compilados pelo Live Unit Testing? 

**Resposta:**

Há um bug conhecido que pode resultar na falha dos builds do Live Unit Testing em inserir os seguintes dados de Cabeçalho do Win32 PE: 

- Versão de Arquivo (especificada por @System.Reflection.AssemblyFileVersionAttribute no código). 

- Ícone do Win32 (especificado por `/win32icon:` na linha de comando). 

- Manifesto do Win32 (especificado por `/win32manifest:` na linha de comando). 

Os testes que dependem desses valores poderão falhar quando executados pelo Live Unit Testing.

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>Por que o Live Unit Testing continua compilando minha solução em todos os momentos, mesmo quando não estou fazendo nenhuma edição? 

**Resposta:**

Isso pode ocorrer se o processo de build da solução gera um código-fonte que faz parte da própria solução e os arquivos de destino do build não têm entradas e saídas apropriadas especificadas. Os destinos devem receber uma lista de entradas e saídas para que o MSBuild possa executar as verificações atualizadas apropriadas e determinar se um novo build é necessário. 

O Live Unit Testing inicia um build sempre que detecta uma alteração nos arquivos de origem. Como o build da solução gera arquivos de origem, o Live Unit Testing entrará em um loop infinito de build. Se, no entanto, as entradas e as saídas do destino forem verificadas quando o Live Unit Testing iniciar o segundo build (depois de detectar os arquivos de origem recém-gerados do build anterior), ele interromperá o loop, pois as verificações de entradas e saídas indicarão que tudo está atualizado.   

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>Como o Live Unit Testing funciona com o recurso Carga de Solução Leve? 

**Resposta:**

Atualmente, o Live Unit Testing não funciona bem com o recurso de carga de Solução Leve quando ainda não estão carregados todos os projetos na solução. Talvez você obtenha informações de cobertura incorretas nesses cenários.
 
## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>Por que o Live Unit Testing não captura a cobertura de um novo processo criado por um teste?
 
**Resposta:**

Esse é um problema conhecido que não pôde ser resolvido na versão do Visual Studio 2017. Ele deverá ser corrigido em uma próxima atualização do Visual Studio 2017. 

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>Por que nada acontece depois de incluir ou excluir testes do conjunto de Teste Dinâmico? 

**Resposta:**

Este é um problema conhecido. Para solucionar esse problema, você precisará fazer uma edição em qualquer arquivo depois de incluir ou excluir os testes.  

## <a name="live-unit-testing-and-editor-icons"></a>Live Unit Testing e ícones do editor 

**Por que não é possível ver nenhum ícone no editor, embora o Live Unit Testing pareça estar executando os testes de acordo com as mensagens na janela de saída?** 

**Resposta:**

Isso ocorre se os assemblies nos quais o Live Unit Testing está operando não estão instrumentados por algum motivo. Por exemplo, o Live Unit Testing não é compatível com projetos que definem `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. Nesse caso, o processo de build precisará ser atualizado para remover essa configuração ou para alterá-la para `true`, a fim de que o Live Unit Testing funcione.  

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>Como fazer para coletar logs mais detalhados de relatórios de bugs de arquivo? 

**Resposta:**

É possível fazer várias coisas para coletar logs mais detalhados: 

- Acesse **Ferramentas**, **Opções**, **Live Unit Testing** e altere a opção de log para **Detalhado**. Isso faz com que logs mais detalhados sejam mostrados na janela de saída. 

- Defina a variável de ambiente do usuário `LiveUnitTesting_BuildLog` com o nome do arquivo que você deseja usar para capturar o log do MSBuild. Em seguida, as mensagens de log detalhado do MSBuild de builds do Live Unit Testing podem ser recuperadas desse arquivo.

- Defina a variável de ambiente de usuário `LiveUnitTesting_TestPlatformLog` como `1` para capturar o log da Plataforma de Teste. Em seguida, as mensagens de log da Plataforma de Teste das execuções do Live Unit Testing poderão ser recuperadas de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`.

- Crie uma variável de ambiente em nível de usuário chamada `VS_UTE_DIAGNOSTICS` e defina-a como 1 (ou qualquer valor) e reinicie o Visual Studio. Agora você verá muitos logs na guia **Saída – Testes** do Visual Studio. 
 
## <a name="see-also"></a>Consulte também

[Teste de Unidade Dinâmica](live-unit-testing.md)
 

