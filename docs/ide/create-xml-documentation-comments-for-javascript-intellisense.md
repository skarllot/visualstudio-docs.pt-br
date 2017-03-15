---
title: "Como criar coment&#225;rios de documenta&#231;&#227;o XML JavaScript | Microsoft Docs"
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
  - "comentários de código, JavaScript IntelliSense"
  - "comentários de documentação [JavaScript]"
  - "IntelliSense [JavaScript], Comentários de documentação XML"
  - "Comentários de documentação XML, JavaScript IntelliSense"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Como criar coment&#225;rios de documenta&#231;&#227;o XML JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Comentários de documentação XML* são comentários de JavaScript que você adicione um script para fornecer informações sobre elementos de código como, por exemplo, funções, campos e variáveis.  No Visual Studio, essas descrições de texto são exibidas com IntelliSense quando você faz referência a função de script.  
  
 Este tópico fornece um tutorial básico sobre o uso de comentários de documentação XML.  Para obter informações sobre o uso de outros elementos, como [\< var \>](../ide/var-javascript.md) e [\< valor \>](../ide/value-javascript.md)e exemplos de código adicionais, consulte [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md).  Para informações sobre como fornecer informações de IntelliSense para um retorno de chamada assíncrono, como um `Promise`, consulte [\< retorna \>](../ide/returns-javascript.md).  
  
> [!NOTE]
>  Comentários de documentação XML estão disponíveis somente em serviços, assemblies e arquivos referenciados.  
  
### Criar comentários de documentação XML para uma função JavaScript  
  
-   Adicione a função [\< resumo \>](../ide/summary-javascript.md), [\< param \>](../ide/param-javascript.md), e [\< retorna \>](../ide/returns-javascript.md) elementos e preceder cada elemento com três barras \(\/ \/ \/\).  
  
    > [!NOTE]
    >  Cada elemento deve ser em uma única linha.  
  
     O exemplo a seguir mostra uma função JavaScript.  
  
    ```javascript  
    function getArea(radius)  
    {  
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>  
        /// <param name="radius" type="Number">The radius of the circle.</param>  
        /// <returns type="Number">The area.</returns>  
        var areaVal;  
        areaVal = Math.PI * radius * radius;  
        return areaVal;  
    }  
    ```  
  
-   Para exibir os comentários de documentação XML, digite o nome e o parêntese de abertura de uma função que é marcado com comentários de documentação XML, como no exemplo a seguir:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Quando você digita o parêntese de abertura da função que contém comentários de documentação XML, o Editor de código usa IntelliSense para exibir as informações definidas em comentários de documentação XML.  
  
### Criar comentários de documentação XML para um campo de JavaScript  
  
-   Em uma definição de função ou objeto de construtor, adicionar um [\< campo \>](../ide/field-javascript.md) elemento precedido por três barras \(\/ \/ \/\).  
  
     O exemplo a seguir mostra o uso de `<field>` elemento em uma função de construtor.  Para exemplos adicionais, consulte [\< campo \>](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Para exibir os comentários de documentação XML, crie um objeto usando o construtor de função é marcado com comentários de documentação XML, como no exemplo a seguir.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   Na próxima linha, digite o nome do objeto e um período para mostrar informações de IntelliSense para o campo.  
  
    ```javascript  
    eng.  
    ```  
  
### Criar comentários de documentação XML para uma função sobrecarregada  
  
1.  Na função, adicionar um [\< assinatura \>](../Topic/%3Csignature%3E%20\(JavaScript\).md) elemento para cada sobrecarga.  Esses elementos, adicionar outros elementos, como `<summary>`, `<param>`, e `<returns>`, precedendo cada elemento com três barras \(\/ \/ \/\).  
  
     O exemplo a seguir mostra uma função sobrecarregada do JavaScript.  Neste exemplo, as sobrecargas diferem pelo tipo de parâmetro.  
  
    ```javascript  
    function calc(a) {  
        /// <signature>  
        /// <summary>Function summary 1.</summary>  
        /// <param name="a" type="Number">A number.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        /// <signature>  
        /// <summary>Function summary 2.</summary>  
        /// <param name="a" type="String">A string.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        return a;  
    }  
    ```  
  
2.  Para exibir os comentários de documentação XML, digite o nome e o parêntese de abertura da função que é marcado com comentários de documentação XML, como no exemplo a seguir:  
  
    ```javascript  
    calc(  
    ```  
  
### Criar IntelliSense localizada  
  
1.  Crie um arquivo XML que tem comentários de documentação no formato OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    >  MessageBundle é o formato recomendado.  Este formato não é suportado no Microsoft Ajax ou em arquivos de .winmd.  Para obter informações sobre como usar a alternativa `VSDoc` formato, consulte [\< loc \>](../ide/loc-javascript.md).  
  
     O exemplo a seguir mostra o conteúdo em um arquivo secundário que contém informações de IntelliSense localizadas.  Este é um arquivo XML que está localizado na pasta cultura específica, como JA.  A pasta deve estar no mesmo local do arquivo. js que contém o `<loc>` elemento.  O nome do arquivo XML deve corresponder a `filename` parâmetro especificado na `<loc>` elemento.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  No arquivo. js, adicione o seguinte código.  O `<loc>` elemento deve ser declarado antes de qualquer script e segue as mesmas regras de uso como o `<reference>` elemento.  Para obter mais informações, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md) e [\< loc \>](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  No arquivo. js, adicione elementos de documentação XML e descrições padrão.  Definir o `locid` valores para corresponder ao correspondente `name` valores de atributo de arquivo secundário.  As descrições padrão serão substituídas pelas informações IntelliSense localizadas, se estiver disponível.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  Para exibir os comentários de documentação XML, digite o nome e o parêntese de abertura da função, como no exemplo a seguir:  
  
    ```javascript  
    add(  
    ```  
  
## Consulte também  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/pt-br/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)