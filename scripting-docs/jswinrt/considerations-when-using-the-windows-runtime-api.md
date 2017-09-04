---
title: "Considerações ao usar a API do Windows Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime API
ms.assetid: 2f56d70c-c80d-4876-8e6a-8ae031d31c22
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: 693b3dac9def5533417638c3ec1c0de8db1d5fe3
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="considerations-when-using-the-windows-runtime-api"></a>Considerações ao usar a API do Windows Runtime
Você pode usar quase todos os elementos da API do Windows Runtime em JavaScript. No entanto, há alguns aspectos da representação dos elementos do Windows Runtime em JavaScript que você deve ter em mente.  
  
> [!IMPORTANT]
>  Para obter informações sobre como criar componentes do Windows Runtime em C++, C# ou Visual Basic e consumi-los em JavaScript, consulte [Criando componentes do Windows Runtime em C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) e [Criando componentes do Windows Runtime em C# e Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="special-cases-in-the-javascript-representation-of-windows-runtime-types"></a>Casos especiais na representação em JavaScript de tipos do Windows Runtime  
  
-   Cadeias de caracteres: uma cadeia de caracteres não inicializada é passada para um método do Windows Runtime como a cadeia de caracteres "undefined" e uma cadeia de caracteres definida como `null` é passada como a cadeia de caracteres "null". (Isso ocorre sempre que um valor `null` ou `undefined` é forçado para uma cadeia de caracteres.) Antes de você passar uma cadeia de caracteres para um método do Windows Runtime, você deve inicializá-lo como a cadeia de caracteres vazia ("").  
  
-   Interfaces: Você não pode implementar uma interface do Windows Runtime em JavaScript.  
  
-   Matrizes: matrizes do Windows Runtime não são redimensionáveis, então métodos que redimensionam matrizes em JavaScript não funcionam em matrizes do Windows Runtime.  
  
-   Matrizes: se você passar um valor de matriz de JavaScript para um método do Windows Runtime, a matriz será copiada. O método do Windows Runtime não é capaz de modificar a matriz ou seus membros e retorná-la ao seu aplicativo JavaScript. No entanto, você pode usar matrizes tipadas (por exemplo, [Objeto Int32Array](../javascript/reference/int32array-object.md)), que não são copiadas.  
  
-   Estruturas: estruturas do Windows Runtime são objetos em JavaScript. Se você quiser passar uma estrutura do Windows Runtime para um método do Windows Runtime, não instancie a estrutura com a palavra-chave `new`. Em vez disso, crie um objeto e adicione os membros relevantes e seus valores. Os nomes dos membros devem estar em minúsculas concatenadas: `SomeStruct.firstMember`.  
  
-   Objetos: objetos JavaScript não são o mesmo que objetos de código gerenciado (`System.Object`). Você não pode passar um objeto JavaScript para um método do Windows Runtime que requer um `System.Object`.  
  
-   Identidade do objeto: na maioria dos casos, os objetos passados bidirecionalmente entre o Windows Runtime e o JavaScript não são alterados. O mecanismo JavaScript mantém um mapa de objetos conhecidos. Quando um objeto é retornado do Windows Runtime, ele é comparado com o mapa e, se ele não existe, um novo objeto é criado. O mesmo procedimento é seguido para objetos que representam as interfaces que são retornadas pelos métodos do Windows Runtime. Há dois tipos de exceções:  
  
    -   Objetos que são retornados de uma chamada do Windows Runtime e, em seguida, têm novas propriedades (expando) adicionadas não mantêm suas novas propriedades quando eles são passados de volta para o Windows Runtime. No entanto, quando eles são retornados ao aplicativo JavaScript, já que eles são comparados ao objeto existente, o objeto retornado tem as propriedades expando.  
  
    -   Estruturas e delegados no Windows Runtime não podem ser identificados como idênticos a estruturas ou delegados usados anteriormente. Sempre que uma estrutura ou um delegado é retornado, ele obtém uma nova referência.  
  
-   Conflitos de nome: várias interfaces do Windows Runtime podem ter membros com os mesmos nomes. Se eles são combinados em um único objeto JavaScript (que pode ser uma representação de uma classe de tempo de execução ou uma interface), os membros são representados por nomes totalmente qualificados. Você pode chamar esses membros usando a seguinte sintaxe: `Class["MemberName"](parameter)`.  
  
     No código a seguir, duas interfaces têm um método Draw e uma classe de tempo de execução implementa ambas.  
  
    ```cpp#  
    namespace CollisionExample {  
        interface InterfaceA  
        {  
            HRESULT Draw([in] Int32 a);  
        }  
        interface InterfaceB  
        {  
            HRESULT Draw([in] HString a);  
        }  
        runtimeclass ExampleObject {  
          interface InterfaceA  
          interface InterfaceB  
        }  
    }  
    ```  
  
     Eis aqui como você pode chamar o código acima em JavaScript.  
  
    ```JavaScript  
    var example = new ExampleObject();  
    example["CollisionExample.InterfaceA.draw"](12);  
    example["CollisionExample.InterfaceB.draw"]("hello");  
    ```  
  
-   Parâmetros `Out`: se um método do Windows Runtime tem vários parâmetros `out`, em JavaScript esse método tem um objeto JavaScript como valor retornado e o objeto tem propriedades que correspondem ao parâmetro `out`. Por exemplo, considere a seguinte assinatura do Windows Runtime em C++.  
  
    ```cpp#  
    void ExampleMethod(  
      [OutAttribute] char^ first,   
      [OutAttribute] char^ second  
    )  
    ```  
  
     A versão do JavaScript desta assinatura é:  
  
    ```JavaScript  
    var returnValue = exampleMethod();  
  
    ```  
  
     Neste exemplo, `returnValue` é um objeto JavaScript que tem dois campos: `first` e `second`.  
  
-   Membros estáticos: o Windows Runtime define os membros estáticos e membros de instância. Em JavaScript, os membros estáticos são adicionados ao objeto que está associado com a interface ou classe do Windows Runtime.  
  
    ```JavaScript  
    // Static method.   
    var accel = Windows.Devices.Sensors.Accelerometer.getDefault();   
    // Instance method.   
    var reading = accel.getCurrentReading();            
    ```  
  
 Para obter mais informações sobre a representação dos tipos básicos do Windows Runtime em JavaScript, consulte [Representação em JavaScript de tipos do Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md).
