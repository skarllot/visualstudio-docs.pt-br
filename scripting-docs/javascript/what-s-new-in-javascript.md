---
title: Novidades no JavaScript | Microsoft Docs
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
ms.assetid: 342b68ef-df93-48c4-81de-bdf6b6ce58d9
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 540d10958a7f2d406a6d70a633fc09a2cada8f41
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="what39s-new-in-javascript"></a>Novidades no JavaScript
Este documento lista os novos recursos do JavaScript que são compatíveis com o [modo de Borda](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx), [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] e aplicativos da Windows Phone Store.  
  
 Para saber quais elementos JavaScript são compatíveis com o modo de Borda mas preteridos nos aplicativos [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)], confira [Informações de Versão](../javascript/reference/javascript-version-information.md).  
  
> [!IMPORTANT]
>  Para saber mais sobre como criar aplicativos da [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] e Windows Phone Store usando JavaScript, incluindo informações sobre o editor de JavaScript do Visual Studio e outros recursos, confira [Desenvolver aplicativos da Windows Store usando o Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkID=238263).  
  
## <a name="new-features-in-javascript"></a>Novos recursos no JavaScript  
  
|Recurso|Descrição|  
|-------------|-----------------|  
|Classes|A nova sintaxe dá suporte a declaração de [classes](../javascript/reference/class-statement-javascript.md).|  
|Promises|[Promises](../javascript/reference/promise-object-javascript.md) permitem codificação assíncrona mais fácil e limpa. Construtores Promise têm suporte, juntamente com os métodos de utilitário `all` e `race`.|  
|Iteradores|Agora você pode iterar pelos objetos que permitem iteração (incluindo matrizes, objetos de tipo matriz e iteradores), invocando um gancho de iteração personalizado com as instruções a serem executadas para o valor de cada propriedade distinta. Para obter mais informações, consulte [Iteradores e geradores](../javascript/advanced/iterators-and-generators-javascript.md). **Observação:** ainda não há suporte para geradores.|  
|Funções de seta|A função de seta (=>) fornece uma sintaxe abreviada para a palavra-chave `function`, que apresenta uma associação `this` léxica.|  
|Novos métodos para objetos internos|Os objetos internos [Array](../javascript/reference/array-object-javascript.md), [Math](../javascript/reference/math-object-javascript.md), [Number](../javascript/reference/number-object-javascript.md), [Object](../javascript/reference/object-object-javascript.md) e [String](../javascript/reference/string-object-javascript.md) incluem muitas novas propriedades e funções de utilitário para manipular e inspecionar dados.|  
|Aprimoramentos de literal de objeto|Os objetos agora dão suporte a propriedades computadas, definições de método concisas e sintaxe abreviada para propriedades cujo valor é inicializado com uma variável de mesmo nome. Para obter mais informações, consulte [Criando objetos](../javascript/creating-objects-javascript.md).|  
|Proxies|[Proxies](../javascript/reference/proxy-object-javascript.md) habilitam o comportamento personalizado para objetos.|  
|Parâmetros Rest|Parâmetros Rest permitem que você transforme argumentos consecutivos em uma chamada de função para uma matriz. Para obter mais informações, consulte [Funções](../javascript/functions-javascript.md).|  
|Operador de espalhamento|O [operador de espalhamento](../javascript/reference/spread-operator-decrement-dot-dot-dot-javascript.md) (`...`) expande expressões que podem ser iteradas, transformando-as em argumentos individuais. Por exemplo, `a.b(...array)` é aproximadamente o mesmo que `a.b.apply(a, array)`.|  
|Símbolos|Os objetos [Symbol](../javascript/reference/symbol-object-javascript.md) permitem que sejam adicionadas propriedades aos objetos existentes sem a possibilidade de interferência com as propriedades do objeto existente, sem nenhuma visibilidade não intencional e sem outras adições não coordenadas por outro código.|  
|Cadeias de caracteres de modelo|[Cadeias de caracteres de modelo](../javascript/advanced/template-strings-javascript.md) são literais de cadeia de caracteres que permitem que expressões sejam avaliadas e concatenadas com o literal de cadeia de caracteres.|  
|Aprimoramentos Unicode|Foram feitos aperfeiçoamentos ao suporte a Unicode. Por exemplo, um novo formato de sequência de escape dá suporte a pontos de código astral (pontos de código com mais de quatro dígitos hexadecimais). Para obter mais informações, consulte [Caracteres especiais](../javascript/advanced/special-characters-javascript.md).|  
|WeakSet|Um [WeakSet](../javascript/reference/weakset-object-javascript.md) será uma coleção de objetos que serão removidos pela coleta de lixo se não forem referenciados em nenhum outro lugar.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de linguagem JavaScript](../javascript/javascript-language-reference.md)
