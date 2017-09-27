---
title: 'Passo a passo: Depurando um modelo de texto que acessa um modelo | Microsoft Docs'
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2943b49571077ac1cab87db5ecc4d0f82390273e
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Instruções passo a passo: depurando um modelo (template) de texto que acessa um modelo
Quando você modificar ou adicionar modelos de texto em uma solução de linguagem específica de domínio, você pode receber erros quando o mecanismo transforma o modelo de código-fonte ou quando ele compila o código gerado. A instrução a seguir demonstra alguns dos itens que você pode fazer para depurar um modelo de texto.  
  
> [!NOTE]
>  Para obter mais informações sobre o texto modelos em geral, consulte [geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md). Para obter mais informações sobre modelos de texto de depuração, consulte [passo a passo: depurando um modelo de texto](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Criando uma solução de linguagem específica de domínio  
 Neste procedimento, você deve criar uma solução de linguagem específica de domínio que tenha as seguintes características:  
  
-   Nome: DebuggingTestLanguage  
  
-   Modelo de solução: mínimo de linguagem  
  
-   Extensão de arquivo: .ddd  
  
-   Nome da empresa: Fabrikam  
  
 Para obter mais informações sobre como criar uma solução de linguagem específica de domínio, consulte [como: criar uma solução de linguagem específica de domínio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Criando um modelo de texto  
 Adicione um modelo de texto à sua solução.  
  
#### <a name="to-create-a-text-template"></a>Para criar um modelo de texto  
  
1.  Compile a solução e iniciar a execução no depurador. (No **criar** menu, clique em **recompilar solução**e, em seguida, no **depurar** menu, clique em **iniciar depuração**.) Uma nova instância do Visual Studio abrirá o projeto de depuração.  
  
2.  Adicione um arquivo de texto chamado `DebugTest.tt` para o projeto de depuração.  
  
3.  Verifique se o **ferramenta personalizada** de DebugTest.tt é definida como `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Diretivas de depuração que acessar um modelo a partir de um modelo de texto  
 Antes de poder acessar um modelo das instruções e expressões em um modelo de texto, você deve primeiro chamar um processador de diretiva gerado. Chamar o processador de diretiva gerado disponibiliza as classes em seu modelo para o código de modelo de texto como propriedades. Para obter mais informações, consulte [acessar modelos de modelos de texto](../modeling/accessing-models-from-text-templates.md).  
  
 Nos procedimentos a seguir, você irá depurar um nome de diretiva incorreto e um nome de propriedade incorreta.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Para depurar um nome de diretiva incorreto  
  
1.  Substitua o código em DebugTest.tt com o código a seguir:  
  
    > [!NOTE]
    >  O código contém um erro. Introduzindo o erro para depurá-lo.  
  
    ```csharp  
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
  
    ```vb  
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
  
2.  Em **Solution Explorer**, clique com botão direito DebugTest.tt e, em seguida, clique em **executar personalizado ferramenta**.  
  
     O **lista de erros** janela exibe o erro:  
  
     **O processador chamado 'DebuggingTestLanguageDirectiveProcessor' não oferece suporte à diretiva chamada 'modelRoot'. A transformação não será executada.**  
  
     Nesse caso, a chamada a diretiva contém um nome de diretiva incorreto. Você especificou `modelRoot` como o nome da diretiva, mas o nome de diretiva correto é `DebuggingTestLanguage`.  
  
3.  Clique duas vezes o erro a **lista de erros** janela para ir para o código.  
  
4.  Para corrigir o código, altere o nome de diretiva para `DebuggingTestLanguage`.  
  
     A alteração é realçada.  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  Em **Solution Explorer**, clique com botão direito DebugTest.tt e, em seguida, clique em **executar personalizado ferramenta**.  
  
     Agora o sistema transforma o modelo de texto e gera o arquivo de saída correspondente. Você não verá quaisquer erros no **lista de erros** janela.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Para depurar um nome de propriedade incorreta  
  
1.  Substitua o código em DebugTest.tt com o código a seguir:  
  
    > [!NOTE]
    >  O código contém um erro. Introduzindo o erro para depurá-lo.  
  
    ```csharp  
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
  
    ```vb  
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
  
2.  No **Solution Explorer**, clique com botão direito DebugTest.tt e, em seguida, clique em **executar personalizado ferramenta**.  
  
     O **lista de erros** janela é exibida e mostra um desses erros:  
  
     (C#)  
  
     **Compilando transformação: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation' não contém uma definição para 'ExampleModel'**  
  
     (Visual Basic)  
  
     **Compilando transformação: 'ExampleModel' não é um membro de ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**  
  
     Nesse caso, o código de modelo de texto contém um nome de propriedade incorreta. Você especificou `ExampleModel` como o nome da propriedade, mas a propriedade correta é nome `LibraryModel`. Você pode encontrar o nome da propriedade correto do fornece o parâmetro, conforme mostrado no código a seguir:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Clique duas vezes em erro na janela lista de erros para saltar para o código.  
  
4.  Para corrigir o código, altere o nome da propriedade `LibraryModel` no código de modelo de texto.  
  
     As alterações são realçadas.  
  
    ```csharp  
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
  
    ```vb  
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
  
5.  Em **Solution Explorer**, clique com botão direito DebugTest.tt e, em seguida, clique em **executar personalizado ferramenta**.  
  
     Agora o sistema transforma o modelo de texto e gera o arquivo de saída correspondente. Você não verá quaisquer erros no **lista de erros** janela.
