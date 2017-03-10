---
title: "Vis&#227;o geral do Visual Studio Tools for Unity | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "crdun"
manager: "crdun"
---
# Vis&#227;o geral do Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nesta seção, você aprenderá mais sobre os recursos do Visual Studio Tools para ofertas do Unity e como usá\-los para se tornarem mais produtivos com o Unity.  
  
 Com o Visual Studio Tools para o Unity \(*VSTU*\), você pode usar o Visual Studio para escrever scripts de jogo e editor em c\# e, em seguida, usar seu depurador poderoso para localizar e corrigir erros.  A versão mais recente do VSTU inclui sintaxe colorida para idiomas de sombreador ShaderLab do Unity, melhores visualizações do depurador e geração de código aprimorada para o Assistente do MonoBehavior.  VSTU também coloca seus arquivos de projeto do Unity, mensagens do console e a capacidade de iniciar o jogo no Visual Studio para que possa gastar menos tempo alternância do Unity Editor durante a gravação de código.  
  
 Continue lendo para saber mais sobre esses recursos.  
  
## Integração com o Unity  
 Visual Studio Tools para o Unity não seria uma enhancer de produtividade caso seja necessário alternar entre o Visual Studio e o Unity editor o tempo todo.  É por isso que o Visual Studio Tools para o Unity torna mais fácil continuar fazendo o trabalho sem sair do Visual Studio.  
  
-   O**Explorador de projeto do Unity**exibe todo o projeto Unity dentro do Visual Studio usando a mesma hierarquia exibida no Unity editor.  
  
-   Integração com o Unity console exibe a saída do console do Unity dentro do janela de erro do Visual Studio.  
  
-   Inicie a depuração de seu jogo do Visual Studio – sem precisar alternar de volta para o Unity, pressione F5.  
  
## Superior a depuração  
 Conecte o depurador poderoso do Visual Studio para seu jogo Unity para depurar seus scripts de c\# e DLLs, independentemente se ele estiver em execução autônoma ou no editor do Unity.  Você pode usar todos os recursos de depuração esperado do Visual Studio.  
  
-   Pontos de interrupção, incluindo pontos de interrupção condicionais.  
  
-   Avalie expressões complexas na janela de inspeção.  
  
-   Inspecionar e modificar o valor de variáveis e argumentos.  
  
-   Analisar estruturas complexas de objetos e dados.  
  
 Você ainda pode depurar seu jogo Unity enquanto ele é executado em outro computador na rede.  
  
## Produtividade  
 Além de produtividade de estabelecidas do Visual Studio para escrever e refatoração de código em c\#, Visual Studio Tools para o Unity fornece recursos de produtividade extra para desenvolvedores do Unity.  
  
-   Sintaxe colorida para idioma de ShaderLab do Unity ajuda a identificar erros no seus sombreadores antes de se tornarem bugs.  Basta abra seus arquivos ShaderLab no Visual Studio.  
  
-   O assistente MonoBehavior permite que você procure uma lista de comportamentos do Unity e cria o código clichê para comportamentos com que pode não estar familiarizado.  Pressionar  CTRL \+ SHIFT \+ M.  
  
-   Depois de se familiarizar com os comportamentos do Unity que mais usados, o assistente MonoBehavior rápida coloca ao seu alcance.  Pressionar  CTRL \+ ALT \+ Q.  
  
-   Acesse a documentação do Unity do Visual Studio.  Basta realçar a chamada de API que você deseja conhecer, em seguida, pressione  CTRL \+ ALT \+ M, CTRL \+ H.  
  
-   Acesse todos esses recursos e muito mais com atalhos de teclado.  
  
## Ferramentas do Visual Studio para a API do Unity  
 Personalizar e estender o comportamento do Visual Studio Tools para o Unity usando as APIs fornecidas.  
  
-   Visual Studio Tools para o Unity registra um retorno de chamada de log para o console do Unity para Visual Studio pode transmitir.  Se você tiver scripts de editor que informações de log, você pode colocá\-los no mesmo retorno de chamada para enviar suas mensagens para o Visual Studio.  Para obter mais informações, consulte o exemplo de retorno de chamada de Log.  
  
-   Você pode alterar como o Visual Studio Tools para o Unity gera arquivos de projeto usando o retorno de chamada do Unity estilo ProjectFileGeneration.  Para obter mais informações, consulte o exemplo de geração de arquivo de projeto.  
  
## Consulte também  
 [Home page do unity](http://unity3d.com)