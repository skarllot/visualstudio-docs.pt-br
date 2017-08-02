---
title: "Refatorando o código do Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76ebcb29-72d1-4958-9a63-8984c03d5c22
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
translationtype: Human Translation
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: ea69604524010ab794a4de0e85aea1e5fd680ac4
ms.lasthandoff: 04/10/2017

---

# <a name="refactoring-python-code"></a>Refatorando o código do Python

O Visual Studio fornece vários comandos para transformar e limpar o código-fonte do Python automaticamente:

- [Renomear](#rename) renomeia uma classe, um método ou um nome de variável selecionado
- [Extrair método](#extract-method) cria um novo método do código selecionado
- [Adicionar importação](#add-import) fornece uma marcação inteligente para adicionar uma importação ausente
- [Remover importações não utilizadas](#remove-imports) remove importações não utilizadas

<a name="rename-variable"</a>
## <a name="rename"></a>Renomear

1. Clique com o botão direito do mouse no identificador que você deseja renomear e selecione **Renomear**, coloque o cursor no identificador e selecione o comando de menu **Editar > Refatorar > Renomear...** ou pressione F2.
1. Na caixa de diálogo **Renomear** exibida, insira o novo nome do identificador e selecione **OK**:

  ![Renomear o prompt com o novo nome do identificador](~/python/media/code-refactor-rename-1.png)

1. Na próxima caixa de diálogo, selecione os arquivos e as instâncias no código aos quais a renomeação será aplicada; selecione uma instância individual para visualizar a alteração específica:

  ![Renomear a caixa de diálogo para selecionar o local em que as alterações serão aplicadas](~/python/media/code-refactor-rename-2.png)

1. Selecione **Aplicar** para fazer as alterações nos arquivos de código-fonte. Essa é uma ação que não pode ser desfeita.

## <a name="extract-method"></a>Extrair método

1. Selecione as linhas de código ou a expressão a serem extraídas para um método separado.
1. Selecione o comando de menu **Editar > Refatorar > Extrair método...** ou digite Ctrl-R, M.
1. Na caixa de diálogo exibida, insira um novo nome de método, indique o local em que ele deverá ser extraído e selecione as variáveis de fechamento. As variáveis não selecionadas para fechamento são transformadas em argumentos de método:

  ![Extrair a caixa de diálogo do método](~/python/media/code-refactor-extract-method-1.png)

1. Selecione **OK** e o código será modificado de acordo:

  ![Efeito da extração de um método](~/python/media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Adicionar importação

Ao colocar o cursor em um identificador que não tem informações de tipo, o Visual Studio fornece uma marcação inteligente (o ícone de lâmpada à esquerda do código) cujos comandos adicionarão a instrução `import` ou `from ... import` necessária:

![Adicionar marcação inteligente de importação](~/python/media/code-refactor-add-import-1.png)

Preenchimentos `import` são oferecidos para pacotes e módulos de nível superior no projeto atual e na biblioteca padrão. Preenchimentos `from ... import` serão oferecidos para submódulos e subpacotes, bem como para membros do módulo. Isso inclui funções, classes ou dados exportados. A seleção de uma dessas opções adiciona a instrução na parte superior do arquivo após outras importações ou em uma instrução `from ... import` existente se o mesmo módulo já foi importado.

![Resultado da adição de uma importação](~/python/media/code-refactor-add-import-2.png)

O Visual Studio tenta filtrar os membros que não estão realmente definidos em um módulo, como módulos que são importados para outro, mas que não são filhos do módulo que está realizando a importação. Por exemplo, muitos módulos usam `import sys` em vez de `from xyz import sys`, portanto a conclusão da importação `sys` não será vista de outros módulos, mesmo se eles não tiverem um membro `__all__` que exclui `sys`.

Da mesma forma, o Visual Studio filtra funções importadas de outros módulos ou do namespace interno. Por exemplo, se um módulo importa a função `settrace` do módulo `sys`, em teoria, é possível importá-lo desse módulo. Porém, é melhor usar `import settrace from sys` diretamente, assim, o Visual Studio oferecerá essa instrução especificamente.

Por fim, se algo precisar ser excluído devido às regras acima, mas tiver outros valores que serão incluídos (devido ao fato de o nome ter recebido um valor no módulo, por exemplo), o Visual Studio ainda excluirá a importação. Isso pressupõe que o valor não deverá ser exportado, pois ele é definido em outro módulo e, portanto, a atribuição adicional provavelmente será um valor fictício que também não é exportado.

<a name="remove-imports"</a>
## <a name="remove-unused-imports"></a>Remover importações não utilizadas

Ao escrever o código, é fácil acabar com instruções `import` para módulos que não estão sendo usados. Como o Visual Studio analisa o código, ele pode determinar automaticamente se uma instrução `import` é necessária, observando se o nome importado é usado dentro do escopo abaixo, no qual a instrução ocorre.

Clique com o botão direito do mouse em qualquer lugar do editor e selecione **Remover Importações**, que oferece opções para remover de **Todos os Escopos** ou apenas do **Escopo Atual**:

![Remover o menu de importações](~/python/media/code-refactor-remove-imports-1.png)

Em seguida, o Visual Studio fará as alterações apropriadas no código:

![Efeito da remoção de importações](~/python/media/code-refactor-remove-imports-2.png)

Observe que o Visual Studio não leva em conta o fluxo de controle; o uso de um nome antes de uma instrução `import` será tratado como se o nome fosse, na verdade, usado. O Visual Studio também ignora todas as importações `from __future__`, as importações que são executadas dentro de uma definição de classe, bem como de instruções `from ... import *`.
