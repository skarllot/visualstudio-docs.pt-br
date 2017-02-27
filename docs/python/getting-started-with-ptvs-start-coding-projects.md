---
title: "Introdução ao PTVS: iniciar a codificação (projetos) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 6
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
ms.openlocfilehash: 96f7bc59b84e837b5a01eec0224171571491a7b1

---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Introdução ao PTVS: iniciar a codificação (projetos)
As PTVS (Ferramentas Python para Visual Studio) ajudam você a gerenciar seu código. 
 
 É possível assistir a essas instruções em um breve [vídeo no YouTube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
 Se já tiver usado o Python antes, você sabe que seu projeto é definido pela forma como você dispões seus arquivos em disco. Isso funciona muito bem para projetos de Python simples, mas quando você tiver mais arquivos (páginas da Web com JavaScript, testes de unidade e scripts de build), os sistemas de arquivos podem começar a ficar um pouco limitantes. O Visual Studio usa projetos para fazer três coisas. 
 
- Identificar arquivos críticos. Arquivos importantes são aqueles que você incorpora a um sistema de controle de versão (arquivos de origem, recursos etc.), mas não arquivos que são gerados como saída do build. Arquivos importantes também são aqueles que você pode copiar para outro computador para que outra pessoa possa trabalhar em seu aplicativo. 
 
- Especificar como os arquivos devem ser usados. Você pode ter arquivos que uma ferramenta precisa processar sempre que os arquivos forem alterados. Projetos do Visual Studio podem capturar essas informações 
 
- Definir os limites de seus componentes. Se tiver vários componentes em seu aplicativo, você pode colocar cada um em um projeto separado. Eles podem, eventualmente, ser implantados em servidores diferentes, compilados com diferentes configurações de depuração ou build ou podem até mesmo ser escritos usando outra linguagem com suporte do Visual Studio, como C++ ou Node. js 
 
 Existem vários modelos de projeto para ajudá-lo a começar. Se você já tiver um código Python no qual gostaria de trabalhar, o assistente de código "De um Existente" o ajudará a criar um projeto que inclui todos os arquivos. Existem vários projetos Web para algumas estruturas populares. Mais modelos que estão disponíveis no pacote de amostras das PTVS. Há opções para fazer com que os modelos Web fornecidos funcionem com outras estruturas. O modelo Python Application é um projeto limpo e vazio. Há um módulo para você começar. 
 
 O Visual Studio mostra seus projetos abertos na janela do Gerenciador de Soluções, incluindo todos os arquivos, caminhos de pesquisa e ambientes Python. Para adicionar novos itens, selecione a pasta do projeto e, no menu de contexto (pressione o botão do ponteiro à direita), escolha Adicionar e, em seguida, Novo Item. É possível selecionar qualquer item na caixa de diálogo, personalizar o nome do item e adicionar o item ao projeto. 
 
 É possível arrastar e soltar no Gerenciador de Soluções. Se já tiver copiado arquivos para sua estrutura de diretórios do projeto, você pode selecionar Mostrar Todos os Arquivos na parte superior do Gerenciador de Soluções. Em seguida, você pode selecionar os itens que deseja adicionar e, no menu de contexto, escolher Incluir no Projeto. 
 
 É possível assistir a essas instruções em um breve [vídeo no YouTube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
## <a name="see-also"></a>Consulte também 
 [Documentação do wiki](https://github.com/Microsoft/PTVS/wiki/Projects) 
 [Introdução ao PTVS e vídeos de aprofundamento](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)


<!--HONumber=Feb17_HO4-->


