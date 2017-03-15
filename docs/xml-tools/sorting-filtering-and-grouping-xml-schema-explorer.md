---
title: "Sorting, Filtering, and Grouping (XML Schema Explorer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Sorting, Filtering, and Grouping (XML Schema Explorer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve as opções que estão disponíveis através do menu de **Classificação, filtragem, e opções de agrupamento** na barra de ferramentas XML Schema Explorer.  
  
## Opções de filtro  
 As seguintes opções de filtro estão disponíveis.  Por padrão, **Mostrar Namespaces** e opções de **Mostrar Arquivos do Esquema** são selecionados.  
  
-   **Mostrar Namespaces**.  
  
-   **Mostrar Arquivos do Esquema**.  
  
-   **Compositores de apresentação \(sequência\/opção\/todos\)**.  
  
## Opções de classificação  
 As seguintes opções de classificação estão disponíveis.  O padrão é **Classificar por Tipo**.  O tipo por opções não se aplica a arquivos e para namespaces.  
  
-   **Classificar por Tipo**.  
  
-   **Classificar por nome**.  
  
-   **Ordem de documento**.  
  
### Classificar por Tipo  
 Quando a opção de **Classificar por Tipo** é selecionada, os nós globais são classificados na seguinte ordem.  Nós são classificados em ordem alfabética dentro de cada grupo.  
  
1.  nós de`import` .  
  
2.  nós de`include` .  
  
3.  nós de`redefine` .  
  
4.  nós de`attribute` .  
  
5.  nós de`attributeGroup` .  
  
6.  nós de`complexType` .  
  
7.  nós de`simpleType` .  
  
8.  nós de`element` .  
  
9. nós de`group` .  
  
### Classificar por Nome  
 Quando a opção de **Classificar por nome** é selecionada, os nós globais são classificados na seguinte ordem:  
  
1.  nós de`import` \(em ordem alfabética namespaces\).  
  
2.  nós de`include` \(em ordem alfabética de atributos de `schemaLocation` \).  
  
3.  nós de`redefine` \(em ordem alfabética de atributos de `schemaLocation` \).  
  
4.  Outros nós globais em ordem alfabética.  
  
### Ordem de documento  
 A opção de **Ordem de documento** está disponível quando a opção de **Mostrar Arquivos do Esquema** é selecionada.  Quando **Ordem de documento** é selecionado, os nós globais são exibidos na ordem em que aparecem no arquivo de esquema.  
  
## Gravando o tipo\/opções de filtro  
 A classificação, filtragem, e opções de agrupamento são salvas no Registro para cada usuário, não importa qual a solução ou arquivos estavam aberta quando as configurações foram alteradas.