---
title: "Criando uma janela de ferramentas b&#225;sicas | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK do Visual Studio, janelas de ferramenta"
  - "janelas de ferramentas, criando no IDE"
ms.assetid: 1e96cf07-bde4-445b-bcd0-48cadb351dde
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Criando uma janela de ferramentas b&#225;sicas
Janelas de ferramenta são comuns do Visual Studio: o **Solution Explorer**, **lista de tarefas**, **Error List**, e **saída** windows são todas as janelas de ferramenta. Todas as janelas de ferramenta podem ser encaixadas no IDE da mesma maneira. Encaixe previsível permite que os usuários a gerenciar suas tarefas e informações de forma eficiente.  
  
 O modelo de pacote do Visual Studio cria uma implementação básica de uma janela de ferramenta simples.  
  
### Para criar uma janela de ferramentas usando o modelo de pacote do Visual Studio  
  
1.  Sobre o **arquivo** aponte para **novo**, e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo caixa, expanda **Other Project Types**, e clique em **extensibilidade**.  
  
3.  No **modelos** painel, clique em **Visual Studio Package**.  
  
4.  No **local** digite o caminho do arquivo para o VSPackage.  
  
5.  No **nome** caixa, digite o nome da solução e clique em **OK** para iniciar o modelo.  
  
6.  Sobre o **Select a Programming Language** selecione c\# ou Visual Basic. Que o modelo para gerar um arquivo key.snk para assinar o assembly. Como alternativa, **Procurar** para seu próprio arquivo de chave. O modelo faz uma cópia do arquivo de chave e nomes de key.snk.  
  
7.  Sobre o **informações básicas sobre o VSPackage** página, especifique os detalhes sobre o VSPackage ou aceite os padrões. Para obter mais informações, consulte [Passo a passo: Criando um comando de Menu usando o modelo de pacote do Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
8.  Sobre o **Selecionar opções VSPackage** página, verifique a janela da ferramenta.  
  
9. Na página de opções da janela de ferramenta, digite o nome para a barra de título no **nome de janela** caixa. Esse nome também é usado como exibir o texto do comando de menu para a janela da ferramenta. O comando de menu é adicionado para o **outras janelas** no submenu a **exibição** menu. Digite a ID de comando para a janela da ferramenta de **ID de comando** caixa ou aceite o padrão.  
  
10. Clique em **Concluir** para criar o VSPackage na pasta que você especificou.  
  
### Para testar sua janela de ferramentas  
  
1.  Sobre o **exibição** aponte para **outras janelas**, e, em seguida, clique em sua ferramenta da janela de comando. Uma janela de ferramenta com um **Click Me\!** botão é exibido.  
  
2.  Clique no botão. Uma mensagem será exibida com o texto:  
  
     Estamos dentro \[da empresa. \< nome de VSPackage \>. MyControl\].button1\_Click\(\).  
  
## Consulte também  
 [Abrindo uma janela de ferramentas programaticamente](../misc/opening-a-tool-window-programmatically.md)   
 [Conceitos básicos de VSPackage](../misc/vspackage-essentials.md)