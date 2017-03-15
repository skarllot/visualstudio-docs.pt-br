---
title: "Esta tarefa exige direitos adicionais | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UACDialog"
ms.assetid: a03d3509-5e6e-411a-9aec-0766d7ee3a0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Esta tarefa exige direitos adicionais
Este erro é exibido se um comando Visual Studio é chamado por um usuário cuja conta tem permissões insuficientes concluir a operação.  
  
 Alguns comandos do Visual Studio devem ser executados com uma conta que tenha os direitos de acesso de usuário suficientes para ativar o comando ler ou gravar todos os arquivos e chaves do Registro necessários.  Para obter esses direitos, você deve fechar e reabrir Visual Studio com uma conta que promova acesso, como um administrador.  
  
 Para obter mais informações sobre permissões para executar o Visual Studio, consulte [Permissões de usuário](../ide/user-permissions-and-visual-studio.md).  
  
### Para corrigir este erro  
  
1.  Na caixa de diálogo, clique em **Reinicie usando uma conta outra**.  
  
     Isso solicita que você salve a solução atualmente carregada e em seguida, feche\-o Visual Studio e reinicie, solicitando o para alternar para uma conta diferente.  
  
2.  No aviso de logon, logon com uma conta que tenha os direitos superiores de que a conta prévia, como o administrador.  
  
     Quando inicia Visual Studio, ele recarregarem a solução mais recente e a linha de comando.  
  
> [!NOTE]
>  Fazer logon com uma conta que tenha os direitos superiores não necessariamente garante que o comando do Visual Studio funciona.  Alguns comandos podem executar em vão mesmo se você estiver usando uma conta de administrador.