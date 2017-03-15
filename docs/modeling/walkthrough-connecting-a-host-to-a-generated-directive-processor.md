---
title: 'Passo a passo: Conectando um Host a um processador de diretriz gerado | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 47
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 3cdbd2adb7b956849e5582e8a5b1ca80a6f5166d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Instruções passo a passo: conectando um host a um processador de diretriz gerado
Você pode escrever seu próprio host que processa os modelos de texto. Um host personalizado básico é demonstrado na [passo a passo: Criando um Host de modelo de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md). Você pode estender esse host para adicionar funções como gerar vários arquivos de saída.  
  
 Neste passo a passo, você expandir seu host personalizado para que ele oferece suporte a modelos de texto que chamam processadores de diretriz. Quando você define uma linguagem específica do domínio, ele gera uma *processador de diretriz* para o modelo de domínio. O processador de diretriz torna mais fácil para os usuários criem modelos que acessar o modelo, reduzindo a necessidade de escrever o assembly e importar diretivas nos modelos.  
  
> [!WARNING]
>  Este passo a passo [passo a passo: Criando um Host de modelo de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md). Execute esse passo a passo primeiro.  
  
 Esta explicação passo a passo inclui as seguintes tarefas:  
  
-   Usando [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para gerar um processador de diretriz se baseia em um modelo de domínio.  
  
-   Conectando um host de modelo de texto personalizado para o processador de diretriz gerado.  
  
-   Testando o host personalizado com o processador de diretriz gerado.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para definir uma DSL, é necessário ter instalados os seguintes componentes:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|SDK de Visualização e Modelagem do Visual Studio||  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
 Além disso, você deve ter a transformação do modelo de texto personalizado criada em [passo a passo: Criando um Host de modelo de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Usando ferramentas de linguagem específica do domínio para gerar um processador de diretriz  
 Neste passo a passo, você pode usar o Assistente de Designer de linguagem específica do domínio para criar uma linguagem específica do domínio para a solução DSLMinimalTest.  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Usar ferramentas de linguagem específica do domínio para gerar um processador de diretriz se baseia em um modelo de domínio  
  
1.  Crie uma solução de linguagem específica do domínio que tem as seguintes características:  
  
    -   Nome: DSLMinimalTest  
  
    -   Modelo de solução: linguagem mínima  
  
    -   Extensão de arquivo: min  
  
    -   Nome da empresa: Fabrikam  
  
     Para obter mais informações sobre como criar uma solução de linguagem específica do domínio, consulte [como: criar uma solução de linguagem específica do domínio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
2.  No menu **Compilar**, clique em **Compilar Solução**.  
  
    > [!IMPORTANT]
    >  Esta etapa gera o processador de diretriz e adiciona a chave para ele no registro.  
  
3.  Sobre o **depurar** menu, clique em **iniciar depuração**.  
  
     Uma segunda instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é aberto.  
  
4.  Na compilação experimental, em **Solution Explorer**, duas vezes no arquivo **sample.min**.  
  
     O arquivo é aberto no designer. Observe que o modelo tem dois elementos, ExampleElement1 e ExampleElement2 e um link entre eles.  
  
5.  Feche a segunda instância de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
6.  Salve a solução e, em seguida, feche o Designer de linguagem específica do domínio.  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Conectando um Host de modelo de texto personalizado a um processador de diretriz  
 Depois de gerar o processador de diretriz, você se conecta o processador de diretriz e o host de modelo de texto personalizado que você criou na [passo a passo: Criando um Host de modelo de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Para se conectar a um host de modelo de texto personalizado para o processador de diretriz gerado  
  
1.  Abra a solução de CustomHost.  
  
2.  Sobre o **projeto** menu, clique em **adicionar referência**.  
  
     O **adicionar referência** caixa de diálogo é aberta com o **.NET** guia exibida.  
  
3.  Adicione as seguintes referências:  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  Na parte superior de Program.cs ou Module1. vb, adicione a seguinte linha de código:  
  
    ```c#  
    using Microsoft.Win32;  
    ```  
  
    ```vb#  
    Imports Microsoft.Win32  
    ```  
  
5.  Localize o código para a propriedade `StandardAssemblyReferences`e substituí-lo com o código a seguir:  
  
    > [!NOTE]
    >  Nesta etapa, você deve adicionar referências aos assemblies que são exigidos pelo processador de diretriz gerado que oferecerá suporte ao seu host.  
  
    ```c#  
    //the host can provide standard assembly references  
    //the engine will use these references when compiling and  
    //executing the generated transformation class  
    //--------------------------------------------------------------  
    public IList<string> StandardAssemblyReferences  
    {  
        get  
        {  
            return new string[]  
            {  
                //if this host searches standard paths and the GAC  
                //we can specify the assembly name like this:  
                //"System"  
                //since this host only resolves assemblies from the   
                //fully qualified path and name of the assembly  
                //this is a quick way to get the code to give us the  
                //fully qualified path and name of the System assembly  
                //---------------------------------------------------------  
                typeof(System.Uri).Assembly.Location,  
                            typeof(System.Uri).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location  
  
            };  
        }  
    }  
    ```  
  
6.  Localize o código para a função `ResolveDirectiveProcessor`e substituí-lo com o código a seguir:  
  
    > [!IMPORTANT]
    >  Esse código contém referências codificadas para o nome do processador de diretriz gerado para o qual você deseja se conectar. Você pode facilmente fazer isso mais gerais, caso em que ele procura por todos os processadores de diretriz listados no registro e tenta encontrar uma correspondência. Nesse caso, o host funcionaria com qualquer processador de diretriz gerado.  
  
    ```c#  
    //the engine calls this method based on the directives the user has   
            //specified it in the text template  
            //this method can be called 0, 1, or more times  
            //---------------------------------------------------------------------  
            public Type ResolveDirectiveProcessor(string processorName)  
            {  
                //check the processor name, and if it is the name of the processor the   
                //host wants to support, return the type of the processor  
                //---------------------------------------------------------------------  
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)  
                {  
                    try  
                    {  
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";  
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))  
                        {  
                            if (specificKey != null)  
                            {  
                                List<string> names = new List<String>(specificKey.GetValueNames());  
                                string classValue = specificKey.GetValue("Class") as string;  
                                if (!string.IsNullOrEmpty(classValue))  
                                {  
                                    string loadValue = string.Empty;  
                                    System.Reflection.Assembly processorAssembly = null;  
                                    if (names.Contains("Assembly"))  
                                    {  
                                        loadValue = specificKey.GetValue("Assembly") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //the assembly must be installed in the GAC  
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);  
                                        }  
                                    }  
                                    else if (names.Contains("CodeBase"))  
                                    {  
                                        loadValue = specificKey.GetValue("CodeBase") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //loading local assembly  
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);  
                                        }  
                                    }  
                                    if (processorAssembly == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    Type processorType = processorAssembly.GetType(classValue);  
                                    if (processorType == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    return processorType;  
                                }  
                            }  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        //if the directive processor can not be found, throw an error  
                        throw new Exception("Directive Processor not found");  
                    }  
                }  
  
                //if the directive processor is not one this host wants to support  
                throw new Exception("Directive Processor not supported");  
            }  
    ```  
  
7.  Sobre o **arquivo** menu, clique em **Salvar tudo**.  
  
8.  No menu **Compilar**, clique em **Compilar Solução**.  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>Testando o Host personalizado com o processador de diretriz  
 Para testar o host de modelo de texto personalizado, primeiro você deve escrever um modelo de texto que chama o processador de diretriz gerado. Em seguida, executar o host personalizado, passe a ele o nome do modelo de texto e verificar se a diretiva foi processada corretamente.  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Para criar um modelo de texto para testar o host personalizado  
  
1.  Crie um arquivo de texto e nomeie-o `TestTemplateWithDP.tt`. Você pode usar qualquer editor de texto, como o bloco de notas, para criar o arquivo.  
  
2.  Adicione o seguinte ao arquivo de texto:  
  
    > [!NOTE]
    >  A linguagem de programação do modelo de texto não precisa coincidir com o host personalizado.  
  
    ```c#  
    Text Template Host Test  
  
    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
    <# //this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
    <# //uncomment this line to test that the host allows the engine to set the extension #>  
    <# //@ output extension=".htm" #>  
  
    <# //uncomment this line if you want to see the generated transformation class #>  
    <# //System.Diagnostics.Debugger.Break(); #>  
    <# //this code uses the results of the examplemodel directive #>  
    <#  
        foreach ( ExampleElement box in this.ExampleModel.Elements )   
        {   
            WriteLine("Box: {0}", box.Name);  
  
            foreach (ExampleElement linkedTo in box.Targets)  
            {  
                WriteLine("Linked to: {0}", linkedTo.Name);  
            }  
  
            foreach (ExampleElement linkedFrom in box.Sources)  
            {  
                WriteLine("Linked from: {0}", linkedFrom.Name);  
            }  
  
            WriteLine("");  
        }   
    #>  
    ```  
  
    ```vb#  
    Text Template Host Test  
  
    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
  
    <# 'this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
  
    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# '@ output extension=".htm" #>  
  
    <# 'Uncomment this line if you want to see the generated transformation class. #>  
    <# 'System.Diagnostics.Debugger.Break() #>  
  
    <# 'this code uses the results of the examplemodel directive #>  
  
    <#      
       For Each box as ExampleElement In Me.ExampleModel.Elements   
  
           WriteLine("Box: {0}", box.Name)  
  
            For Each LinkedTo as ExampleElement In box.Targets  
                WriteLine("Linked to: {0}", LinkedTo.Name)  
            Next  
  
            For Each LinkedFrom as ExampleElement In box.Sources  
                WriteLine("Linked from: {0}", LinkedFrom.Name)  
            Next  
  
            WriteLine("")  
  
       Next   
    #>  
    ```  
  
3.  No código, substitua \<caminho > com o caminho do arquivo Sample.min a partir da linguagem de design específica que você criou no primeiro procedimento.  
  
4.  Salve e feche o arquivo.  
  
#### <a name="to-test-the-custom-host"></a>Para testar o host personalizado  
  
1.  Abra uma janela do Prompt de Comando.  
  
2.  Digite o caminho do arquivo executável para o host personalizado, mas não pressione ENTER ainda.  
  
     Por exemplo, digite:  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  Em vez de digitar o endereço, você pode navegar até o arquivo CustomHost.exe na **Windows Explorer**e, em seguida, arraste o arquivo para a janela do Prompt de comando.  
  
3.  Digite um espaço.  
  
4.  Digite o caminho do arquivo de modelo de texto e pressione ENTER.  
  
     Por exemplo, digite:  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  Em vez de digitar o endereço, você pode navegar até o arquivo TestTemplateWithDP.txt na **Windows Explorer**e, em seguida, arraste o arquivo para a janela do Prompt de comando.  
  
     O aplicativo de host personalizado é executado e inicia o processo de transformação do modelo de texto.  
  
5.  Em **Windows Explorer**, navegue até a pasta que contém o arquivo TestTemplateWithDP.txt.  
  
     A pasta também contém o arquivo TestTemplateWithDP1.txt.  
  
6.  Abra esse arquivo para ver os resultados da transformação do modelo de texto.  
  
     Os resultados da saída de texto gerada aparecerá e deve ter esta aparência:  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: criando um host de modelo de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md)

