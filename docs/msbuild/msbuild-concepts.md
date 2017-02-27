---
title: Conceitos do MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: f6c59188abc8cbb9909c12438bc58fa9301d8af9
ms.openlocfilehash: 9a53328adf662b1c47dc1bf2317764562f2e204e

---
# <a name="msbuild-concepts"></a>Conceitos do MSBuild
O [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornece um esquema XML básico que você pode usar para controlar como a plataforma de build compila o software. Para especificar os componentes no build e como eles devem ser compilados, use essas quatro partes do MSBuild: propriedades, itens, tarefas e destinos.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Propriedades MSBuild](../msbuild/msbuild-properties.md)|Introduz propriedades e coleções de propriedades. As propriedades são pares chave-valor que podem ser usados para configurar builds.|  
|[Itens](../msbuild/msbuild-items.md)|Descreve os conceitos gerais por trás do formato do arquivo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] e como as partes se encaixam.|  
|[Destinos](../msbuild/msbuild-targets.md)|Explica como agrupar tarefas em uma ordem específica e habilitar seções do processo de build a ser chamado na linha de comando.|  
|[Tarefas](../msbuild/msbuild-tasks.md)|Mostra como criar uma unidade do código executável que pode ser usado por [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para realizar operações de build atômicas.|  
|[Comparando propriedades e itens](../msbuild/comparing-properties-and-items.md)|Compara itens e propriedades do MSBuild. Ambos são usados para passar informações para tarefas, avaliar condições e armazenar os valores que podem ser referenciadas em todo o arquivo de projeto.|  
|[Caracteres especiais do MSBuild](../msbuild/msbuild-special-characters.md)|Explica como escapar alguns caracteres que o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reserva para uso especial em contextos específicos.|  
|[Passo a passo: criando um arquivo de projeto MSBuild do zero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Mostra como criar um arquivo de projeto básico de forma incremental, usando somente um editor de texto.|  
|[Passo a passo: usando o MSBuild](../msbuild/walkthrough-using-msbuild.md)|Apresenta os blocos de construção do MSBuild e mostra como escrever, manipular e depurar projetos do MSBuild sem fechar o IDE (ambiente de desenvolvimento integrado) do Visual Studio.|  
|[Referência do MSBuild](../msbuild/msbuild-reference.md)|Links para documentos que contêm informações de referência.|  
|[MSBuild](../msbuild/msbuild.md)|Apresenta uma visão geral do esquema XML para um arquivo de projeto e mostra como ele controla os processos que compilam o software.|


<!--HONumber=Feb17_HO4-->


