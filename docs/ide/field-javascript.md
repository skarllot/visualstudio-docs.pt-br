---
title: "&lt; Campo &gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "< Campo > marca XML JavaScript"
  - "marca XML de campo JavaScript"
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt; Campo &gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica informações de documentação, incluindo uma descrição, para um campo ou membro que são definidos em um objeto.  
  
## Sintaxe  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### Parâmetros  
 `name`  
 O nome do campo ou membro.  Quando o elemento de `<field>` é usado em uma função de construtor, `name` é necessário e define o membro que a marca se aplica.  Quando o elemento de `<field>` está diretamente anotando um campo, esse atributo é ignorado, e o nome usado pelo Visual Studio é o nome do campo real no código\-fonte.  
  
 `static`  
 Opcional.  Especifica se o campo é um membro da função de construtor ou um membro objeto retornado pela função de construtor.  Definir a `true` para manipular o campo como um membro da função de construtor.  Definir a `false` para manipular o campo como um membro objeto retornado pela função de construtor.  
  
 `type`  
 Opcional.  O tipo de dados do campo.  O tipo pode ser um dos seguintes:  
  
-   Um idioma ECMAScript na especificação de ECMAScript 5, como `Number` e `Object`.  
  
-   O objeto DOM, como `HTMLElement`, `Window`, e `Document`.  
  
-   Uma função de construtor de JavaScript.  
  
 `integer`  
 Opcional.  Se `type` é `Number`, especifica se o campo é um número inteiro.  Defina a `true` para indicar que o campo é um inteiro; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `domElement`  
 Opcional.  Esse atributo é substituído; o atributo de `type` tem precedência sobre este atributo.  Esse atributo especifica se o campo documentado é um elemento DOM.  Defina a `true` para especificar que o campo é um elemento DOM; se não, defina a `false`.  Se o atributo de `type` não está definido e `domElement` é definido como `true`, o IntelliSense trata o campo documentado como `HTMLElement` ao executar a instrução.  
  
 `mayBeNull`  
 Opcional.  Especifica se o campo documentado pode ser definido como nulo.  Defina a `true` para indicar que o campo pode ser definido como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementType`  
 Opcional.  Se `type` é `Array`, esse atributo especifica o tipo dos elementos da matriz.  
  
 `elementInteger`  
 Opcional.  Se `type` é `Array` e `elementType` é `Number`, esse atributo especifica se os elementos na matriz são números inteiros.  Defina a `true` para indicar que os elementos na matriz são números inteiros; se não, defina a `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `elementDomElement`  
 Opcional.  Esse atributo é substituído; o atributo de `elementType` tem precedência sobre este atributo.  Se `type` é `Array`, esse atributo especifica se os elementos na matriz são elementos DOM.  Defina a `true` para especificar que os elementos são elementos DOM; se não, defina a `false`.  Se o atributo de `elementType` não está definido e `elementDomElement` é definido como `true`, o IntelliSense trata cada elemento na matriz como `HTMLElement` ao executar a instrução.  
  
 `elementMayBeNull`  
 Opcional.  Se `type` é `Array`, especifica se os elementos na matriz podem ser definidos como nulo.  Defina a `true` para indicar que os elementos na matriz podem ser definidos como nulo; se não, defina a `false`.  O valor padrão é `false`.  Este atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
 `helpKeyword`  
 Opcional.  A palavra\-chave para F1 ajuda.  
  
 `locid`  
 Opcional.  O identificador para informações de localização no campo.  O identificador é ou um ID do membro ou corresponde ao valor do atributo de `name` em um pacote de mensagem definida por metadados de OpenAjax.  O tipo identificador depende de formato especificado na marca de [\< loc \>](../ide/loc-javascript.md) .  
  
 `value`  
 Opcional.  Especifica o código que deve ser avaliado para o uso do IntelliSense em vez de código de função próprio.  Para `<field>`, esse atributo é suportado para funções de construtor, mas não suportado para literais de objeto.  Você pode usar este atributo deve fornecer informações de tipo quando o tipo de campo é indefinido.  Por exemplo, você pode usar `value=’1’` para manipular o tipo do campo como um número.  
  
 `description`  
 Opcional.  Uma descrição para o campo.  
  
## Comentários  
 O atributo de `name` é necessário quando você estiver documentando um campo em uma função de construtor.  Para todos outros cenários, todos os atributos para o elemento de `<field>` são opcionais.  
  
 Quando você estiver documentando uma função de construtor, o elemento de `<field>` deve aparecer imediatamente antes da declaração do campo.  O atributo de `name` deve corresponder ao nome do campo que é usado no código\-fonte.  Para membros de objeto, o atributo de `name` pode ser omitido se o elemento de `<field>` aparece imediatamente antes da declaração de membro de objeto.  
  
## Exemplo  
 O exemplo de código a seguir mostra como usar o elemento de `<field>` .  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## Exemplo  
 O exemplo a seguir mostra como usar o elemento de `<field>` com o atributo de `static` definido como `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## Exemplo  
 O exemplo a seguir mostra como usar o elemento de `<field>` com o atributo de `static` definido como `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## Exemplo  
 O exemplo a seguir mostra como usar o elemento de `<field>` com o atributo de `value` .  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)