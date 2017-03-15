---
title: "Como depurar um aplicativo ClickOnce com permiss&#245;es restritas | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuração [Visual Studio], aplicativos ClickOnce"
  - "Implantação do ClickOnce, depuração"
  - "Aplicativos ClickOnce, depuração"
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como depurar um aplicativo ClickOnce com permiss&#245;es restritas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Como desenvolvedor, você provavelmente está executando seu computador de desenvolvimento com permissões de confiança total, portanto, não verá as exceções de segurança mesmo quando estiver depurando um aplicativo ClickOnce que o usuário final pode ver ao executá\-lo com permissões restritas.  
  
 Para capturar essas exceções, você precisa depurar o aplicativo com as mesmas permissões que o usuário final. Depuração com permissões restritas pode ser habilitada no **segurança** página do **Project Designer**.  
  
 Além disso, ao desenvolver aplicativos que chamem Web services, os serviços da Web geralmente residem em seu computador de desenvolvimento. Uma vez implantado, o usuário final irá acessar esses serviços da Web de uma URL diferente. Para emular a experiência do usuário final durante a depuração, você pode especificar que uma URL e o depurador tratará os serviços da Web como se eles estavam sendo chamados essa URL.  
  
### Para habilitar a depuração com permissões restritas  
  
1.  Com um projeto selecionado no **Solution Explorer**, diante o **projeto** menu, clique em **propriedades**.  
  
2.  No **Project Designer**, clique o **segurança** guia.  
  
3.  Selecione o **Habilitar a configuração de segurança do ClickOnce** caixa de seleção e, em seguida, clique no **é um aplicativo de confiança parcial** botão de opção.  
  
4.  Clique o **Avançado** botão.  
  
5.  Selecione o **depurar esse aplicativo com o conjunto de permissões selecionado** caixa de seleção e, em seguida, clique em **OK**.  
  
     Quando você depura o aplicativo, qualquer tentativa de acessar uma permissão que não faz parte do conjunto de permissões irá disparar uma exceção de segurança.  
  
### Para especificar uma URL para depuração  
  
1.  Com um projeto selecionado no **Solution Explorer**, diante o **projeto** menu, clique em **propriedades**.  
  
2.  No **Project Designer**, clique o **segurança** guia.  
  
3.  Selecione o **Habilitar a configuração de segurança do ClickOnce** caixa de seleção e, em seguida, clique no **é um aplicativo de confiança parcial** botão de opção.  
  
4.  Clique o **Avançado** botão.  
  
5.  Selecione o **depurar esse aplicativo com o conjunto de permissões selecionado** caixa de seleção e, em seguida, clique em **OK**.  
  
6.  No **depurar esse aplicativo como se ele fosse baixado da seguinte URL** caixa de texto, insira uma URL ou caminho de rede.  
  
## Consulte também  
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)