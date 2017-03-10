---
title: "Conclus&#227;o de instru&#231;&#227;o para identificadores | Microsoft Docs"
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
  - "IntelliSense [JavaScript], conclusão de instrução"
  - "conclusão de instrução, JavaScript IntelliSense"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Conclus&#227;o de instru&#231;&#227;o para identificadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript não permite digitação para declarações de variável explícita.  Como resultado, IntelliSense não pode sempre fornecer listas de conclusão para objetos.  Isso pode ocorrer em várias situações.  A seguir estão alguns mais comuns.  
  
-   Um parâmetro é declarado, mas ele não foi chamado em outro local do documento ativo, como mostrado no exemplo a seguir.  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   É um objeto em uma função que é chamada em resposta a um evento.  Em tempo de design, o mecanismo de IntelliSense não pode determinar o tipo dos objetos usados nesta situação.  
  
     Se o mecanismo de IntelliSense pode determinar que o evento deve ser chamado, normalmente por meio de `addEventListener` para o evento no documento ativo, informações mais precisas de IntelliSense são fornecidas.  
  
 Quando não consegue identificar um objeto IntelliSense, o mecanismo IntelliSense preenche a lista de conclusão com entidades nomeadas ou identificadores, que estão presentes no documento ativo.  Quando a lista de conclusão contém esses identificadores, ícones de informações aparecem ao lado.  Além disso, uma dica de ferramenta para cada identificador indica que a expressão é desconhecida.  A ilustração a seguir mostra a instrução opções de conclusão para um objeto do tipo `light` que não pode ser identificada porque o objeto e suas propriedades são indefinidas.  No entanto, o `intensity` propriedade está disponível na lista de identificador porque foi usado na `illuminate` função.  
  
 **Opções de conclusão de um objeto não identificado**  
  
 ![JavaScript IntelliSense para identificadores](../ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 Você pode substituir a lista de conclusão de um objeto usando recursos de extensibilidade de JavaScript IntelliSense ou comentários de documentação XML.  Usando esses recursos, você pode fornecer informações de tipo e mais descritivo IntelliSense quando ele poderia não estar disponível.  Para obter mais informações, consulte [Estendendo JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) e [Como criar comentários de documentação XML JavaScript](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## Consulte também  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)