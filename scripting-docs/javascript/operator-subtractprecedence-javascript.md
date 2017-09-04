---
title: "Precedência do operador (JavaScript) | Microsoft Docs"
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
- operator precedence
- order of precedence
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 82503a312a4a4996e3bd38f596eef3104af3f11b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="operator-precedence-javascript"></a>Precedência do operador (JavaScript)
A precedência dos operadores descreve a ordem em que as operações são realizadas quando uma expressão é avaliada. As operações com uma precedência maior são realizadas antes daquelas com precedência menor. Por exemplo, a multiplicação é realizada antes da adição.  
  
## <a name="includejavascriptjavascriptincludesjavascript-mdmd-operators"></a>Operadores [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
 A tabela a seguir lista os operadores [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ordenados da maior para a menor precedência. Operadores com a mesma precedência são avaliados da esquerda para a direita.  
  
|Operador|Descrição|  
|--------------|-----------------|  
|. [ ] ( )|Acesso a campos, indexação de matrizes, chamadas de funções e agrupamento de expressões|  
|++ -- - ~ ! delete new typeof void|Operadores unários, tipo de dados de retorno, criação de objetos, valores indefinidos|  
|* / %|Multiplicação, divisão, divisão de módulo|  
|+ - +|Adição, subtração, concatenação de cadeias de caracteres|  
|<\< >> >>>|Deslocamento de bits|  
|< \<= > >= instanceof|Menor que, menor que ou igual a, maior que, maior que ou igual a, instância de|  
|== != === !==|Igualdade, desigualdade, igualdade estrita e desigualdade estrita|  
|&|AND bit a bit|  
|^|XOR bit a bit|  
|&#124;|OR bit a bit|  
|&&|AND lógico|  
|&#124;&#124;|OR lógico|  
|?:|Condicional|  
|= *OP*=|Atribuição, atribuição com operação (como += e &=)|  
|,|Avaliação múltipla|  
  
 Os parênteses são usados para alterar a ordem de avaliação determinada pela precedência dos operadores. Isso significa que uma expressão entre parênteses é totalmente avaliada antes que o seu valor seja usado no restante da expressão.  
  
 Por exemplo:  
  
```JavaScript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 Há três operadores na primeira expressão: =, * e +. De acordo com as regras de precedência de operadores, eles são avaliados na seguinte ordem: \*, +, = (78 \* 96 = 7488, 7488 + 3 = 7491).  
  
 Na segunda expressão, o operador ( ) é avaliado primeiro, de modo que a expressão de adição é avaliada antes da multiplicação (9 + 3 = 12, 12 * 78 = 936).  
  
 O exemplo a seguir mostra uma instrução que inclui uma variedade de operadores e é resolvida como `true`.  
  
```JavaScript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 Os operadores são avaliados nesta ordem: () para o agrupamento, *, + (dentro de agrupamento), "." para a função, () para a função, /, ==, ===, e &&.
