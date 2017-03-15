---
title: "Introdução ao PTVS: Python interativo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 4
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fbfe2a8c99cf6edafb4f9315039d4ac5a50310ab
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-ptvs-interactive-python"></a>Introdução ao PTVS: Python interativo
Prompts interativos ou REPLs (read-eval-print loops) são uma ferramenta importante para linguagens de programação produtivas.  Eles permitem que você execute trechos de código para descobrir e aprender APIs, experimente usando API e desenvolva interativamente o código de trabalho para incluir em projetos ou programas.  
  
 É possível assistir a essas instruções em um breve [vídeo no YouTube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Na janela de Ambientes Python, você verá uma lista de todos os seus ambientes Python.  Você pode selecionar qualquer um para abrir uma janela interativa ou REPL.  Se você já executou o Python.exe em um prompt de comando, então você já viu um REPL python antes.  O REPL solicita que você insira o código, depois, pressione enter e veja imediatamente os resultados do seu código.  Isso é um contexto de execução ao vivo que inclui todo o estado de todas as suas execuções, atribuições de variáveis etc.  Você pode se referir a variáveis mantendo resultados em envios posteriores ao prompt do REPL.  Você pode gravar várias linhas de código e executá-las todas de uma vez (por exemplo, uma declaração de método ou várias instruções).  
  
 Quando você começar a usar uma nova biblioteca, o REPL é uma ótima maneira de experimentar a biblioteca.  Você pode importar a biblioteca, inspecionar subpacotes, classes e funções.  O Python pode fornecer todas essas informações por meio de sua função `help()`.  Além disso, Ferramentas do Python para Visual Studio (PTVS) fornecem sugestões e documentação com base em sua modelagem de código usada no editor, o que é feito sem a necessidade de executar a biblioteca.  Quando você executar o código, o PTVS usa informações de tempo de execução do Python para melhorar as sugestões de PTVS.  
  
 A Janela interativa também é útil para desenvolvimento de código iterativo ou evolucionários, inclusive testar seu código à medida que você o desenvolve.  Você pode selecionar uma função em uma janela do editor, pressionar o botão direito do ponteiro e escolher Enviar a interativo.  Este comando copia a seleção para a Janela interativa à medida que a próxima entrada e o executa.  Você visualiza imediatamente os resultados.  Se precisar fazer alterações na entrada anterior, você pode pressionar a seta para cima para obter o código de volta, modificá-lo e pressionar Ctrl+Enter para executar o código.  Pressionar Enter no final da entrada a executa, mas pressionar Enter no meio da entrada insere uma nova linha.  
  
 Você pode abrir uma Janela interativa para cada instalação do Python, quantas desejar.  Existem botões na parte superior da janela para limpar a exibição, redefinir o contexto de execução etc.  O histórico permanecerá intacto.  
  
 É possível assistir a essas instruções em um breve [vídeo no YouTube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Consulte também  
 [Documentação do wiki](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [Introdução ao PTVS e vídeos de aprofundamento](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
