---
title: Cadeias de caracteres de modelo (JavaScript) | Microsoft Docs
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
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: d7b6aa430fd4f958c5519093b85d399060b6031a
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="template-strings-javascript"></a>Cadeias de caracteres de modelo (JavaScript)
Em [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], você pode usar cadeias de caracteres de modelo para construir literais de cadeia de caracteres com expressões incorporadas. Cadeias de caracteres de modelo também dão suporte interno para cadeias de caracteres de várias linhas.  
  
 Para construir uma cadeia de caracteres de modelo, use o acento grave (também chamado de crase) (`) para delimitar a cadeia de caracteres em vez de aspas simples ou duplas. O exemplo de código a seguir mostra uma cadeia de caracteres de modelo simples.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Cadeias de caracteres de modelo podem incluir quebras de linha sem exigir o uso do caractere de avanço de linha (\n).  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 O caractere $ é usado para especificar os espaços reservados em uma cadeia de caracteres de modelo. A sintaxe é ${*expressão*}, em que *expressão* é qualquer expressão JavaScript como uma variável ou função, conforme mostrado no exemplo a seguir.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Funções de modelo marcadas, que permitem que você modifique o valor de uma cadeia de caracteres de modelo usando uma função que é invocada com argumentos da cadeia de caracteres de modelo. O primeiro argumento é uma matriz de literais de cadeias de caracteres, delimitada pelas expressões de cadeia de caracteres de modelo que contém e o segundo argumento é uma matriz (uma [parâmetro Rest](../../javascript/functions-javascript.md)) que contém os valores das expressões de cadeia de caracteres de modelo.  
  
 No exemplo a seguir, a função de modelo marcada, buildURL é usado para construir uma URL. A sintaxe usa o nome da função seguido imediatamente pela cadeia de caracteres de modelo.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Se você precisar acessar os valores brutos da cadeia de caracteres passada, o primeiro argumento passado para a função de modelo marcado dá suporte a uma propriedade `raw` que retorna o formulário de cadeia de caracteres bruta das cadeias passadas.  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  Você também pode usar a função [String.raw](../../javascript/reference/string-raw-function-javascript.md) para retornar o formulário de cadeia de caracteres bruta de uma cadeia de caracteres de modelo.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de linguagem JavaScript](../../javascript/javascript-language-reference.md)   
 [JavaScript avançado](../../javascript/advanced/advanced-javascript.md)
