---
title: "Como restaurar comandos de depurador ocultos | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "comandos, depurador"
  - "depurador, restaurando comandos"
  - "depurando [Visual Studio], restaurando comandos"
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como restaurar comandos de depurador ocultos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao configurar o Visual Studio, será solicitado que você escolha um conjunto de configurações padrão da IDE para a sua linguagem de programação principal.  As configurações padrão da IDE para algumas linguagens podem ocultar alguns comandos do depurador.  
  
 Se você quiser usar um recurso do depurador que esteja oculto pelas configurações padrão da IDE, poderá adicionar o comando novamente ao menu usando o procedimento a seguir.  
  
### Para restaurar comandos ocultos do depurador  
  
1.  Com um projeto aberto, no menu **Ferramentas**, clique em **Personalizar**.  
  
2.  Na caixa de diálogo **Personalizar**, clique na guia **Comandos**.  
  
3.  Na lista suspensa da **barra de menus:**, selecione o menu **Depurar** que você deseja que contenha o comando restaurado.  
  
4.  Clique no botão **Adicionar Comando...**.  
  
5.  Na caixa **Adicionar Comando**, selecione o comando que você deseja adicionar, e clique em **OK**.  
  
6.  Repita a etapa anterior para adicionar outro comando.  
  
7.  Clique em **Fechar** quando terminar de adicionar os comandos ao menu.  
  
    > [!WARNING]
    >  Alguns itens de menu aparecem somente quando o depurador estiver em modos específicos, por exemplo, o modo de execução ou o modo de interrupção.  Consequentemente, um item que você adicionou não pode ser visível imediatamente quando você concluir essas etapas.  
  
## Restaurando os comandos não disponíveis na caixa de diálogo personalizar  
 Alguns comandos, especialmente os encontrados em menus hierárquicos, não podem ser restaurados da caixa de diálogo **Personalizar**.  Para restaurar esses comandos, você deverá importar uma nova coleção de configurações da IDE.  
  
#### Para importar novas configurações da IDE  
  
1.  No menu, **Ferramentas**, clique em **Importar e Exportar Configurações**.  
  
2.  Na página **Assistente de Importação e Exportação de Configurações**, clique em **Importar configurações de ambiente selecionadas** e clique em **Avançar**.  
  
3.  Na página **Salvar configurações atuais**, decida se deseja salvar as configurações existentes e clique em **Avançar**.  
  
4.  Na página **Escolha uma Coleção de Configurações a Importar**, na pasta **Configurações padrão**, escolha uma coleção de configurações de desenvolvimento que tenha os comandos que você deseja usar.  Se você não souber qual coleção escolher, experimente **Configurações Gerais de Desenvolvimento** ou **Configurações de desenvolvimento do Visual C\+\+**, que fornecem a maioria dos comandos do depurador.  
  
5.  Clique em **Avançar**.  
  
6.  Na página **Escolha as Configurações a Importar**, em **Opções**, verifique se **Depurando** está selecionado.  Desmarque as outras caixas de seleção, a menos que você também queira importar essas configurações.  
  
7.  Clique em **Finalizar**.  
  
8.  Na página **Importação Concluída**, revisar todos os erros associados à redefinição das configurações em **Detalhes**.  
  
9. Clique em **Fechar**.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)