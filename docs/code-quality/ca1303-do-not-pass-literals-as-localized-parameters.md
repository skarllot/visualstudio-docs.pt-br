---
title: "CA1303: n&#227;o passar literais como par&#226;metros localizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303: n&#227;o passar literais como par&#226;metros localizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um método envia uma cadeia literal como um parâmetro a um construtor o método ou na biblioteca de classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e na cadeia de caracteres deve ser localizável.  
  
 Esse aviso é gerado quando uma cadeia de caracteres literal é passado como um valor em um parâmetro ou a uma propriedade e um ou mais dos seguintes casos são verdadeiras:  
  
-   O atributo de <xref:System.ComponentModel.LocalizableAttribute> de parâmetro ou da propriedade for definido para retificar.  
  
-   O nome do parâmetro ou da propriedade contém o texto”, “a “, mensagem” ou “legenda”.  
  
-   O nome do parâmetro de cadeia de caracteres que é passado para um método de Console.Write ou de Console.WriteLine é “valor” ou “formato”.  
  
## Descrição da Regra  
 Literais de cadeia de caracteres que são inseridas no código\-fonte são difíceis de ser localizado.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, substituir a cadeia literal com uma cadeia de caracteres recuperada por uma instância da classe de <xref:System.Resources.ResourceManager> .  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se a biblioteca de código não será localizada, ou se a cadeia de caracteres não é exposto ao usuário final ou a um desenvolvedor que usa a biblioteca de códigos.  
  
 Os usuários podem eliminar o ruído nos métodos que não devem ser transmitidos localizar cadeias de caracteres ou renomeando o parâmetro ou a propriedade denominada, ou marcando esses itens como anteriores.  
  
## Exemplo  
 O exemplo a seguir mostra um método que gerencie uma exceção quando qualquer um dos dois argumentos está fora do intervalo.  Para o primeiro argumento, o construtor de exceção é passado uma cadeia de caracteres literal, que viola esta regra.  Para o segundo argumento, o construtor é passado corretamente uma cadeia de caracteres recuperada com <xref:System.Resources.ResourceManager>.  
  
 [!CODE [FxCop.Globalization.DoNotPassLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals#1)]  
  
## Consulte também  
 [Recursos em aplicativos de área de trabalho](../Topic/Resources%20in%20Desktop%20Apps.md)