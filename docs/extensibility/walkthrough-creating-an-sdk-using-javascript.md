---
title: 'Passo a passo: Criando um SDK usando JavaScript | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6a46542dcbd293971011d3e04409a52b3d88a01c
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>Passo a passo: Criando um SDK usando JavaScript
Este passo a passo ensina a usar o JavaScript para criar uma matemática simple SDK como uma extensão do Studio Visual (VSIX).  Passo a passo é dividida em partes:  
  
-   [Para criar o projeto do SDK de extensão SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [Para criar um aplicativo de exemplo que usa o SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 Para JavaScript, não há nenhum tipo de projeto de biblioteca de classe. Neste passo a passo, o arquivo de exemplo arithmetic.js é criado diretamente no projeto do VSIX. Na prática, recomendamos que você primeiro compilar e testar os arquivos JavaScript e CSS como um aplicativo da Windows Store — por exemplo, usando o **aplicativo em branco** modelo — antes de colocá-los em um projeto do VSIX.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="a-namecreatesimplemathvsixa-to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>Para criar o projeto do SDK de extensão SimpleMathVSIX  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Na lista de categorias de modelo, em **Visual C#**, selecione **extensibilidade**e, em seguida, selecione o **projeto VSIX** modelo.  
  
3.  No **nome** texto, especifique `SimpleMathVSIX` e escolha o **Okey** botão.  
  
4.  Se o **Assistente de pacote do Visual Studio** for exibida, escolha o **próximo** botão o **boas-vindas** página e, em seguida, em **página 1 de 7**, escolha o **concluir** botão.  
  
     Embora o **Designer de manifesto** é aberta, vamos manter este passo a passo simples modificando diretamente o arquivo de manifesto.  
  
5.  Em **Solution Explorer**, abra o menu de atalho para o arquivo source.extension.vsixmanifest e, em seguida, escolha **Exibir código**. Use esse código para substituir o conteúdo existente no arquivo.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  Em **Solution Explorer**, abra o menu de atalho para o projeto SimpleMathVSIX e, em seguida, escolha **adicionar**, **Novo Item**.  
  
7.  No **dados** categoria, selecione **arquivo XML**, nomeie o arquivo `SDKManifest.xml`e escolha o **adicionar** botão.  
  
8.  Em **Solution Explorer**, abra o menu de atalho para o arquivo Sdkmanifest e, em seguida, escolha **abrir** para exibir o arquivo no **Editor XML**.  
  
9. Adicione o seguinte código no arquivo Sdkmanifest.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. Em **Solution Explorer**, no menu de atalho para o arquivo Sdkmanifest, escolha **propriedades**.  
  
11. No **propriedades** janela, defina a **incluir na VSIX** propriedade **True**.  
  
12. Em **Solution Explorer**, no menu de atalho para o projeto SimpleMathVSIX, escolha **adicionar**, **nova pasta**e, em seguida, nomeie a pasta `Redist`.  
  
13. Adicione subpastas Redist para criar essa estrutura de pastas:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. No menu de atalho para a pasta \js\, escolha **adicionar**, **Novo Item**.  
  
15. Em **itens do Visual c#**, selecione o **Web** categoria e selecione o **arquivo JavaScript** item. Nomeie o arquivo `arithmetic.js`e, em seguida, escolha o **adicionar** botão.  
  
16. Insira o código a seguir arithmetic.js:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. Em **Solution Explorer**, no menu de atalho para o arquivo arithmetic.js, escolha **propriedades**. Fazer essas alterações de propriedade:  
  
    -   Definir o **incluir na VSIX** propriedade **True**.  
  
    -   Definir o **Copy to Output Directory** propriedade **copiar sempre**.  
  
18. Em **Solution Explorer**, no menu de atalho para o projeto SimpleMathVSIX, escolha **criar**.  
  
19. Após a compilação concluída com êxito, no menu de atalho do projeto, escolha **Abrir pasta no Explorador de arquivos**. Navegue até \bin\debug\\e execute `SimpleMathVSIX.vsix` para instalá-lo.  
  
20. Escolha o **instalar** botão e permita a conclusão da instalação.  
  
21. Reinicie o Visual Studio.  
  
##  <a name="a-namecreatesampleappa-to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>Para criar um aplicativo de exemplo que usa o SDK  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
2.  Na lista de categorias de modelo, em **JavaScript**, selecione **da Windows Store**e, em seguida, selecione o **aplicativo em branco** modelo.  
  
3.  No **nome** , especifique `ArithmeticUI`. Escolha o **Okey** botão.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o projeto ArithmeticUI e, em seguida, escolha **adicionar**, **referência**.  
  
5.  Em **Windows**, escolha **extensões**e observe que **cálculos matemáticos simples** é exibida.  
  
6.  Selecione o **cálculos matemáticos simples** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
7.  Em **Solution Explorer**, em **referências**, observe que o **cálculos matemáticos simples** referência é exibida. Expandi-lo e observe que há uma pasta \js\ que inclui arithmetic.js. Você pode abrir arithmetic.js para confirmar se o seu código-fonte foi instalado.  
  
8.  Use o código a seguir para substituir o conteúdo de Default. htm.  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. Use o seguinte código para substituir o conteúdo de \js\default.js.  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. Substitua o conteúdo de \css\default.css por este código:  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. Escolha a tecla F5 para compilar e executar o aplicativo.  
  
12. No aplicativo da interface do usuário, digite os dois números, selecione uma operação e, em seguida, escolha o ** = ** botão. O resultado correto é exibido.  
  
## <a name="see-also"></a>Consulte também  
 [Criando um Kit de desenvolvimento de Software](../extensibility/creating-a-software-development-kit.md)
