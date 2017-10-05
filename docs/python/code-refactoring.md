---
title: "Refatorando o código do Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76ebcb29-72d1-4958-9a63-8984c03d5c22
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 8826722a80f97de3b6e2e56600f6aaa9cb5d6134
ms.contentlocale: pt-br
ms.lasthandoff: 07/18/2017

---

# <a name="refactoring-python-code"></a>Refatorando o código do Python

O Visual Studio fornece vários comandos para transformar e limpar o código-fonte do Python automaticamente:

- [Renomear](#rename) renomeia uma classe, um método ou um nome de variável selecionado
- [Extrair método](#extract-method) cria um novo método do código selecionado
- [Adicionar importação](#add-import) fornece uma marcação inteligente para adicionar uma importação ausente
- [Remover importações não utilizadas](#remove-imports) remove importações não utilizadas

<a name="rename-variable"</a>
## <a name="rename"></a>Renomear

1. Clique com o botão direito do mouse no identificador que você deseja renomear e selecione **Renomear**, coloque o cursor no identificador e selecione o comando de menu **Editar > Refatorar > Renomear...**  (F2).
1. Na caixa de diálogo **Renomear** exibida, insira o novo nome do identificador e selecione **OK**:

  ![Renomear o prompt com o novo nome do identificador](media/code-refactor-rename-1.png)

1. Na próxima caixa de diálogo, selecione os arquivos e as instâncias no código aos quais a renomeação será aplicada; selecione uma instância individual para visualizar a alteração específica:

  ![Renomear a caixa de diálogo para selecionar o local em que as alterações serão aplicadas](media/code-refactor-rename-2.png)

1. Selecione **Aplicar** para fazer as alterações nos arquivos de código-fonte. (Não é possível desfazer esta ação.)

## <a name="extract-method"></a>Extrair método

1. Selecione as linhas de código ou a expressão a ser extraída para um método separado.
1. Selecione o comando de menu **Editar > Refatorar > Extrair método...** ou digite Ctrl-R, M.
1. Na caixa de diálogo exibida, insira um novo nome de método, indique o local em que ele deverá ser extraído e selecione as variáveis de fechamento. As variáveis não selecionadas para fechamento são transformadas em argumentos de método:

  ![Extrair a caixa de diálogo do método](media/code-refactor-extract-method-1.png)

1. Selecione **OK** e o código será modificado de acordo:

  ![Efeito da extração de um método](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Adicionar importação

Ao colocar o cursor em um identificador que não tem informações de tipo, o Visual Studio fornece uma marcação inteligente (o ícone de lâmpada à esquerda do código) cujos comandos adicionam a instrução `import` ou `from ... import` necessária:

![Adicionar marcação inteligente de importação](media/code-refactor-add-import-1.png)

O Visual Studio oferece conclusões `import` para módulos e pacotes de nível superior no projeto atual e na biblioteca padrão. O Visual Studio também oferece conclusões `from ... import` para submódulos e subpacotes, bem como membros do módulo. As conclusões incluem funções, classes e dados exportados. A seleção de uma dessas opções adiciona a instrução na parte superior do arquivo após outras importações ou em uma instrução `from ... import` existente se o mesmo módulo já foi importado.

![Resultado da adição de uma importação](media/code-refactor-add-import-2.png)

O Visual Studio tenta filtrar os membros que não estão realmente definidos em um módulo, como módulos que são importados para outro, mas que não são filhos do módulo que está realizando a importação. Por exemplo, muitos módulos usam `import sys` em vez de `from xyz import sys`, portanto você não vê a conclusão da importação `sys` de outros módulos, mesmo se eles não tiverem um membro `__all__` que exclui `sys`.

Da mesma forma, o Visual Studio filtra funções importadas de outros módulos ou do namespace interno. Por exemplo, se um módulo importa a função `settrace` do módulo `sys`, em teoria, é possível importá-lo desse módulo. Porém, é melhor usar `import settrace from sys` diretamente, assim, o Visual Studio oferecerá essa instrução especificamente.

Por fim, se algo normalmente precisar ser excluído devido às regras acima, mas tiver outros valores que serão incluídos (devido ao fato de o nome ter recebido um valor no módulo, por exemplo), o Visual Studio ainda excluirá a importação. Esse comportamento pressupõe que o valor não deverá ser exportado, pois ele é definido em outro módulo e, portanto, a atribuição adicional provavelmente será um valor fictício que também não é exportado.

<a name="remove-imports"</a>
## <a name="remove-unused-imports"></a>Remover importações não utilizadas

Ao escrever o código, é fácil acabar com instruções `import` para módulos que não estão sendo usados. Como o Visual Studio analisa o código, ele pode determinar automaticamente se uma instrução `import` é necessária, observando se o nome importado é usado dentro do escopo abaixo, no qual a instrução ocorre.

Clique com o botão direito do mouse em qualquer lugar do editor e selecione **Remover Importações**, que oferece opções para remover de **Todos os Escopos** ou apenas do **Escopo Atual**:

![Remover o menu de importações](media/code-refactor-remove-imports-1.png)

Em seguida, o Visual Studio fará as alterações apropriadas no código:

![Efeito da remoção de importações](media/code-refactor-remove-imports-2.png)

Observe que o Visual Studio não leva em conta o fluxo de controle, o uso de um nome antes de uma instrução `import` é tratado como se o nome fosse, na verdade, usado. O Visual Studio também ignora todas as importações `from __future__`, as importações que são executadas dentro de uma definição de classe, bem como de instruções `from ... import *`.
