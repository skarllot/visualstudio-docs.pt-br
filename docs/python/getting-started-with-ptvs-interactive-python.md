---
title: "Introdu&#231;&#227;o ao PTVS: Python interativo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 4
caps.handback.revision: 4
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
---
# Introdu&#231;&#227;o ao PTVS: Python interativo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Prompts interativos ou loops de leitura\-avaliação\-impressão \(REPLs\) são uma ferramenta fundamental para linguagens de programação produtivas.  Eles permitem que você execute trechos de código para descobrir e aprender APIs, experimente usar a API e desenvolvem um código de trabalho para incluir em projetos ou programas interativamente.  
  
 Assista a estas instruções em um curto [vídeo do youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Na janela de ambientes de Python, verá uma lista de todos os seus ambientes de Python.  Você pode selecionar qualquer um para abrir uma janela interativa ou REPL  Se você já executou Python.exe em um prompt de comando, você viu um python REPL antes.  Solicita o REPL e você pode inserir o código, pressione enter e ver imediatamente os resultados do seu código.  Isso é um contexto de execução em tempo real que inclua todo o estado de todas as suas execuções, atribuições de variável etc.  Você pode se referir a variáveis com resultados em envios posteriores para o REPL prompt.  Você pode escrever várias linhas de código e executá\-los todos de uma vez \(por exemplo, uma declaração de método ou várias instruções\).  
  
 Quando você começar a usar uma nova biblioteca, o REPL é uma ótima maneira de experimentar a biblioteca.  Você pode importar a biblioteca, inspecionar os pacotes sub, classes e funções.  Python pode informar todas essas informações por meio de seu `help()` função.  Além disso, Python Tools para Visual Studio \(PTVS\) oferece sugestões e com base em sua modelagem de código usada no editor, o que ele faz sem a necessidade de executar a biblioteca de documentação.  Quando você executar o código, o PTVS usa informações de tempo de execução do Python para melhorar as sugestões de PTVS.  
  
 Janela interativa também é útil para desenvolvimento iterativo ou evolucionários código, inclusive testar seu código como desenvolvê\-lo.  Você pode selecionar uma função em uma janela do editor, pressione o botão direito do ponteiro e escolha enviar a interativo.  Este comando copia a seleção na janela interativa como a próxima entrada e executa\-o.  Você ver imediatamente os resultados.  Se você precisar fazer alterações à entrada anterior, você pode pressionar a seta para cima para obter o código, modificar e pressione Ctrl \+ Enter para executar o código.  Pressionar Enter no final da entrada executa, mas pressionando Enter no meio de entrada insere uma nova linha.  
  
 Você pode abrir uma janela interativa para cada instalação do Python, quantos desejar.  Existem botões na parte superior da janela para limpar a tela, redefinir o contexto de execução, etc.  O histórico permanecerão intacto.  
  
 Assista a estas instruções em um curto [vídeo do youtube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## Consulte também  
 [Wiki documentação](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [PTVS Introdução e vídeos de mergulho profundo](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)