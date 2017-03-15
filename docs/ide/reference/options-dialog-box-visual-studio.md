---
title: "Caixa de Diálogo Opções (Visual Studio) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 19
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fa8c80e6830238bc482d6f2a8206a268ce23e5ea
ms.lasthandoff: 02/22/2017

---
# <a name="options-dialog-box-visual-studio"></a>Caixa de diálogo Opções (Visual Studio)
A caixa de diálogo **Opções** permite que você configure o IDE (ambiente de desenvolvimento integrado) para as suas necessidades. Por exemplo, estabelecer um local de salvamento padrão para seus projetos, alterar a aparência e o comportamento padrão das janelas e criar atalhos para os comandos mais usados. Também há opções específicas para a sua plataforma e linguagem de desenvolvimento. Você pode acessar **Opções** do menu **Ferramentas**.  
  
> [!NOTE]
>  As opções disponíveis nas caixas de diálogo e os nomes os locais dos comandos de menu que você vê podem diferir do que é descrito na Ajuda, dependendo de suas configurações ativas ou da edição. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="layout-of-the-options-dialog-box"></a>Layout da caixa de diálogo Opções  
 A caixa de diálogo **Opções** é dividida em duas partes: um painel de navegação à esquerda e uma área de exibição à direita. O controle de árvore no painel de navegação inclui nós de pasta, como Ambiente, Editor de Texto, Projetos e Soluções e Controle do Código-Fonte. Expanda qualquer nó da pasta para listar as páginas de opções que ele contém. Quando você seleciona o nó para uma determinada página, suas opções aparecem na área de exibição.  
  
 Opções para um recurso IDE não aparecem no painel de navegação até que o recurso seja carregado na memória. Portanto, quando começa uma nova sessão, pode ser que não sejam exibidas as mesmas opções que eram exibidas quando você terminou a última. Quando você cria um projeto ou executa um comando que usa um aplicativo em particular, nós para opções relevantes são adicionados à caixa de diálogo Opções. Essas opções adicionadas então permanecerão disponíveis, desde que o recurso de IDE permaneça na memória.  
  
> [!NOTE]
>  Algumas coleções de configurações definem o escopo do número de páginas que aparecem no painel de navegação da caixa de diálogo Opções. Você pode optar por exibir todas as páginas possíveis selecionando **Mostrar todas as configurações**.  
  
## <a name="how-options-are-applied"></a>Como as opções são aplicadas  
 Clicar em OK na caixa de diálogo **Opções** salva todas as configurações em todas as páginas. Clicar em Cancelar em qualquer página cancela todas as solicitações de alteração, incluindo qualquer uma recém feita em outras páginas de **Opções**. Algumas alterações nas configurações de opção, como aquelas feitas na [Caixa de Diálogo Fontes e Cores, Ambiente, Opções](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), apenas entrarão em vigor depois que você fechar e reabrir o Visual Studio.  
  
### <a name="show-all-settings"></a>Mostrar todas as configurações  
 Marcar ou desmarcar **Mostrar todas as configurações** aplica todas as alterações feitas na caixa de diálogo **Opções**, embora você ainda não tenha clicado em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando o editor](../../ide/customizing-the-editor.md)
