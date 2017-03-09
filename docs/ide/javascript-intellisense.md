---
title: JavaScript IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
author: mikejo
ms.author: mikejo
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: d07820eda0d76163d99d7752789750eaf56182fd
ms.openlocfilehash: 1f8372fe201d6b23ee2c65e0f6d6a2fa28976654
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
O [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] fornece uma experiência de edição de JavaScript avançada pronta para o uso. Ativado por um serviço de linguagem baseado no TypeScript, o Visual Studio oferece um IntelliSense mais sofisticado, suporte para recursos modernos do JavaScript e recursos aprimorados de produtividade como Ir para Definição, refatoração e muito mais.

> [!NOTE]
>  O serviço de linguagem JavaScript do [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] usa um novo mecanismo para o serviço de linguagem (“salsa”). Os detalhes estão incluídos aqui neste tópico, e talvez você deseje ler esta [postagem no blog](https://blogs.msdn.microsoft.com/visualstudio/2016/04/08/previewing-salsa-javascript-language-service-visual-studio-15/). A nova experiência de edição também aplica-se principalmente no Código do VS. Consulte os [documentos do Código do VS](https://code.visualstudio.com/docs/languages/javascript) para obter mais informações.

Para obter mais informações sobre a funcionalidade geral [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] do IntelliSense, consulte [Usando o IntelliSense](../ide/using-intellisense.md). 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>Novidades no serviço de linguagem JavaScript do [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

- IntelliSense mais sofisticado

    O JavaScript IntelliSense do [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] agora exibirá muito mais informações sobre listas de parâmetro e de membro.
Essas novas informações são fornecidas pelo serviço de linguagem TypeScript, que usa a análise estática nos bastidores para entender melhor o código.
O TypeScript usa várias fontes para criar essas informações.
    - [IntelliSense baseado na inferência de tipos](#TypeInference)
    - [IntelliSense baseado no JSDoc](#JsDoc)
    - [IntelliSense baseado em arquivos de declaração do TypeScript](#TSDeclFiles)

- [Aquisição automática de definições de tipo](#Auto)
- [Suporte para ES6 e outros](#ES6)
- [Suporte à sintaxe JSX](#JSX)

## <a name="TypeInference"></a>IntelliSense baseado na inferência de tipos
No JavaScript, na maioria das vezes, não há nenhuma informação de tipo explícita disponível. Felizmente, em geral, é bem fácil deduzir um tipo considerando o contexto de código ao redor.
Esse processo é chamado de inferência de tipos.

Para uma variável ou uma propriedade, em geral, o tipo é o tipo do valor usado para inicializá-lo ou a atribuição de valor mais recente. 

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Para uma função, o tipo de retorno pode ser inferido de instruções de returno. 

Para parâmetros de função, atualmente, não há nenhuma inferência, mas existem maneiras de resolver esse problema usando o JSDoc ou arquivos `.d.ts` TypeScript (consulte as próximas seções).

Além disso, há uma inferência especial para o seguinte:
 - Classes de “estilo ES3”, especificadas usando uma função de construtor e atribuições à propriedade de protótipo.
 - Padrões de módulo de estilo CommonJS, especificados como atribuições de propriedade no objeto `exports` ou atribuições à propriedade `module.exports`.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

## <a name="JsDoc"></a> IntelliSense baseado no JSDoc

Nos casos em que a inferência de tipos não fornecer as informações de tipo desejadas (ou para dar suporte à documentação), as informações de tipo podem ser fornecidas explicitamente por meio de anotações do JSDoc.  Por exemplo, para fornecer um tipo específico a um objeto parcialmente declarado, é possível usar a marcação `@type` conforme mostrado abaixo:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Conforme mencionado, os parâmetros de função nunca são inferidos. No entanto, usando a marcação `@param` do JSDoc, é possível adicionar tipos a parâmetros de função também. 

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```
 
Consulte [este documento](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) para obter as anotações do JsDoc com suporte no momento.

## <a name="TsDeclFiles"></a> IntelliSense baseado em arquivos de declaração do TypeScript

Como o JavaScript e o TypeScript agora são baseados no mesmo serviço de linguagem, eles podem interagir de forma mais sofisticada. Por exemplo, o JavaScript IntelliSense pode ser fornecido para valores declarados em um arquivo `.d.ts` ([mais informações](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md)), e tipos como interfaces e classes declaradas no TypeScript estão disponíveis para uso como tipos em comentários do JsDoc. 

Abaixo, mostramos um exemplo simples de um arquivo de definição do TypeScript que fornece essas informações de tipo (por meio de uma interface) para um arquivo JavaScript no mesmo projeto (usando uma marcação do JsDoc).

_**Declarações do TypeScript usadas no JavaScript**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

## <a name="Auto"></a> Aquisição automática de definições de tipo
No mundo do TypeScript, as bibliotecas mais populares do JavaScript têm suas APIs descritas por arquivos `.d.ts` e o repositório mais comum dessas definições está em [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Por padrão, o serviço de linguagem Salsa tentará detectar quais bibliotecas do JavaScript estão em uso e baixará e referenciará automaticamente o arquivo `.d.ts` correspondente que descreve a biblioteca, a fim de fornecer um IntelliSense mais sofisticado. Os arquivos são baixados em um cache localizado na pasta do usuário em `%LOCALAPPDATA%\Microsoft\TypeScript`. 

> [!NOTE]
> Esse recurso estará **desabilitado** por padrão se um arquivo de configuração `tsconfig.json` estiver sendo usado, mas poderá ser definido como habilitado, conforme descrito mais abaixo.

Atualmente, a detecção automática funciona para dependências baixadas no npm (com a leitura do arquivo `package.json`), no Bower (com a leitura do arquivo `bower.json`) e em arquivos soltos no projeto que correspondem a uma lista de aproximadamente as 400 bibliotecas mais populares do JavaScript. Por exemplo, se você tiver `jquery-1.10.min.js` no projeto, o arquivo `jquery.d.ts` será buscado e carregado para proporcionar uma melhor experiência de edição. Esse arquivo `.d.ts` não afetará o projeto. 

Se você não desejar usar a aquisição automática, desabilite-a adicionando um arquivo de configuração, conforme descrito abaixo. Ainda é possível colocar arquivos de definição para uso diretamente no projeto manualmente.

## <a name="ES6"></a> Suporte para ES6 e outros

O ES6, ou o ECMAScript 2015, é a próxima versão do JavaScript. Ele leva uma nova sintaxe à linguagem, como classes, funções de seta, `let`/`const` e muito mais. Toda essa nova sintaxe tem suporte no Visual Studio.

Um dos principais recursos que o TypeScript fornece é a capacidade de usar os recursos do ES6, além de emitir código que pode ser executado em tempos de execução do JavaScript que ainda não entende os recursos mais novos. Isso é normalmente conhecido como “transpiling”. Como o JavaScript usa o mesmo serviço de linguagem, ele também pode aproveitar o ES6+ para executar transpilation do ES5.

Antes que isso possa ser configurado, são necessárias algumas noções básicas sobre as opções de configuração.  O TypeScript é configurado por meio de um arquivo `tsconfig.json`. Na ausência desse arquivo, alguns valores padrão são usados. Por motivos de compatibilidade, esses padrões são diferentes em um contexto em que apenas arquivos JavaScript (e, opcionalmente, arquivos `.d.ts`) estão presentes. Para compilar arquivos JavaScript, um arquivo `tsconfig.json` deve ser adicionado, e alguns desses padrões devem ser definidos explicitamente.

As configurações necessárias para o arquivo tsconfig são descritas abaixo:

 - `allowJs`: esse valor deve ser definido como `true` para que os arquivos JavaScript sejam reconhecidos.
Por padrão, isso é `false`, pois o TypeScript é compilado para o JavaScript, e isso é necessário para evitar que o compilador inclua arquivos que ele acabou de compilar.
 - `outDir`: isso deve ser definido com um local não incluído no projeto, para que os arquivos JavaScript emitidos não sejam detectados e então incluídos no projeto (consulte `exclude` abaixo).
 - `module`: se estiver usando módulos, essa configuração informará ao compilador qual formato de módulo o código emitido deverá usar (por exemplo, `commonjs` para o Nó ou agregadores como Browserify).
 - `exclude`: essa configuração indica quais pastas não serão incluídas no projeto. 
 O local de saída, bem como pastas não pertencentes ao projeto como `node_modules` ou `temp`, devem ser adicionados a essa configuração.
 - `enableAutoDiscovery`: essa configuração habilita a detecção automática e o download de arquivos de definição, conforme descrito acima.
 - `compileOnSave`: essa configuração informa ao compilador se ele deve recompilar sempre que um arquivo de origem é salvo no Visual Studio.

Para converter arquivos JavaScript em módulos CommonJS em uma pasta `./out`, configurações semelhantes às mostradas abaixo podem ser incluídas em um arquivo `tsconfig.json`.

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typingOptions": {
    "enableAutoDiscovery": true
  }
}
```

Com as configurações acima em vigor, se houver um arquivo de origem (`./app.js`) que contém vários recursos da linguagem ECMAScript 2015, conforme mostrado abaixo:

```js
import {Subscription} from 'rxjs/Subscription';

class Foo {
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;
    }
}

export let sqr = x => x * x;
export default Subscription;
```

Um arquivo será emitido para o `./out/app.js` que tem o ECMAScript 5 como destino (o padrão), semelhante ao exemplo mostrado abaixo:

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
//# sourceMappingURL=app.js.map
```

## <a name="JSX"></a> Suporte à sintaxe JSX

O JavaScript no Visual Studio 2017 conta com suporte avançado à sintaxe JSX. O JSX é um conjunto de sintaxes que permite marcas HTML em arquivos JavaScript. 

A ilustração abaixo mostra um componente React definido no arquivo TypeScript `comps.tsx` e, em seguida, esse componente sendo usado no arquivo `app.jsx`, completo com o IntelliSense para conclusões e documentação nas expressões JSX.
Você não precisa do TypeScript aqui; esse exemplo específico eventualmente também contém algum código TypeScript.
<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/react.png" height="500" width="640"/>

> [!NOTE]
> Para converter a sintaxe JSX em chamadas React, a configuração `"jsx": "react"` deve ser adicionada ao `compilerOptions` no arquivo `tsconfig.json` descrito acima.

O arquivo JavaScript criado em “./out/app.js” após o build conterá o código:

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

