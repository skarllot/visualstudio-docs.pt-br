---
title: "Comentários da Tarefa"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 973e7b627a7b5c121ff388874577fe59c45529d7
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="task-comments"></a>Comentários da Tarefa

Ao escrever o código, é uma prática padrão comentar explicitamente código incompleto, questionável ou soluções alternativas rápidas com avisos. Os tokens de sinal padrão fornecidos pelo Visual Studio para Mac são TODO, HACK, FIXME e UNDONE, embora tokens personalizados possam ser definidos em **Visual Studio > Preferências... > Ambiente > Tarefas**, que é ilustrado abaixo:

 ![Preferências da lista de tarefas](media/source-editor-image10.png)

Para adicionar um novo comentário de tarefa, adicione um comentário que inclui a palavra-chave da tarefa. Por exemplo:

```
//TODO: Finish this for all properties.
```

O Visual Studio para Mac chama a atenção para esses marcadores realçando-os no painel da Lista de Tarefas, que pode ser exibido navegando para **Exibir > Painéis > Tarefa**:

![Painel de lista de tarefas](media/source-editor-image11.png)
