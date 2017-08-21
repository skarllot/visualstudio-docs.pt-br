---
title: "Comentários"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: cb44dc755721f6095c9a07ad3e6fec1f6849e149
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---

# <a name="comments"></a>Comentários

Ao depurar ou fazer experimentos no código, pode ser útil comentar blocos de código ou temporariamente ou a longo prazo. 

Para comentar um bloco inteiro de código:

* Selecione o código e escolha **Ativar/desativar comentários da linha** no menu de contexto

OU

* Use a associação de tela `cmd + /` no código selecionado.

Esses métodos podem ser usados para comentar ou remover a marca de comentário de partes do código. Em arquivos de C#, níveis adicionais de comentários de linha podem ser adicionados, permitindo que regiões de códigos sejam comentadas e a marca de comentário seja removida, preservando ainda os comentários reais: 

 ![comentários de vários níveis](media/source-editor-image8.png)

Comentários também são úteis para documentar código para futuros desenvolvedores poderão vir a interagir com ele. Isso geralmente é feito na forma de comentário de várias linhas, que são adicionados da seguinte maneira em cada linguagem:

**C#**

``` cs
/*
 This is a multi-line
 comment in C#
*/
```
**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

