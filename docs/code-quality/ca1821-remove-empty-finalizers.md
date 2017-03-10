---
title: "CA1821: remover finalizadores vazios | Microsoft Docs"
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
  - "RemoveEmptyFinalizers"
  - "CA1821"
helpviewer_keywords: 
  - "CA1821"
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1821: remover finalizadores vazios
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|CheckId|CA1821|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo implementa um finalizador que está vazia, chama somente o finalizador do tipo de base, ou chama somente métodos condicional emissores.  
  
## Descrição da Regra  
 Sempre que possível, para evitar finalizers devido à sobrecarga adicional de desempenho que é envolvida no tempo de vida do objeto de rastreamento.  O coletor de lixo será executado o finalizador antes de coleta o objeto.  Isso significa que duas coleções serão necessárias coletar o objeto.  Um finalizador vazia incorre essa sobrecarga adicionada sem nenhum benefício.  
  
## Como Corrigir Violações  
 Remova o finalizador vazia.  Se um finalizador depurando, é necessário incluir o finalizador inteiro em políticas de `#if DEBUG / #endif` .  
  
## Quando Suprimir Alertas  
 Não suprima uma mensagem desta regra.  A falha suprimir o desempenho de reduz de acabamento e não fornece nenhum benefício.  
  
## Exemplo  
 O exemplo a seguir mostra um finalizador vazio que deve ser removido, um finalizador que deve ser incluído em políticas de `#if DEBUG / #endif` , e um finalizador que use as políticas de `#if DEBUG / #endif` corretamente.  
  
 [!code-cs[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]