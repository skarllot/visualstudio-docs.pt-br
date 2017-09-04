---
title: "Exibindo texto em uma página da Web (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="displaying-text-in-a-webpage-javascript"></a>Exibindo texto em uma página da Web (JavaScript)
Há vários modos de exibir texto nas páginas da Web. Cada um desses modos apresenta vantagens e desvantagens, e é compatível com usos específicos.  
  
## <a name="displaying-text"></a>Exibindo texto  
  
-   O modo recomendado para exibir o texto é criar um elemento e gravar este código na propriedade textContent correspondente a ele.  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     Nesse exemplo, o valor de `text` é "my text". Porém, o valor resultante da inclusão ou configuração da propriedade `textContent` em um nó pai pode incluir o texto dos nós filhos. O exemplo a seguir mostra que a propriedade `textContent` configurada em um nó filho está incluída no valor da propriedade `textContent` do nó pai:  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     Nesse exemplo, o valor de `text` é "[nested]".  
  
-   Você também pode criar um elemento e gravar suas propriedades [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) ou [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx). A configuração dessas propriedades afeta o texto do elemento em si, mas não dos elementos filhos. No entanto, essas propriedades também apresentam algumas desvantagens:  
  
    -   A propriedade [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) não funciona em todos os navegadores. Por isso, evite usá-la para não ter problemas de compatibilidade.  
  
    -   A propriedade [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) é afetada pelos estilos CSS e não será exibida se o elemento estiver oculto.  
  
    -   A propriedade [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) obtém e define nós aninhados e texto. As propriedades que não são seguras podem ser usadas em ataques de injeção de script. Além disso, quando essa propriedade é definida como texto sem marcas HTML, todos os nós configurados anteriormente são removidos.  
  
-   Você pode usar o método `document.write` sem precisar criar um elemento. No entanto, esse método limpa toda a página da Web, o que talvez não seja o resultado desejado.  
  
     O exemplo a seguir mostra uma das desvantagens do uso de `document.write`. O script deve mostrar a hora a cada cinco segundos, mas mostra apenas duas vezes. Quando `document.write` é chamado pela segunda vez, a página já está carregada, e `document.write` limpa toda a página ao chamar `document.open`. Nesse momento, a função `ShowTime` já não existe mais.  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     Para corrigir o código acima, remova a linha que contém `document.write` e remova os comentários das duas linhas do código abaixo dela.  
  
-   Você também pode usar uma função `alert``prompt` ou `confirm`, que exibe uma mensagem em uma janela pop-up. Na maioria dos casos, não recomendamos usar janelas pop-up em um navegador da Web. Grande parte dos navegadores modernos têm configurações que bloqueiam as janelas pop-up imediatamente. Com isso, é possível que sua mensagem não seja exibida. Além disso, o uso de janelas pop-up pode criar um loop infinito, o que impede o usuário de fechar a página da Web como de costume.
