---
title: 'Passo a passo: Depurando um modelo de texto que acessa um modelo | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7bbe2b592dc315bc0885e1f1ca4c890e4e66255d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Instruções passo a passo: depurando um modelo (template) de texto que acessa um modelo
Quando você modificar ou adicionar modelos de texto em uma solução de linguagem específica do domínio, você pode receber erros quando o mecanismo transforma o modelo de código-fonte ou quando ele compila o código gerado. A instrução a seguir demonstra algumas das coisas que você pode fazer para depurar um modelo de texto.  
  
> [!NOTE]
>  Para obter mais informações sobre o texto modelos em geral, consulte [de geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md). Para obter mais informações sobre depuração de modelos de texto, consulte [passo a passo: depurando um modelo de texto](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Criando uma solução de linguagem específica do domínio  
 Neste procedimento, você deve criar uma solução de linguagem específica do domínio que tem as seguintes características:  
  
-   Nome: DebuggingTestLanguage  
  
-   Modelo de solução: linguagem mínima  
  
-   Extensão de arquivo: .ddd  
  
-   Nome da empresa: Fabrikam  
  
 Para obter mais informações sobre como criar uma solução de linguagem específica do domínio, consulte [como: criar uma solução de linguagem específica do domínio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Criando um modelo de texto  
 Adicione um modelo de texto à sua solução.  
  
#### <a name="to-create-a-text-template"></a>Para criar um modelo de texto  
  
1.  Compilar a solução e iniciar executando-o no depurador. (No **criar** menu, clique em **recompilar solução**e, em seguida, no **depurar** menu, clique em **iniciar depuração**.) Uma nova instância do Visual Studio abre o projeto de depuração.  
  
2.  Adicione um arquivo de texto chamado `DebugTest.tt` para depuração de projeto.  
  
3.  Verifique se o **ferramenta personalizada** de DebugTest.tt é definida como `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Diretivas de depuração que acessar um modelo a partir de um modelo de texto  
 Antes de poder acessar um modelo de instruções e expressões em um modelo de texto, você deve primeiro chamar um processador de diretriz gerado. Chamar o processador de diretriz gerado disponibiliza as classes em seu modelo para o código de modelo de texto como propriedades. Para obter mais informações, consulte [acessar modelos de modelos de texto](../modeling/accessing-models-from-text-templates.md).  
  
 Nos procedimentos a seguir, você irá depurar um nome incorreto de diretiva e um nome de propriedade incorreta.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Para depurar um nome incorreto de diretiva  
  
1.  Substitua o código em DebugTest.tt com o código a seguir:  
  
    > [!NOTE]
    >  O código contém um erro. Introduzindo o erro para depurá-lo.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  Em **Solution Explorer**, clique com botão direito DebugTest.tt e, em seguida, clique em **executar ferramenta personalizada**.  
  
     O **Error List** janela exibirá este erro:  
  
     **O processador chamado 'DebuggingTestLanguageDirectiveProcessor' não oferece suporte à diretriz chamada 'modelRoot'. A transformação não será executada.**  
  
     Nesse caso, a diretiva chamada contém um nome de diretiva incorreto. Você especificou `modelRoot` como o nome da diretiva, mas o nome correto de diretriz é `DebuggingTestLanguage`.  
  
3.  Clique duas vezes no **Error List** janela para ir para o código.  
  
4.  Para corrigir o código, altere o nome de diretiva para `DebuggingTestLanguage`.  
  
     A alteração é realçada.  
  
    ```c#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  Em **Solution Explorer**, clique com botão direito DebugTest.tt e, em seguida, clique em **executar ferramenta personalizada**.  
  
     Agora o sistema transforma o modelo de texto e gera o arquivo de saída correspondente. Você não verá todos os erros a **Error List** janela.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Para depurar um nome de propriedade incorreta  
  
1.  Substitua o código em DebugTest.tt com o código a seguir:  
  
    > [!NOTE]
    >  O código contém um erro. Introduzindo o erro para depurá-lo.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  No **Solution Explorer**, clique com botão direito DebugTest.tt e, em seguida, clique em **executar ferramenta personalizada**.  
  
     O **Error List** janela aparece e exibe um desses erros:  
  
     (C#)  
  
     **Compilando transformação: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation' não contém uma definição para 'ExampleModel'**  
  
     (Visual Basic)  
  
     **Compilando transformação: 'ExampleModel' não é um membro de ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**  
  
     Nesse caso, o código do modelo de texto contém um nome de propriedade incorreta. Você especificou `ExampleModel` como o nome da propriedade, mas a propriedade correta nome é `LibraryModel`. Você pode encontrar o nome da propriedade correto de fornece o parâmetro, conforme mostrado no código a seguir:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Clique duas vezes em erro na janela lista de erros para saltar para o código.  
  
4.  Para corrigir o código, altere o nome de propriedade para `LibraryModel` no código do modelo de texto.  
  
     As alterações são realçadas.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5.  Em **Solution Explorer**, clique com botão direito DebugTest.tt e, em seguida, clique em **executar ferramenta personalizada**.  
  
     Agora o sistema transforma o modelo de texto e gera o arquivo de saída correspondente. Você não verá todos os erros a **Error List** janela.
