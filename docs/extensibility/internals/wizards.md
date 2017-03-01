---
title: Assistentes | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: af0466ea3c11b75090e45cb9b408ed0723cd8a6f
ms.lasthandoff: 02/22/2017

---
# <a name="wizards"></a>Assistentes
Depois de criar um assistente, você geralmente deseja adicioná-lo a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrado (IDE) do ambiente de desenvolvimento para que outros possam usá-lo. O assistente adicionado aparece no **adicionar novo projeto** ou **Adicionar Novo Item** caixas de diálogo. Para ver o **adicionar novo projeto** ou **Adicionar Novo Item** caixa de diálogo caixas, clique uma solução aberta no **Solution Explorer**, aponte para **adicionar**e, em seguida, clique em **novo projeto** ou **Novo Item**.  
  
 Assistentes podem ser implementados em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para permitir que os usuários selecionem um modo de exibição de árvore de valores disponíveis quando eles abrirem o **adicionar novo projeto** caixa de diálogo ou o **Add New Item** caixa de diálogo, ou quando eles com o botão direito em um item **Solution Explorer**.  
  
 No assistente, você pode fornecer a opção de localizar o nome de um novo projeto ou HTTP e você pode determinar o ícone que os usuários verão quando eles selecionam o assistente. Você também pode controlar a ordem na qual os novos itens aparecem em relação a outros itens disponíveis; itens não precisam ser organizados em ordem alfabética.  
  
 Você também pode fornecer um assistente que inicia de forma diferente, com base em parâmetros personalizados que são passados para o Assistente quando ele é aberto.  
  
 Os tópicos desta seção discutem os arquivos que você implementar para fazer com que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **adicionar novo projeto** e **Adicionar Novo Item** caixas de diálogo para listar o assistente entre modelos e os assistentes disponíveis e os requisitos que o assistente deve atender para que funcionem corretamente no IDE.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Descrição do modelo do diretório (. Arquivos Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Fornece uma visão geral do modelo de que arquivos de descrição de diretório e explica como eles funcionam no IDE para exibir pastas, arquivos. vsz do assistente e arquivos de modelo que estão associados um projeto nas caixas de diálogo.  
  
 [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Explica como o IDE inicia assistentes e lista as três partes do arquivo. vsz.  
  
 [Interface de assistente (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Descreve o `IDTWizard` interface assistentes devem implementar para trabalhar no IDE.  
  
 [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)  
 Explica como os assistentes são implementados e o que ocorre quando o IDE passa parâmetros de contexto para a implementação.  
  
 [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)  
 Explica como usar parâmetros personalizados para controlar a operação do assistente depois que o assistente for iniciado.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Fornece links para tópicos adicionais que oferecem informações sobre como criar novos tipos de projeto.  
  
 [Passo a passo: Criando um assistente](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Ilustra como criar um assistente.  
  
 [Estendendo projetos](../../extensibility/extending-projects.md)  
 Descreve como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos e soluções para organizar arquivos de código e arquivos de recurso e como implementar o controle de origem.
