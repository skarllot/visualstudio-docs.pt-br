---
title: "Solução de problemas com scripts (JavaScript) | Microsoft Docs"
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
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="troubleshooting-your-scripts-javascript"></a>Solucionando problemas com scripts (JavaScript)
Em qualquer linguagem de programação, há locais que têm surpresas. Por exemplo, o valor `null` em [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] não tem o mesmo comportamento do valor `Null` nas linguagens C ou C++.  
  
 Aqui estão algumas das áreas problemáticas que você pode encontrar ao escrever scripts [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax-errors"></a>Erros de sintaxe  
 É importante prestar atenção aos detalhes ao escrever scripts. Por exemplo, cadeias de caracteres devem ser colocadas entre aspas.  
  
## <a name="order-of-script-interpretation"></a>Ordem de interpretação de Script  
 A interpretação de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] faz parte do processo de análise de HTML do seu navegador da Web. Se você colocar um script dentro da marca \<HEAD> em um documento, ele será interpretado antes de qualquer parte da marca \<BODY>. Se você tiver objetos criados na marca \<BODY>, eles não existirão no momento em que o \<HEAD> estiver sendo analisada e não poderão ser manipulados pelo script.  
  
> [!NOTE]
>  Esse comportamento é específico do Internet Explorer. ASP e WSH têm modelos de execução diferente (assim como outros hosts).  
  
## <a name="automatic-type-coercion"></a>Coerção de tipo automático  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] é uma linguagem fracamente tipada com coerção automática. Apesar de valores com tipos diferentes não serem iguais, as expressões no exemplo a seguir retornam **true**.  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 Para verificar se o tipo e o valor são os mesmos, use o operador de igualdade estrita (===). Ambos os exemplos a seguir retornam false:  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>Precedência do Operador  
 A [precedência do operador](../../javascript/operator-subtractprecedence-javascript.md) determina quando uma operação é executada durante a avaliação de uma expressão. No exemplo a seguir, a multiplicação é executada antes da subtração, embora a subtração apareça primeiro na expressão.  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>Usando loops for...in com objetos  
 Quando você itera pelas propriedades de um objeto com um loop [for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), você não pode prever nem controlar a ordem na qual os campos do objeto são atribuídos à variável de contador de loops. Além disso, a ordem pode ser diferente em diferentes implementações da linguagem.  
  
## <a name="with-keyword"></a>Palavra-chave with  
 A instrução [with](../../javascript/reference/with-statement-javascript.md) é prática para acessar as propriedades que já existem em um objeto especificado, mas não pode ser usada para adicionar propriedades a um objeto. Para criar novas propriedades em um objeto, você deve fazer referência ao objeto especificamente.  
  
## <a name="this-keyword"></a>Palavra-chave this  
 Embora você use a palavra-chave `this` dentro da definição de um objeto para fazer referência ao objeto em si, não é possível usar `this` ou palavras-chave semelhantes para referir-se à função atualmente em execução quando essa função não é uma definição de objeto. Se a função deve ser atribuída a um objeto como um método, você pode usar a palavra-chave `this` dentro da função para fazer referência ao objeto.  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>Escrevendo um script que escreve um script no Internet Explorer  
 A marca \</SCRIPT> encerra o script atual se encontrada pelo interpretador. Para exibir "\</SCRIPT>", reescreva-o como pelo menos duas cadeias de caracteres, por exemplo, "\</SCR" e "IPT>", que você pode, em seguida, concatenar juntas na instrução que as escreve.  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Referências de janela implícitas no Internet Explorer  
 Já que mais de uma janela pode ser aberta por vez, qualquer referência de janela implícita aponta para a janela atual. Para outras janelas, você deve usar uma referência explícita.
