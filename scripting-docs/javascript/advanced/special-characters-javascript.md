---
title: Caracteres especiais (JavaScript) | Microsoft Docs
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
- line terminator character
- white space character
- Unicode character
- escape sequence
- backslash (\)
ms.assetid: 3b38b1bd-1f0f-4748-b13e-55cab36fd126
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 066b83e7457dd630b1aa59cba83d0dec6a84631c
ms.openlocfilehash: 0eaae8dfc84d9a3be6db54c50558d4cf675a53a8
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="special-characters-javascript"></a>Caracteres especiais (JavaScript)
O [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fornece sequências de escape que você pode incluir em cadeias de caracteres para criar caracteres que não podem ser digitados diretamente.  
  
## <a name="remarks"></a>Comentários  
 Um valor de cadeia de caracteres é uma série de zero ou mais caracteres Unicode (letras, dígitos e outros caracteres). Literais de cadeia de caracteres são colocados entre pares correspondentes de aspas simples ou duplas. Aspas duplas podem estar contidas em uma cadeia de caracteres delimitada por aspas simples. Aspas simples podem estar contidas em uma cadeia de caracteres delimitada por aspas duplas.  
  
 Cada caractere em um literal de cadeia de caracteres pode ser representado por uma sequência de escape. Uma sequência de escape começa com uma barra invertida (\\) que informa ao interpretador [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que o próximo caractere é um caractere especial.  
  
 Você pode especificar um caractere Unicode usando a sequência de escape \u*hhhh*, em que *hhhh* é um número hexadecimal de quatro dígitos. Uma sequência de escape Unicode pode representar qualquer caractere de 16 bits. Para obter informações adicionais, consulte [Sequências de escape de ponto de código Unicode](#CodePoint).  
  
 Você pode usar uma sequência de escape de caractere único para alguns caracteres. Por exemplo, \t especifica um caractere de tabulação.  
  
## <a name="escape-sequences"></a>Sequências de Escape  
 A tabela a seguir lista alguns exemplos de sequências de escape para caracteres comuns.  
  
|Valor de caractere Unicode|Sequência de escape|Significado|Categoria|  
|-----------------------------|---------------------|-------------|--------------|  
|\u0008|\b|Backspace||  
|\u0009|\t|Tabulação|Espaço em branco|  
|\u000A|\n|Alimentação de linha (nova linha)|Terminador de linha|  
|\u000B|\v<br /><br /> (Consulte a observação após esta tabela.)|Tabulação vertical|Espaço em branco|  
|\u000C|\f|Avanço de página|Espaço em branco|  
|\u000D|\r|Retorno de carro|Terminador de linha|  
|\u0020||Espaço|Espaço em branco|  
|\u0022|\\"|Aspas duplas (")||  
|\u0027|\\'|Aspas simples (')||  
|\u005C|\\\|Barra invertida (\\)||  
|\u00A0||Espaço incondicional|Espaço em branco|  
|\u2028||Separador de linha|Terminador de linha|  
|\u2029||Separador de parágrafo|Terminador de linha|  
|\uFEFF||Marca de ordem de byte|Espaço em branco|  
  
 A coluna de Categoria especifica se o caractere é um caractere de espaço em branco ou terminador de linha. O [método trim (cadeia de caracteres)](../../javascript/reference/trim-method-string-javascript.md) remove os espaços em branco inicial e final e também os caracteres de terminação de linha de uma cadeia de caracteres.  
  
 A barra invertida é usada como o caractere de escape. Portanto, você não pode digitar uma diretamente em seu script. Se quiser incluir uma barra invertida, você deverá digitar duas delas juntas (\\\\).  
  
> [!NOTE]
>  A partir do [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)], você não pode identificar o navegador como Internet Explorer testando a equivalência da barra vertical (\v) e do "v". Em versões anteriores, a expressão `"\v" === "v"` retorna `true`. Em [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)], a expressão retorna `false`.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir demonstra as sequências de escape \\\ e \\'.  
  
### <a name="code"></a>Código  
  
```JavaScript  
document.write('The image path is C:\\webstuff\\mypage\\gifs\\garden.gif.');  
document.write ("<br />");  
document.write('The caption reads, "After the snow of \'97. Grandma\'s house is covered."');  
```  
  
<a name="CodePoint"></a>   
## <a name="unicode-code-point-escape-sequences"></a>Sequências de escape de ponto de código Unicode  
 No [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], o Unicode tem suporte total. Os pontos de código Unicode mais comuns são representados por quatro dígitos hexadecimais, como /u0009 para um caractere de tabulação. Agora há suporte para pontos de código Astral, que incluem todos os símbolos que exigem mais de quatro dígitos hexadecimais, em um formato simplificado. Usando o formato "\u{*codepoint*}", o conjunto de caracteres Unicode completo pode ser representado em um formato literal. Por exemplo, para representar o símbolo "𠮷", você pode usar o seguinte formato: "\u{20BB7}".  
  
 No exemplo de código a seguir, as cadeias de caracteres são todas equivalentes. (\uD842\uDFB7 é o método de solução alternativa para especificar esse símbolo em versões anteriores.)  
  
```JavaScript  
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"  
```  
  
 RegExp agora inclui um sinalizador /u para habilitar o suporte completo para pontos de código astral. Por exemplo, no exemplo de código a seguir, o sinalizador /u na expressão regular habilita a correspondência de pontos de código astral (o ponto corresponde a qualquer caractere na cadeia de caracteres fornecida).  
  
```JavaScript  
"𠮷".match(/./u)[0].length == 2  
```  
  
 O sinalizador /u habilita a análise do novo formato, \u{codepoint}), como uma sequência de escape Unicode. Isso é necessário porque \u{xxxxx} sem o sinalizador /u tem um significado diferente em uma expressão regular.  
  
> [!NOTE]
>  Para pontos de código astral, o comprimento sempre é 2. Isso coincide com o comportamento de versões anteriores.  
  
 O objeto de Cadeia de Caracteres agora inclui dois novos métodos, String.codePointAt e String.fromCodePoint, para dar suporte a pontos de código astral. Por exemplo, você pode usar codePointAt para retornar o ponto de código equivalente ao símbolo "𠮷".  
  
```JavaScript  
"𠮷".codePointAt(0) == 0x20BB7  
  
```  
  
 Também é possível iterar pontos de código usando a instrução `for...of`.  
  
```JavaScript  
for(var c of "𠮷") {  
    console.log(c);  
}  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Função String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)
