---
title: Como desbloquear o Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/23/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 89c7ea153dc44342851b43ced5d99ffcd0b52312
ms.openlocfilehash: 75f0baac767d66ec3c942d26957beed256f45ab3
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-unlock-visual-studio"></a>Como Desbloquear o Visual Studio
Você pode avaliar o Visual Studio gratuitamente por até 30 dias. Ao entrar no IDE, você pode estender o período de teste por 90 dias. Para continuar usando o Visual Studio, você pode desbloquear o IDE  
  
1.  usando uma assinatura online.  
  
2.  inserindo uma chave do produto (Product Key).  
  
## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Para desbloquear o Visual Studio usando uma assinatura online  
 Para desbloquear o Visual Studio usando uma assinatura online do MSDN ou do Visual Studio associada a uma conta da Microsoft ou uma conta corporativa ou de estudante:  
  
1.  Clique no botão "Entrar" no canto superior direito do IDE (ou vá para Arquivo > Configurações de Conta para abrir a caixa de diálogo Configurações de Conta e clique no botão "Entrar".)  
  
2.  Insira as credenciais para uma conta da Microsoft ou uma conta corporativa ou de estudante. O Visual Studio encontrará uma assinatura do MSDN ou uma assinatura do Visual Studio Team Services associada à sua conta.  
  
> [!IMPORTANT]
>  O Visual Studio procura automaticamente assinaturas online associadas ao se conectar a uma conta do Visual Studio Team Services pela janela de ferramentas do Team Explorer. Quando você se conecta a uma conta do Visual Studio Team Services, pode entrar usando contas da Microsoft ou corporativas ou de estudante. Se houver uma assinatura online para aquela conta de usuário, o Visual Studio automaticamente desbloqueará o IDE para você.  
  
## <a name="to-unlock-visual-studio-with-a-product-key"></a>Para desbloquear o Visual Studio com uma chave do produto (Product Key)  
  
1.  Selecione **Arquivo > Configurações de Conta** para abrir a caixa de diálogo Configurações de Conta e clique no link "**	Licenciar com uma Chave do Produto (Product Key)**".  
  
2.  Insira a chave do produto (Product Key) no espaço fornecido.  
  
> [!TIP]
>  Versões de pré-lançamento do Visual Studio não têm chaves do produto (Product Keys). Você deve entrar no IDE para usar versões de pré-lançamento.  
  
## <a name="address-license-problem-states"></a>Tratar os estados de problema de licença  
  
### <a name="update-stale-licenses"></a>Atualizar licenças obsoletas  
 Talvez você tenha visto a mensagem abaixo indicando que sua licença ficará obsoleta no Visual Studio.  
  
 ![Caixa de diálogo de informações de usuário do Visual Studio](../ide/media/vs2013_userinfo.png "VS2013_UserInfo")  
  
 Essa mensagem indica que embora sua assinatura ainda possa ser válida, o token de licença que o Visual Studio usa para manter sua assinatura atualizada ainda não foi atualizado e se tornou obsoleto devido a um dos motivos a seguir:  
  
1.  Você não usou o Visual Studio ou não teve uma conexão com a Internet por um longo período.  
  
2.  Você saiu do Visual Studio.  
  
 Antes de o token de licença se tornar obsoleto, o Visual Studio mostrará primeiro uma mensagem de aviso solicitando que você insira suas credenciais novamente.  
  
 Se você não inserir suas credenciais novamente, o token começará a se tornar obsoleto. Quando isso acontece, a caixa de diálogo Configurações de Conta informa os dias restantes antes de seu token expirar completamente. Depois que o token expirar, você precisará inserir novamente suas credenciais para esta conta ou licença com outro método acima para poder continuar usando o Visual Studio.  
  
> [!IMPORTANT]
>  Se estiver usando o Visual Studio por longos períodos em ambientes com acesso limitado ou sem acesso à Internet, você deverá usar uma chave do produto (Product Key) para desbloquear o Visual Studio para evitar a interrupção.  
  
### <a name="update-expired-licenses"></a>Atualizar licenças expiradas  
 Se sua assinatura tiver expirado completamente e você não tiver mais direitos de acesso ao Visual Studio, você precisará:  
  
1.  Renovar sua assinatura. Para obter mais informações sobre a licença que você está usando, acesse a caixa de diálogo Arquivo > Configurações de Conta e procure as informações de licença no lado direito da caixa de diálogo.  
  
2.  Se você tiver outra assinatura associada a uma conta diferente, adicione essa conta à lista Todas as Contas no lado esquerdo da caixa de diálogo Arquivo > Configurações de Conta clicando no link “Adicionar uma conta...” .  
  
## <a name="see-also"></a>Consulte também  
 [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md) (Entrando no Visual Studio)

