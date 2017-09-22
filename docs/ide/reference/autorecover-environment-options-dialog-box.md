---
title: "Caixa de diálogo AutoRecuperação, Ambiente, Opções | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 320b31b01237656be157be9ad9ce5787521215db
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# <a name="autorecover-environment-options-dialog-box"></a>AutoRecover, Caixa de diálogo Opções, Ambiente
Use essa página da caixa de diálogo Opções para especificar se os arquivos passam por backup automático ou não. Essa página também permite especificar se arquivos modificados são restaurados ou não quando o IDE (ambiente de desenvolvimento integrado) é desligado inesperadamente. Você pode acessar essa caixa de diálogo selecionando o menu **Ferramentas** e escolhendo **Opções** e, em seguida, selecionando a pasta **Ambiente** e a página **AutoRecuperação**. Se essa página não aparecer na lista, selecione **Mostrar todas as configurações** na caixa de diálogo **Opções**.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 **Salvar informações de AutoRecuperação a cada \<n> minutos**  
 Use esta opção para personalizar a frequência com que um arquivo é salvo automaticamente no editor. Para arquivos salvos anteriormente, uma cópia do arquivo é salva em \\...\meus Documentos\Visual Studio \<*versão*>\Arquivos de Backup\\<*nome do projeto*>. Se o arquivo for novo e não tiver sido salvo manualmente, ele será salvo automaticamente usando um nome de arquivo gerado aleatoriamente.  
  
 **Manter informações de AutoRecuperação por \<n> dias**  
 Use esta opção para especificar por quanto tempo o Visual Studio manterá arquivos criados para AutoRecuperação.  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo Opções](../../ide/reference/options-dialog-box-visual-studio.md)
