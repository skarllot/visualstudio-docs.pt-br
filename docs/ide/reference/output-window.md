---
title: "Janela de Saída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 30
author: kempb
ms.author: kempb
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 118223d1a5c07188b8f8d8c7b6990792dcd94ff5
ms.lasthandoff: 02/22/2017

---
# <a name="output-window"></a>Janela Saída
A Janela de **Saída** pode exibir mensagens de status para vários recursos no IDE (ambiente de desenvolvimento integrado). Para abrir a Janela de **Saída**, na barra de menus, escolha **Exibir/Saída** (ou clique em CTRL+ALT+O).  
  
> [!WARNING]
>  A Janela de Saída não é exibida no menu Exibir nas edições do Visual Studio Express. Para mostrá-la, use as teclas de atalho CTRL+ALT+O.  
  
## <a name="toolbar"></a>Barra de ferramentas  
 **Mostrar saída de**  
 Exibe um ou mais painéis de saída a serem exibidos. Vários painéis de informações podem estar disponíveis, dependendo de quais ferramentas no IDE usaram a Janela de **Saída** para entregar mensagens ao usuário.  
  
 **Localizar Mensagem no Código**  
 Move o ponto de inserção no editor de código para a linha que contém o erro de build selecionado.  
  
 **Ir para Mensagem Anterior**  
 Altera o foco na Janela de **Saída** para o erro de build anterior e move o ponto de inserção no editor de código para a linha que contém o erro de build.  
  
 **Ir para a Próxima Mensagem**  
 Altera o foco na Janela de **Saída** para o próximo erro de build e move o ponto de inserção no editor de código para a linha que contém o erro de build.  
  
 **Limpar tudo**  
 Limpa todo o texto do painel **Saída**.  
  
 **Ativar/Desativar Quebra Automática de Linha**  
 Ativa e desativa o recurso Quebra Automática de Linha no painel **Saída**. Quando a Quebra Automática de Linha estiver ativada, um texto em entradas maiores que se estende além da área de exibição será mostrado na próxima linha.  
  
## <a name="output-pane"></a>Painel de saída  
 O painel **Saída** selecionado na lista **Mostrar saída de** exibe a saída da fonte indicada.  
  
## <a name="routing-messages-to-the-output-window"></a>Encaminhando mensagens para a Janela de Saída  
 Para exibir a janela **Saída** sempre que você compilar um projeto, na caixa de diálogo **Geral, Projetos e Soluções, Opções**, selecione **Mostrar Janela de Saída no início do build**. Em seguida, com um arquivo de código aberto para edição, escolha os botões **Ir para a Próxima Mensagem** e **Ir para a Mensagem Anterior** na barra de ferramentas da Janela de **Saída** para selecionar entradas no painel **Saída**. Conforme você faz isso, o ponto de inserção no editor de código salta para a linha de código em que ocorre o problema selecionado.  
  
 Alguns recursos do IDE e comandos invocados na [Janela Comando](../../ide/reference/command-window.md) fornecem sua saída para a Janela de **Saída**. A saída de ferramentas externas como arquivos .bat e .com, que normalmente é exibida na janela Prompt de Comando, é encaminhada para um painel **Saída** ao selecionar a opção **Usar Janela de Saída** em [Gerenciando ferramentas externas](../../ide/managing-external-tools.md). Muitos outros tipos de mensagens também podem ser exibidos em painéis **Saída**. Por exemplo, quando a sintaxe Transact-SQL em um procedimento armazenado é verificada em um banco de dados de destino, os resultados são exibidos na Janela de **Saída**.  
  
 Você também pode programar seus próprios aplicativos para gravar mensagens de diagnóstico em tempo de execução em um painel **Saída**. Para fazer isso, use os membros da classe <xref:System.Diagnostics.Debug> ou <xref:System.Diagnostics.Trace> no namespace <xref:System.Diagnostics> da Biblioteca de Classes .NET Framework. Membros da classe <xref:System.Diagnostics.Debug> exibem a saída quando você compila as configurações de Depuração da solução ou do projeto; membros da classe <xref:System.Diagnostics.Trace> exibem a saída quando você compila configurações de Depuração ou de Versão. Para obter mais informações, consulte [Mensagens de diagnóstico na Janela de Saída](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 No [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], é possível criar etapas e eventos de build personalizados cujos avisos e erros são exibidos e contados no painel **Saída**. Ao pressionar F1 em uma linha de saída, é possível exibir um tópico de ajuda apropriado. Para obter mais informações, consulte [Formatando a saída de uma etapa de build ou um evento de build personalizado](/visual-cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).  
  
## <a name="scrolling-behavior"></a>Comportamento de rolagem  
 Se você usar a rolagem automática na Janela de Saída e, em seguida, navegar usando o mouse ou as teclas de seta, a rolagem automática será interrompida. Para retomar a rolagem automática, pressione CTRL+END.  
  
## <a name="see-also"></a>Consulte também  
 [Mensagens de diagnóstico na Janela de Saída](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Como controlar a Janela de Saída](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [Compilando e criando](../../ide/compiling-and-building-in-visual-studio.md)   
 [Noções sobre configurações de build](../../ide/understanding-build-configurations.md)   
 [Visão geral da biblioteca de classes](http://msdn.microsoft.com/Library/7e4c5921-955d-4b06-8709-101873acf157)
