---
title: "Protótipos e herança de protótipos | Microsoft Docs"
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
- prototype [JavaScript]
- prototype inheritance [JavaScript]
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: ade60bcbbfad166bae18b650daa6906f9983d4cd
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="prototypes-and-prototype-inheritance"></a>Protótipos e herança de protótipos
Em JavaScript, um `prototype` é uma propriedade de funções e de objetos que são criados por funções de construtor. O protótipo de uma função é um objeto. Seu principal uso é quando uma função é usada como um construtor.  
  
```JavaScript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 No exemplo anterior, o protótipo da função `Vehicle` é o protótipo de qualquer objeto instanciado com o construtor `Vehicle`.  
  
## <a name="using-prototypes-to-add-properties-and-methods"></a>Usando protótipos para adicionar propriedades e métodos  
 Você pode usar a propriedade `prototype` para adicionar propriedades e métodos a objetos, mesmo aqueles que já foram criados:  
  
```JavaScript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 O valor de `testColor` é "red" (vermelho).  
  
 Você pode até mesmo adicionar propriedades e métodos a objetos predefinidos. Por exemplo, você pode definir um método `Trim` no objeto de protótipo `String`, e todas as cadeias de caracteres no seu script herdarão esse método.  
  
```JavaScript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### <a name="using-prototypes-to-derive-one-object-from-another-with-objectcreate"></a>Usando protótipos para derivar um objeto de outro com Object.create  

O protótipo `Object` pode ser usado para derivar um objeto de outro. Por exemplo, você pode usar a função [Object.create](../../javascript/reference/object-create-function-javascript.md) para derivar um novo objeto `Bicycle` usando o protótipo do objeto `Vehicle` que definimos anteriormente (além de qualquer nova propriedade necessária).  
  
```JavaScript  
var bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 O objeto `bicycle` possui as propriedades `wheels`, `engine`, `color` e `pedals`, e seu protótipo é `Vehicle.prototype`. O mecanismo de JavaScript localiza a propriedade `pedals` em `bicycle` e pesquisa a cadeia de protótipos para localizar `wheels`, `engine` e as propriedades `color` em `Vehicle`.  
  
### <a name="changing-an-objects-prototype"></a>Alterando o protótipo de um objeto  
 No Internet Explorer 11, você pode substituir o protótipo interno de um objeto ou função por um novo protótipo usando a propriedade [__proto\_\_](../../javascript/reference/proto-property-object-javascript.md). Ao usar essa propriedade, você herda as propriedades e os métodos do novo protótipo, junto com outras propriedades e métodos em sua cadeia de protótipos.  
  
 O exemplo a seguir mostra como você pode alterar o protótipo de um objeto. Este exemplo mostra como as propriedades herdadas do objeto mudam quando você altera seu protótipo.  
  
```JavaScript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```

