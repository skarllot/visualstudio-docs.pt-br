---
title: Copiando, transmitindo e comparando dados (JavaScript) | Microsoft Docs
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
- arrays [Visual Studio], passing values
- function parameters
- string comparison
- function parameters, about function parameters
- ByRef argument
- arrays [Visual Studio], setting data types
- arrays [Visual Studio], copying data
- ByVal argument
- string comparison, testing data
ms.assetid: fbccd877-7249-45d4-bd9f-6bcd8ba94a6b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: c3cf980ca1dfd0c0e09871b6de9756cb2a10364b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="copying-passing-and-comparing-data-javascript"></a>Copiando, transmitindo e comparando dados (JavaScript)
No [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], a maneira como os dados são identificados depende do tipo de dados.  
  
## <a name="by-value-vs-by-reference"></a>Por valor vs. Por referência  
 Números e valores boolianos (**true** e **false**) são copiados, passados e comparados *por valor*. Ao copiar ou passar por valor, você aloca um espaço na memória do computador e copia o valor do original para ele. Se você alterar o original, a cópia não será afetada (e vice-versa), pois os dois são entidades distintas.  
  
 Objetos, matrizes e funções são copiados, passados e comparados *por referência*. Ao copiar ou transmitir por referência, você cria essencialmente um ponteiro para o item original e usa o ponteiro como se ele fosse uma cópia. Se alterar o original, você irá alterar o original e a cópia (e vice-versa). Existe, na verdade, apenas uma entidade. A "cópia" não é realmente uma cópia, e sim apenas outra referência aos dados.  
  
 Durante a comparação por referência, as duas variáveis devem referenciar exatamente a mesma entidade para que a comparação seja bem-sucedida. Por exemplo, dois objetos **Array** distintos sempre serão comparados como diferentes, mesmo que contenham os mesmos elementos. Uma das variáveis deve ser uma referência para outra para que a comparação seja bem-sucedida. Para verificar se dois objetos Array contêm os mesmos elementos, compare os resultados do método **toString()**.  
  
 Por último, cadeias de caracteres são copiadas e passadas por referência, mas são comparadas por valor. Se você tiver dois objetos **String** (criados com **new** String("algo")), eles serão comparados por referência, mas, se um ou ambos os valores for um valor de cadeia de caracteres, eles serão comparados por valor.  
  
> [!NOTE]
>  Por causa da maneira como conjuntos de caracteres ASCII e ANSI são construídos, letras maiúsculas precedem letras minúsculas em uma ordem sequencial. Por exemplo, "Zoo" é comparado como *menor* que "aardvark". É possível chamar **toUpperCase()** ou **toLowerCase()** em ambas as cadeias de caracteres caso você queira realizar uma correspondência sem distinção entre maiúsculas e minúsculas.  
  
## <a name="passing-parameters-to-functions"></a>Passando parâmetros para funções  
 Ao passar um parâmetro para uma função por valor, você está fazendo uma cópia separada desse parâmetro: uma cópia que existe somente dentro da função. Embora objetos e matrizes sejam transmitidos por referência, se você substituí-los diretamente por um novo valor na função, o novo valor não será refletido fora da função. Somente as alterações feitas em propriedades de objetos, ou elementos de matrizes, são visíveis fora da função.  
  
 Por exemplo (usando o modelo de objeto do Internet Explorer):  
  
```JavaScript  
// This clobbers (over-writes) its parameter, so the change  
// is not reflected in the calling code.  
function Clobber(param)   
{  
    // clobber the parameter; this will not be seen in   
    // the calling code  
    param = new Object();  
    param.message = "This will not work";  
}  
  
// This modifies a property of the parameter, which  
// can be seen in the calling code.  
function Update(param)  
{  
    // Modify the property of the object; this will be seen  
    // in the calling code.  
    param.message = "I was changed";  
}  
  
// Create an object, and give it a property.  
var obj = new Object();  
obj.message = "This is the original";  
  
// Call Clobber, and print obj.message. Note that it hasn't changed.  
Clobber(obj);  
window.alert(obj.message); // Still displays "This is the original".  
  
// Call Update, and print obj.message. Note that is has changed.  
Update(obj);  
window.alert(obj.message); // Displays "I was changed".  
```  
  
## <a name="testing-data"></a>Testando dados  
 Ao realizar um teste por valor, você compara dois itens distintos para ver se eles são iguais entre si. Normalmente, essa comparação é realizada byte por byte. Ao testar por referência, você está verificando se dois itens são ponteiros para um único item original. Se esse for o caso, eles serão comparados como iguais. Caso contrário, mesmo contendo os mesmos valores, byte por byte, eles serão comparados como diferentes.  
  
 Copiar e passar cadeias de caracteres por referência economiza memória. Porém, como você não pode alterar cadeias de caracteres depois de criadas, é possível compará-las por valor. Isso permite testar se duas cadeias de caracteres têm o mesmo conteúdo, mesmo que uma delas tenha sido gerada totalmente separada da outra.  
  
## <a name="see-also"></a>Consulte também  
 [Calcular datas e horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)
