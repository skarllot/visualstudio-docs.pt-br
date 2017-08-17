---
title: "Escopo variável (JavaScript) | Microsoft Docs"
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
- scope, JavaScript
- variable scope [JavaScript]
- variables, scope [JavaScript]
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 5afc99bf3d1006b68e1d6c4c8d5bbcfc90eb776f
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="variable-scope-javascript"></a>Escopo variável (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tem dois escopos: global e local. Uma variável declarada fora de uma definição de função é global e o valor dela é acessível e pode ser modificado por todo o programa. Uma variável que é declarada dentro de uma definição de função é local. Ela é criada e destruída cada vez que a função é executada e ela não pode ser acessada por nenhum código fora da função. O JavaScript não dá suporte a escopo de bloco (no qual um conjunto de chaves `{. . .}` define um novo escopo), exceto no caso especial de variáveis de escopo de bloco.  
  
## <a name="scope-in-javascript"></a>Escopo em JavaScript  
 Uma variável local pode ter o mesmo nome de uma global, mas elas são totalmente separadas; alterar o valor de uma variável não tem nenhum efeito na outra. Somente a versão local tem significado dentro da função na qual ela é declarada.  
  
```JavaScript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 Em JavaScript, as variáveis são avaliadas como se elas fossem declaradas no início do escopo em que elas existem. Às vezes isso resulta em um comportamento inesperado, conforme mostrado aqui.  
  
```JavaScript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 Quando [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] executa uma função, ele primeiro procura por todas as declarações de variável, por exemplo, `var someVariable;`. Ele cria as variáveis com um valor inicial de `undefined`. Se uma variável é declarada com um valor, por exemplo, `var someVariable = "something";`, ela ainda tem inicialmente o valor `undefined` e assume o valor declarado apenas quando a linha que contém a declaração é executada.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] processa todas as declarações de variável antes de executar qualquer código, esteja a declaração dentro de um bloco ou de outro constructo. Quando [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tiver encontrado todas as variáveis, ele executará o código na função. Se uma variável é declarada implicitamente dentro de uma função – ou seja, se ela aparece no lado esquerdo de uma expressão de atribuição, mas não foi declarada com `var` – ela é criada como uma variável global.  
  
 Em JavaScript, uma função interna (aninhada) armazena referências para as variáveis locais que estão presentes no mesmo escopo da função em si, mesmo depois que a função retorna. Esse conjunto de referências é chamado de fechamento. No exemplo a seguir, a segunda chamada para a função interna gera a mesma mensagem ("Olá Bill") que a primeira chamada, porque o parâmetro de entrada para a função externa, `name`, é uma variável local que é armazenada no fechamento da função interna.  
  
```JavaScript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## <a name="block-scoped-variables"></a>Variáveis com escopo de bloco  
 O Internet Explorer 11 introduz suporte para [let](../../javascript/reference/let-statement-javascript.md) e [const](../../javascript/reference/const-statement-javascript.md), que são variáveis de escopo de bloco. Para essas variáveis, as chaves `{. . .}` definem um novo escopo. Quando você define uma dessas variáveis para um valor específico, o valor só se aplica ao escopo no qual ele está definido.  
  
 O exemplo a seguir ilustra o uso de `let` e de escopo de bloco.  
  
> [!NOTE]
>  O código a seguir tem suporte no modo padrão do Internet Explorer 11 e posterior.  
  
```JavaScript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```
