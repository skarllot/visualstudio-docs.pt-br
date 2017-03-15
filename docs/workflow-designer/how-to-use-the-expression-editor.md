---
title: "How to: Use the Expression Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ExpressionTextBox.UI"
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
caps.handback.revision: 13
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Use the Expression Editor
O editor de expressão é um controle de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que é usado em muitas atividades de fluxo de trabalho como um meio de inserir e avaliar dessas expressões.  O editor de expressão fornece IDE completo que a experiência de edição IntelliSense, que inclui coloração, ParamInfo, squiggles de erro, entre outros recursos.  O compilador valida a expressão após está conectado.  Se a expressão é inválido, um ícone de erro é exibido.  O editor também pode ser aberto como uma caixa de diálogo **Editor de Expressão** .  
  
 As expressões são valores ou código literal de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] associado aos argumentos ou propriedades.  Contém os elementos de valor \(por exemplo.  variáveis, constantes, literais, propriedades\) que são combinados com as operações para produzir um novo valor.  As expressões são escritas usando a sintaxe de VB.NET mesmo se o aplicativo estiver em um programa usando C\#.  Isso significa que a maiúsculas não importa, a comparação é executada usando os únicos igual \(“sinal \= "\) em vez de \=\= o \(“"\), os operadores boolianos é a palavra “e” e “ou” em vez de "" de símbolos&&e “&#124;&#124;”, e **Nothing** é usado em vez de **null**.  Para obter mais informações sobre expressões e operadores no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e alguns exemplos, consulte [operadores e expressões em Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).  
  
 **Editor de Expressão** Se comporta como segue:  
  
-   Se o foco não estiver no editor de expressão, parece um controle normal TextBlock.  
  
-   Uma vez que o foco estiver no editor de expressão, e ele se comporta como o controle editor de expressão.  Após perde o foco, parece uma TextBlock normal novamente.  
  
-   Se você fica no editor de expressão em um designer rehosted de fluxo de trabalho, então se comporta como uma caixa de texto.  Quando o foco é perdido no designer rehosted de fluxo de trabalho, o editor de expressão parece uma TextBlock normal novamente.  
  
> [!NOTE]
>  O IntelliSense para o editor de expressão está disponível somente dentro de [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  Em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] e em cenários rehosted, o compilador valida a expressão após está conectado e o editor de expressão um ícone de erro se a expressão não é válido.  
  
### Usando o editor de expressão  
  
1.  Em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], abra um projeto novo ou existente de fluxo de trabalho.  
  
2.  Adicione, por exemplo, a atividade de <xref:System.Activities.Statements.Assign> ao fluxo de trabalho.  
  
    > [!NOTE]
    >  Várias atividades de fluxo de trabalho têm editores de expressão.  A expressão TextBlocks também aparece no designer variável, no designer do argumento, e no designer dinâmico do argumento.  A atividade de <xref:System.Activities.Statements.Assign> é usada como um exemplo.  
  
3.  Clique no editor de expressão esquerdo do designer de atividade para atividades de <xref:System.Activities.Statements.Assign> .  
  
     As cadeias de caracteres **\<A\>** e **\<Inserir uma expressão VB\>** de marca de agua de cinza são as cadeias de caracteres de texto padrão para editores de expressão na atividade de <xref:System.Activities.Statements.Assign> .  
  
4.  Digite sua expressão.  Se você inserir uma cadeia de caracteres, certifique\-se coloque aspas ao redor de cadeia de caracteres.  Se você escolher para associar o argumento da expressão a uma variável, deixe a aspas \- tica.  
  
     Quando você terminar, selecione uma região ou uma área fora do editor de expressão para deslocar o foco a outra parte do designer.  Isso fará com que o compilador validar a expressão como descrito anteriormente.  
  
     Entrada de maneira alternativa\/edição uma expressão é clique nas reticências ao lado do nome da propriedade na grade de propriedade.  Isso abrirá **Editor de Expressão** como a caixa de diálogo.  
  
## Consulte também  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>