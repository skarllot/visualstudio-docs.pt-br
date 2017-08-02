---
title: "Visualizar alterações | Microsoft Docs"
ms.custom: 
ms.date: 12/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e15c00f6-3e22-49b8-8269-69e4c8be8040
author: BrianPeek
ms.author: brpeek
manager: ghogen
f1_keywords:
- vs.codefix.previewchanges
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
ms.sourcegitcommit: 14e6961d6db557e77687eef17aae9b16f5a4d706
ms.openlocfilehash: eb49815ed120ee4ff65dfc04764282f1ac6d1ff8

---

# <a name="preview-changes"></a>Visualizar Alterações

Ao usar diversas *ações rápidas* ou ferramentas de *refatoração* no Visual Studio, geralmente é possível visualizar as alterações que serão feitas ao seu projeto antes de aceitá-las.  Isso é feito na janela **Visualizar Alterações**.  Por exemplo, aqui está a janela **Visualizar Alterações** mostrando o que será alterado durante uma refatoração de renomeação em um projeto C#:

![Visualizar Alterações](~/ide/media/previewchanges.png)

A metade superior da janela mostra as linhas específicas que serão alteradas, cada uma com uma caixa de seleção.  Você poderá marcar ou desmarcar cada caixa de seleção se você quiser aplicar a refatoração seletivamente, apenas a linhas específicas.

A parte inferior da janela mostra o código formatado do projeto que será alterado, com as áreas afetadas realçadas.  Selecionar a linha específica na metade superior da janela realçará a linha correspondente na metade inferior.  Isso permite que você pule rapidamente para a linha apropriada e veja o código ao redor.

Depois de revisar as alterações, clique no botão **Aplicar** para confirmar as alterações ou clique no botão **Cancelar** para deixar as coisas como estavam.

## <a name="see-also"></a>Consulte também  
[Refatoração no Visual Studio](../ide/refactoring-in-visual-studio.md)



<!--HONumber=Feb17_HO4-->


