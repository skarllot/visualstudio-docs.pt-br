---
title: "Apenas Meu C&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Apenas Meu C&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os desenvolvedores que usam linguagens do .NET Framework estão familiarizados com Just My Code recurso do depurador que as etapas de sistema, estrutura e outras chamadas de não usuário e recolhe essas chamadas nas janelas de pilha de chamada. Apenas meu código foi estendido para as linguagens C\+\+ e JavaScript. Este tópico descreve os detalhes do uso de Just My Code no .NET Framework, C\+\+ nativo e JavaScript projetos.  
  
##  <a name="BKMK_Enable_or_disable_Just_My_Code"></a> Ativar ou desativar o Just My Code  
 Para ativar ou desativar o Just My Code, escolha **Opções e configurações** sobre o **Depurar** menu. No **depuração** \/ **geral** nó, marque ou desmarque **Habilitar Just My Code**.  
  
 ![Enable Just My Code in the Options dialog box](../debugger/media/dbg_justmycode_options.png "DBG\_JustMyCode\_Options")  
  
> [!NOTE]
>  O **Habilitar Just My Code** configuração é uma configuração global que é aplicada a todos os projetos do Visual Studio em todos os idiomas.  
  
###  <a name="BKMK_Override_call_stack_filtering"></a> Substituir filtragem da pilha de chamada  
 Em exibições da pilha de chamadas, como as janelas pilha de chamadas e tarefas, apenas meu código recolhe o código não\-usuário em um quadro anotado rotulado `[External Code]`. Para exibir os quadros recolhidos, escolha **Mostrar código externo** no menu de contexto da pilha de chamadas exibir.  
  
> [!NOTE]
>  O **Mostrar código externo** configuração é salva para o criador de perfil do usuário atual. Ela é aplicada a todos os projetos em todos os idiomas que são abertos pelo usuário.  
  
##  <a name="BKMK__NET_Framework_Just_My_Code"></a> Apenas meu código do .NET framework  
  
###  <a name="BKMK_NET_User_and_non_user_code"></a> Código de não usuário e  
 Para distinguir código de usuário de código não\-usuário, Just My Code examina arquivos de símbolo \(. PDB\) e otimizações de programa. O depurador considera o código para ser o código não\-usuário quando o binário é otimizado ou quando o arquivo. PDB não está disponível.  
  
 Três atributos também afetam o que o depurador considera como meu código:  
  
-   <xref:System.Diagnostics.DebuggerNonUserCodeAttribute> informa o depurador que o código para que é aplicado não é meu código.  
  
-   <xref:System.Diagnostics.DebuggerHiddenAttribute> oculta o código do depurador, mesmo se Just My Code está desativado.  
  
-   <xref:System.Diagnostics.DebuggerStepThroughAttribute> informa o depurador para percorrer o código que ele é aplicado, em vez de depurar o código.  
  
 Todos os demais códigos são considerados código de usuário.  
  
###  <a name="BKMK_NET_Stepping_behavior"></a> Comportamento de depuração  
 Quando você **Step Into** \(atalho de teclado: F11\) código de não usuário, o depurador percorre o código para a próxima instrução do usuário. Quando você **Sair** \(teclado: Shift \+ F11\), o depurador executa a próxima linha do código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo é encerrado, um ponto de interrupção é atingido ou ocorre uma exceção.  
  
###  <a name="BKMK_NET_Breakpoint_behavior"></a> Comportamento de ponto de interrupção  
 Quando o Just My Code estiver habilitado, você pode escolher **Interromper tudo** \(teclado: Ctrl \+ Alt \+ Break\) e interromper a execução em um local onde não há nenhum código de usuário para exibir. Quando isso acontece, a janela de origem não é exibida. Se você, em seguida, escolha um comando de depuração, o depurador leva você para a próxima linha do código do usuário.  
  
###  <a name="BKMK_NET_Exception_behavior"></a> Comportamento de exceção  
 Se uma exceção não tratada ocorrer em código não\-usuário, o depurador interrompe na linha de código de usuário em que a exceção foi gerada.  
  
 Se as exceções de primeira chance são habilitadas para a exceção, a linha de código do usuário é realçada em verde. A pilha de chamadas exibe um quadro anotado rotulado **\[código externo\]**.  
  
##  <a name="BKMK_C___Just_My_Code"></a> Apenas meu código do C\+\+  
  
###  <a name="BKMK_CPP_User_and_non_user_code"></a> Código de não usuário e  
 C\+\+ Just My Code é diferente do .NET Framework e o JavaScript Just My Code, como o comportamento de depuração é independente do comportamento da pilha de chamada.  
  
 **Pilhas de chamadas**  
  
 Por padrão, o depurador considera estas funções código de não usuário nas janelas de pilha de chamada:  
  
-   Funções com informações de origem retiradas no respectivo arquivo de símbolos.  
  
-   Funções de onde os arquivos de símbolos indicam que não há nenhum arquivo de origem correspondente para o quadro de pilha.  
  
-   Funções especificadas na `*.natjmc` arquivos de `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
 **Passo a passo**  
  
 Por padrão, somente as funções especificadas em `*.natstepfilter` arquivos de `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta são considerados código não\-usuário.  
  
 Você pode criar seu próprio `.natstepfilter` e `.natjmc` para personalizar a depuração e chamar o comportamento da janela de pilha no `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers`.  
  
###  <a name="BKMK_CPP_Stepping_behavior"></a> Comportamento de depuração  
 Quando você **Step Into** \(atalho de teclado: F11\) código não\-usuário do código do usuário, o depurador percorre o código para a próxima linha de código do usuário. Quando você **Sair** \(teclado: Shift \+ F11\), o depurador executa a próxima linha do código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo é encerrado, um ponto de interrupção é atingido ou ocorre uma exceção.  
  
 Se o depurador for interrompido no código de não usuário \(por exemplo, se um comando interromper tudo parar em código não\-usuário\), depuração continua no código não\-usuário.  
  
###  <a name="BKMK_CPP_Exception_behavior"></a> Comportamento de exceção  
 Quando o depurador atinge uma exceção, ele irá parar na exceção independentemente de ser em usuário ou código não\-usuário. O **sem tratamento do usuário** opções no **exceções** caixa de diálogo são ignorados.  
  
###  <a name="BKMK_CPP_Customize_stepping_behavior"></a> Personalizar o comportamento de depuração  
 Você pode especificar funções para percorrer listando\-os como código de não usuário em `*.natstepfilter` arquivos.  
  
-   Para especificar o código de não usuário para todos os usuários do computador do Visual Studio, adicione o arquivo. natstepfilter para o `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
-   Para especificar o código de não usuário para um usuário individual, adicione o arquivo. natstepfilter para o `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` pasta.  
  
 os arquivos. natstepfilter são arquivos xml com esta sintaxe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Action>StepAction</Action>  
    </Function>  
    <Function>  
        <Name>FunctionSpec</Name>  
        <Module>ModuleSpec</Module>  
        <Action>StepAction</Action>  
    </Function>  
</StepFilter>  
  
```  
  
|Elemento|Descrição|  
|--------------|---------------|  
|Função|Obrigatório. Especifica uma ou mais funções como funções de não usuário.|  
|`Name`|Obrigatório. Especificando o nome completo da função para fazer a correspondência de expressão regular formatada como uma ECMA\-262. Por exemplo:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> informa o depurador que todos os métodos `MyNS::MyClass` devem ser considerados código não\-usuário. A correspondência diferencia maiúsculas de minúsculas.|  
|`Module`|Opcional. Especificando o caminho completo para o módulo que contém a função de expressão regular formatada como uma ECMA\-262. A correspondência diferencia maiúsculas de minúsculas.|  
|`Action`|Obrigatório. Um desses valores diferenciam maiúsculas de minúsculas:<br /><br /> -   `NoStepInto`  – informa o depurador para depurar a função correspondente.<br />-   `StepInto`  – informa o depurador para percorrer funções correspondentes, substituindo qualquer outro `NoStepInto` pelas funções correspondentes.|  
  
###  <a name="BKMK_CPP_Customize_call_stack_behavior"></a> Personalizar comportamento da pilha de chamada  
 Você pode especificar módulos, arquivos de origem e funções para serem tratados como código de não usuário em pilhas de chamadas especificando\-os em `*.natjmc` arquivos.  
  
-   Para especificar o código de não usuário para todos os usuários do computador do Visual Studio, adicione o arquivo. natjmc para o `%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers` pasta.  
  
-   Para especificar o código de não usuário para um usuário individual, adicione o arquivo. natjmc para o `%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers` pasta.  
  
 os arquivos. natjmc são arquivos xml com esta sintaxe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">  
  
  <!-- Modules -->  
  <Module Name="ModuleSpec" />  
  <Module Name="ModuleSpec" Company="CompanyName" />  
  
  <!-- Files -->  
  <File Name="FileSpec"/>  
  
  <!-- Functions -->  
  <Function Name="FunctionSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" />  
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />  
  
</NonUserCode>  
  
```  
  
 **Atributos do elemento de módulo**  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Name`|Obrigatório. O caminho completo do módulo ou módulos. Você pode usar os caracteres curinga do Windows `?` \(zero ou um caractere\) e `*` \(zero ou mais caracteres\). Por exemplo,<br /><br /> `<Module Name=”?:\3rdParty\UtilLibs\*” />`<br /><br /> informa o depurador para tratar todos os módulos no `\3rdParty\UtilLibs` em qualquer unidade como código externo.|  
|`Company`|Opcional. O nome da empresa que publica o módulo que está incorporado no arquivo executável. Você pode usar esse atributo para resolver a ambiguidade dos módulos.|  
  
 **Atributos do elemento de arquivo**  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Name`|Obrigatório. O caminho completo do arquivo de origem ou arquivos a serem tratados como código externo. Você pode usar os caracteres curinga do Windows `?` e `*` ao especificar o caminho.|  
  
 **Atributos do elemento de função**  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Name`|Obrigatório. O nome totalmente qualificado da função a ser tratados como código externo.|  
|`Module`|Opcional. O nome ou o caminho completo para o módulo que contém a função. Você pode usar esse atributo para resolver a ambiguidade de funções com o mesmo nome.|  
|`ExceptionImplementation`|Quando definido como `true`, a pilha de chamadas exibe a função que lançou a exceção em vez dessa função.|  
  
##  <a name="BKMK_JavaScript_Just_My_Code"></a> Apenas meu código do JavaScript  
  
###  <a name="BKMK_JS_User_and_non_user_code"></a> Código de não usuário e  
 **Classificações de código**  
  
 JavaScript Just My Code controla a exibição de pilha de revisão e chame categorizando o código em uma destas classificações:  
  
|||  
|-|-|  
|**MyCode**|Código do usuário que você possui e controla.|  
|**LibraryCode**|Código não\-usuário de bibliotecas que você usa regularmente e seu aplicativo depende para funcionar corretamente \(por exemplo WinJS ou jQuery\).|  
|**UnrelatedCode**|Código de não usuário que pode ser executado no seu aplicativo, mas você não possui e seu aplicativo não depende diretamente para funcionar corretamente \(por exemplo, o SDK de publicidade que exibe anúncios\). Em projetos da Windows Store, qualquer código que é carregado no seu aplicativo de um URI HTTP ou HTTPS também é considerado UnrelatedCode.|  
  
 O depurador do JavaScript classifica automaticamente estes tipos de código:  
  
-   Script que é executado passando uma cadeia de caracteres para o host fornecido `eval` função é classificada como **MyCode**.  
  
-   Script que é executado passando uma cadeia de caracteres para o `Function` construtor é classificado como **LibraryCode**.  
  
-   O script que está contido em uma referência da estrutura, como WinJS ou o SDK do Azure, é classificado como **LibraryCode**.  
  
-   Script que é executado passando uma cadeia de caracteres para o `setTimeout`, `setImmediate`, ou `setInterval` é classificado como **UnrelatedCode**.  
  
-   O `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` Especifica outro código não\-usuário e para todos os projetos de JavaScript do Visual Studio.  
  
 Você pode alterar as classificações padrão e classificar arquivos específicos e urls adicionando um arquivo. JSON chamado `mycode.json` para a pasta raiz de um projeto.  
  
 Todos os demais códigos são classificados como **MyCode**.  
  
###  <a name="BKMK_JS_Stepping_behavior"></a> Comportamento de depuração  
  
-   Se uma função não for um usuário \(**MyCode**\) código, **Step Into** \(atalho de teclado: F11\) se comporta como **passar** \(teclado: F10\).  
  
-   Se uma etapa começar em não\-usuário \(**LibraryCode** ou **UnrelatedCode**\) de código, em seguida, depuração temporária se comportará como se Just My Code não está habilitado. Assim que você percorrer voltar ao código do usuário, Just My Code revisão é reativado.  
  
-   Quando uma etapa nos resultados de código do usuário em deixar o contexto de execução atual \(por exemplo, executar uma etapa na última linha de um manipulador de eventos\), o depurador pára na próxima linha do código do usuário executada. Por exemplo, se um retorno de chamada é executado em **LibraryCode** código o depurador continua até que a próxima linha de código do usuário seja executada.  
  
-   **Step Out** \(teclado: Shift \+ F11\) pára na próxima linha do código do usuário. Se nenhum código de usuário for encontrado, a execução continua até que o aplicativo é encerrado, um ponto de interrupção é atingido ou ocorre uma exceção.  
  
###  <a name="BKMK_JS_Breakpoint_behavior"></a> Comportamento de ponto de interrupção  
  
-   Pontos de interrupção definidos em qualquer código serão sempre atingidos independentemente da classificação do código  
  
-   Se o `debugger` palavra\-chave é encontrado em:  
  
    -   **LibraryCode** código, o depurador sempre interromperá.  
  
    -   **UnrelatedCode** código, o depurador não pára.  
  
###  <a name="BKMK_JS_Exception_behavior"></a> Comportamento de exceção  
 Se uma exceção não tratada ocorrer em:  
  
-   **MyCode** ou **LibraryCode** código, o depurador sempre interromperá.  
  
-   **UnrelatedCode** código, e **MyCode** ou **LibraryCode** código está na pilha de chamadas, o depurador será interrompido.  
  
 Se as exceções de primeira chance são habilitadas para a exceção na caixa de diálogo exceções e a exceção é lançada **LibraryCode** ou **UnrelatedCode** código:  
  
-   Se a exceção for tratada, o depurador não será interrompido.  
  
-   Se a exceção não for tratada, o depurador interrompe.  
  
###  <a name="BKMK_JS_Customize_Just_My_Code"></a> Personalizar apenas meu código  
 Para categorizar o usuário e código de não usuário para um único projeto do Visual Studio, adicione um arquivo. JSON chamado `mycode.json` para a pasta raiz do projeto.  
  
 As classificações são executadas nesta ordem:  
  
1.  Classificações padrão  
  
2.  Classificações no `%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json` arquivo  
  
3.  Classificações no `mycode. json` arquivo do projeto atual.  
  
 Cada etapa de classificação substitui as etapas anteriores. Um arquivo. JSON não é necessário listar todos os pares de chave\-valor e o **MyCode**, **bibliotecas**, e **Unrelated** valores podem ser matrizes vazias.  
  
 Meus arquivos. JSON de código usam a seguinte sintaxe:  
  
```json  
{  
    "Eval" : "Classification",  
    "Function" : "Classification",  
    "ScriptBlock" : "Classification",  
    "MyCode" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ],  
    "Libraries" : [  
        "UrlOrFileSpec”,  
        . .  
        "UrlOrFileSpec”  
    ],  
    "Unrelated" : [  
        "UrlOrFileSpec”,  
        . . .  
        "UrlOrFileSpec”  
    ]  
}  
  
```  
  
 **Eval, Function e ScriptBlock**  
  
 O **Eval**, **função**, e **ScriptBlock** pares chave\-valor determinam como dinamicamente código gerado é classificado.  
  
|||  
|-|-|  
|**Eval**|Script que é executado passando uma cadeia de caracteres para o host fornecido `eval` função. Por padrão, o script Eval é classificado como **MyCode**.|  
|**Função**|Script que é executado passando uma cadeia de caracteres para o `Function` construtor. Por padrão, o script Function é classificado como **LibraryCode**.|  
|**ScriptBlock**|Script que é executado passando uma cadeia de caracteres para o `setTimeout`, `setImmediate`, ou `setInterval` funções. Por padrão, o script ScriptBlock é classificado como **UnrelatedCode**.|  
  
 Você pode alterar o valor a uma dessas palavras\-chave:  
  
-   `MyCode`  classifica o script como **MyCode**.  
  
-   `Library`  classifica o script como **LibraryCode**.  
  
-   `Unrelated`  classifica o script como **UnrelatedCode**.  
  
 **MyCode, Libraries e não relacionados**  
  
 O **MyCode**, **bibliotecas**, e **Unrelated** pares chave\-valor especificam as urls ou arquivos que você deseja incluir em uma classificação:  
  
|||  
|-|-|  
|**MyCode**|Uma matriz de urls ou arquivos que são classificados como **MyCode**.|  
|**Libraries**|Uma matriz de urls ou arquivos que são classificados como **LibraryCode**.|  
|**Não relacionados**|Uma matriz de urls ou arquivos que são classificados como **UnrelatedCode**.|  
  
 A cadeia de caracteres de url ou o arquivo pode conter um ou mais `*` caracteres, que correspondem a zero ou mais caracteres.`*` é o equivalente da expressão regular `.*`.