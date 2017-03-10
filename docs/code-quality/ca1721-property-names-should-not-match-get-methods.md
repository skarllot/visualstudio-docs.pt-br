---
title: "CA1721: os nomes de propriedade n&#227;o devem corresponder a m&#233;todos get | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1721: os nomes de propriedade n&#227;o devem corresponder a m&#233;todos get
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O nome de um público ou inicia protegidos do membro com “e” correspondem a obtenção de outra forma o nome de um público ou de uma propriedade protegida.  Por exemplo, um tipo que contém um método denominado” e “GetColor uma propriedade chamada “cor” viola a regra.  
  
## Descrição da Regra  
 Obter métodos e as propriedades devem ter nomes que distinguem claramente a função.  
  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isso reduz o tempo necessário para obter uma nova biblioteca de software, e aumenta a confiança da biblioteca cliente que esteve desenvolvida por alguém que tiver experiência em código gerenciado desenvolvendo.  
  
## Como Corrigir Violações  
 Alterar o nome de modo que não corresponde ao nome de um método que é prefixado com “obtenham”.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
> [!NOTE]
>  Esse aviso pode ser excluído se o método obter é causado implementando a interface de IExtenderProvider.  
  
## Exemplo  
 O exemplo a seguir contém um método e uma propriedade que diminui a regra.  
  
 [!CODE [FxCop.Naming.GetMethod#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod#1)]  
  
## Regras Relacionadas  
 [CA1024: usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)