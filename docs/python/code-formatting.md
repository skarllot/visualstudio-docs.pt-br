---
title: "Formatando o código do Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0f1631-360b-45d4-a0cb-01c3c10d25f2
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: a14bc7e8c9194fff3a1bec2739c9e9c2480e905b
ms.contentlocale: pt-br
ms.lasthandoff: 05/09/2017

---

# <a name="formatting-python-code"></a>Formatando o código do Python

O Visual Studio permite reformatar rapidamente o código para que ele corresponda às opções de formatação pré-configuradas.

- Para formatar uma seleção: selecione **Editar > Avançado > Seleção de Formato** ou pressione Ctrl+E, F.
- Para formatar todo o arquivo: selecione **Editar > Avançado > Formatar Documento** ou pressione Ctrl+E, D.

As opções são definidas por meio de **Ferramentas > Opções > Editor de Texto > Python > Formatação** e suas subguias e, por padrão, são definidas para corresponderem a um superconjunto do [guia de estilo do PEP 8](http://www.python.org/dev/peps/pep-0008/). A guia **Geral** determina quando a formatação é aplicada; as outras três subpáginas são definidas nas próximas seções.

[O suporte do Python no Visual Studio](installation.md) também adiciona o comando útil [Preencher Parágrafo de Comentário](#fill-comment-paragraph-command) ao menu **Editar > Avançado**, conforme descrito abaixo.

## <a name="spacing"></a>Espaçamento

O **espaçamento** controla o local em que espaços são inseridos ou removidos em vários constructos de linguagem. Cada opção tem três valores possíveis:

- Marcado: garante que o espaçamento é aplicado.
- Desmarcado: remove o espaçamento.
- Indeterminado: deixa a formatação original em vigor.

Exemplos para as várias opções são fornecidos nas tabelas a seguir.

| Opção Definições de Classe | Selecionado | Limpo |
| --- | --- | --- | 
| Insere espaço entre o nome de uma declaração da classe e a lista de bases | `class X (object): pass` | `class X(object): pass` | 
| Inserir espaço dentro dos parênteses da lista de bases | `class X( object ): pass` | `class X(object): pass` |
| Inserir espaço dentro dos parênteses da lista de bases vazia | `class X( ): pass` | `class X(): pass` |

<br/>

| Opção Definições de Função | Selecionado | Limpo |
| --- | --- | --- |
| Inserir espaço entre o nome de uma declaração da função e a lista de parâmetros | `def X (): pass` | `def X(): pass` | 
| Inserir espaço dentro dos parênteses da lista de parâmetros | `def X( a, b ): pass` | `def X(a, b): pass` |
| Inserir espaço dentro dos parênteses da lista de parâmetros vazia | `def X( ): pass` | `def X(): pass` |
| Inserir espaços em torno de “=” em valores de parâmetro padrão | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| Inserir espaço antes e depois de operadores de anotação de retorno | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| Opção Operadores | Selecionado | Limpo |
| --- | --- | --- |
| Inserir espaços em torno de operadores binários | `a + b` | `a+b` |
| Inserir espaços em torno de atribuições | `a = b` | `a=b` |

<br/>

| Opção de espaçamento de expressão | Selecionado | Limpo |
| --- | --- | --- |
| Inserir espaço entre o nome de uma chamada de função e a lista de argumentos | `X ()` | `X()` |
| Inserir espaço dentro dos parênteses da lista de argumentos vazia | `X( )` | `X()` |
| Inserir espaço dentro dos parênteses da lista de argumentos | `X( a, b )` | `X(a, b)` |
| Inserir espaço dentro dos parênteses da expressão | `( a )` | `(a)` |
| Inserir espaço dentro dos parênteses da tupla vazia | `( )` | `()` |
| Inserir espaço dentro dos parênteses da tupla | `( a, b )` | `(a, b)` |
| Inserir espaço dentro de colchetes vazios | `[ ]` | `[]` |
| Inserir espaços dentro dos colchetes das listas | `[ a, b ]` | `[a, b]` |
| Inserir espaço antes do colchete de abertura | `x [i]` | `x[i]` |
| Inserir espaços dentro de colchetes | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>Instruções

As **instruções** controlam a reescrita automática de várias instruções em formatos mais apropriados para o Python.

| Opção | Antes da formatação | Após a formatação |
| --- | --- | --- |
| Colocar os módulos importados em uma nova linha | `import sys, pickle` | `import sys`<br/>`import pickle` |
| Remover pontos-e-vírgulas desnecessários | `x = 42;` | `x = 42` |
| Colocar várias instruções em novas linhas | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |


## <a name="wrapping"></a>Disposição

O **encapsulamento** permite definir a **Largura máxima do comentário** (o padrão é 80), para que se a opção **Encapsular comentários que são muito largos** for definida, o Visual Studio reformate os comentários para que eles não excedam essa largura.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```



## <a name="fill-comment-paragraph-command"></a>Comando Preencher Parágrafo de Comentário

A opção **Editar > Avançado > Preencher Parágrafo de Comentário** (Ctrl+E, Ctrl+P) reflui e formata o texto de comentário, combinando linhas curtas e dividindo as longas.

Por exemplo:

```python
# foo 
# bar
# baz
```

é alterado para:

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

é alterado para:

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
