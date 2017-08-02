---
title: Como desbloquear o Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/20/2017
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
ms.translationtype: HT
ms.sourcegitcommit: c3521e1de25854db012cb91bbe09d9463ecb42c7
ms.openlocfilehash: db9fff46d52be80e53bd5c09fb8ab9d1f06d4f3c
ms.contentlocale: pt-br
ms.lasthandoff: 07/21/2017

---

# <a name="how-to-unlock-visual-studio"></a>Como Desbloquear o Visual Studio
Você pode avaliar o Visual Studio gratuitamente por até 30 dias. Entrar no IDE estende o período de avaliação para 90 dias. Para continuar usando o Visual Studio, desbloqueie o IDE  
  
1.  usando uma assinatura online ou  
1.  inserindo uma chave do produto (Product Key).  
  
ed## Para desbloquear o Visual Studio usando uma assinatura online  
 Para desbloquear o Visual Studio usando uma assinatura do MSDN ou do Visual Studio Team Service associada a uma conta da Microsoft ou uma conta corporativa ou de estudante:  
  
1.  Clique no botão "Entrar" no canto superior direito do IDE (ou acesse Arquivo > Configurações de Conta para abrir a caixa de diálogo Configurações de Conta e clique no botão "Entrar".)  
  
1.  Insira as credenciais para uma conta da Microsoft ou uma conta corporativa ou de estudante. O Visual Studio encontrará uma assinatura do MSDN ou uma assinatura do Visual Studio Team Services associada à sua conta.  
  
> [!IMPORTANT]
>  O Visual Studio procura automaticamente assinaturas online associadas ao se conectar a uma conta do Visual Studio Team Services pela janela de ferramentas do Team Explorer. Quando você se conecta a uma conta do Visual Studio Team Services, pode entrar usando contas da Microsoft ou corporativas ou de estudante. Se houver uma assinatura online para aquela conta de usuário, o Visual Studio automaticamente desbloqueará o IDE para você.  
  
## <a name="to-unlock-visual-studio-with-a-product-key"></a>Para desbloquear o Visual Studio com uma chave do produto (Product Key)  
  
1.  Selecione **Arquivo > Configurações de Conta** para abrir a caixa de diálogo Configurações de Conta e clique no link "**Licenciar com uma Chave do Produto (Product Key)**".  
1.  Insira a chave do produto (Product Key) no espaço fornecido.  
  
> [!TIP]
>  Versões de pré-lançamento do Visual Studio não têm chaves do produto (Product Keys). Você deve entrar no IDE para usar versões de pré-lançamento.  
  
## <a name="address-license-problem-states"></a>Tratar os estados de problema de licença  
  
### <a name="update-stale-licenses"></a>Atualizar licenças obsoletas  
 Você poderá ver a mensagem abaixo informando que sua licença está obsoleta no Visual Studio, indicando "Sua licença ficou obsoleta e deve ser atualizada".
  
 ![Mensagem de licença obsoleta do Visual Studio](~/ide/media/vs2017_stale-license.png)  
  
 Essa mensagem indica que embora sua assinatura ainda possa ser válida, o token de licença que o Visual Studio usa para manter sua assinatura atualizada ainda não foi atualizado e se tornou obsoleto devido a um dos motivos a seguir:  
  
1.  Você não usou o Visual Studio ou não teve uma conexão com a Internet por um longo período.   
1.  Você saiu do Visual Studio.  
  
 Antes de o token de licença se tornar obsoleto, o Visual Studio mostrará primeiro uma mensagem de aviso solicitando que você insira suas credenciais novamente.  
  
 Se você não digitar novamente suas credenciais, o token começará a ficar obsoleto e a caixa de diálogo Configurações da Conta informará quantos dias você ainda tem até seu token expirar totalmente. Depois que o token expirar, você precisará inserir novamente suas credenciais para esta conta ou licença com outro método acima para poder continuar usando o Visual Studio.  
  
> [!Important]
>  Se estiver usando o Visual Studio por longos períodos em ambientes com acesso limitado ou sem acesso à Internet, você deverá usar uma chave do produto (Product Key) para desbloquear o Visual Studio para evitar a interrupção.  
  
### <a name="update-expired-licenses"></a>Atualizar licenças expiradas  
 Se sua assinatura tiver expirado completamente e você não tiver mais direitos de acesso ao Visual Studio, você precisará:  
  
1.  Renovar sua assinatura. Para obter mais informações sobre a licença que você está usando, acesse **Arquivo > Configurações de Conta** e procure as informações de licença no lado direito da caixa de diálogo.  
  
1.  Se você tiver outra assinatura associada a uma conta diferente, adicione essa conta à lista **Todas as Contas** no lado esquerdo da caixa de diálogo **Arquivo > Configurações de Conta**, selecionando o link **Adicionar uma conta...**.  
  
## <a name="see-also"></a>Consulte também  
 [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md) (Entrando no Visual Studio)

