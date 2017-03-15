---
title: "Como depurar um aplicativo parcialmente confi&#225;vel | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], aplicativos parcialmente confiáveis"
  - "aplicativos parcialmente confiáveis"
  - "segurança [Visual Studio], aplicativos parcialmente confiáveis"
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar um aplicativo parcialmente confi&#225;vel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aplica\-se a aplicativos do Windows e do console.  
  
 O [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md) facilita implantar aplicativos de confiança parcial que se beneficiam de [Segurança de acesso do código](../Topic/Code%20Access%20Security.md) para limitar o acesso aos recursos em um computador.  
  
 Depurar um aplicativo de confiança parcial pode ser um desafio, porque os aplicativos de confiança parcial têm permissões de segurança diferentes \(e, portanto, comportam\-se diferente\) dependendo de onde são instalados.  Se for instalado da Internet, um aplicativo de confiança parcial terá algumas permissões.  Se for instalado de uma intranet local, terá mais permissões e, se for instalado do computador local, terá permissões completas.  Você também pode ter zonas personalizados, com permissões personalizadas.  Você pode precisar depurar um aplicativo de confiança parcial em algumas ou todas essas condições.  Felizmente, o Visual Studio facilita isso também.  
  
 Antes de iniciar uma sessão de depuração no Visual Studio, você pode escolher a zona que deseja simular a instalação de um aplicativo.  Quando você iniciar a depuração, o aplicativo terá as permissões adequadas para um aplicativo de confiança parcial instalado a partir dessa zona.  Isso permite ver o comportamento do aplicativo que seria exibido para um usuário que faz o download a partir dessa zona.  
  
 Se o aplicativo tentar executar uma ação para a qual não tem permissão, ocorre uma exceção.  Nesse ponto, o Assistente de Exceção oferece a possibilidade adicionar uma permissão adicional, que permite reiniciar a sessão de depuração com permissões suficientes para evitar o problema.  
  
 Posteriormente, você pode voltar e ver quais permissões foram adicionadas durante a depuração.  Se você tivesse que adicionar uma permissão ao depurar, ela provavelmente indicaria que você precisa adicionar uma solicitação de consentimento do usuário nesse momento em seu código.  
  
> [!NOTE]
>  Os visualizadores do depurador exigem privilégios maiores do que são permitidos por um aplicativo de confiança parcial.  Os visualizadores não serão carregados quando você for interrompido no código com confiança parcial.  Para depurar usando um visualizador, você deverá executar o código com confiança total.  
  
### Para escolher uma zona para seu aplicativo de confiança parcial  
  
1.  No menu **Projeto**, escolha *Projectname***Propriedades**.  
  
2.  Nas páginas de propriedades de *Projectname*, clique na página **Segurança**.  
  
3.  Selecione **Habilitar configurações de segurança do ClickOnce**.  
  
4.  Em **A zona a partir do qual seu aplicativo será instalado**, clique na caixa de listagem suspensa e escolha a zona que você deseja simular o aplicativo do qual está sendo instalado.  
  
     A grade **Permissões exigidas pelo aplicativo** mostra todas as permissões disponíveis.  A marca de seleção indica as permissões concedidas ao aplicativo.  
  
5.  Se a zona que você escolher foi **\(Personalizada\)**, selecione as configurações personalizadas corretas na coluna **Configuração** da grade **Permissões**.  
  
6.  Clique **OK** para fechar as páginas de propriedades.  
  
### Para adicionar uma permissão extra quando ocorrer uma exceção de segurança  
  
1.  A caixa de diálogo **Assistente de Exceção** é exibida com a mensagem: SecurityException sem tratamento.  
  
2.  Na caixa de diálogo **Assistente de Exceção**, em **Ações**, clique em **Adicionar Permissão ao Projeto**.  
  
3.  A caixa de diálogo **Reiniciar Depuração** é exibida.  
  
    -   Se você quiser reiniciar a sessão de depuração com a nova permissão, clique em **Sim**.  
  
    -   Se você não quiser reiniciar ainda, clique em **Não**.  
  
### Para exibir as permissões adicionais adicionadas durante a depuração  
  
1.  No menu **Projeto**, escolha *Projectname***Propriedades**.  
  
2.  Nas páginas de propriedades de *Projectname*, clique na página **Segurança**.  
  
3.  Examine a grade **Permissões exigidas pelo aplicativo**.  Qualquer permissão adicional que você tiver adicionado tem dois ícones na coluna **Incluído**: a marca de seleção normal, que todas as permissões incluídas têm, e um ícone adicional, que parece um balão que contém a letra “i”.  
  
4.  Use a barra de rolagem vertical para exibir a grade **Permissões exigidas pelo aplicativo** inteira.  
  
## Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Segurança do depurador](../debugger/debugger-security.md)