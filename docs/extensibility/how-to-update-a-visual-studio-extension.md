---
title: "Como: atualizar uma extensão do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 14
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 04868e6866762c86dabebaf7220080ae9dbdda02
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-update-a-visual-studio-extension"></a>Como: atualizar uma extensão do Visual Studio
Você pode atualizar uma extensão do Visual Studio em seu sistema usando **extensões e atualizações** para instalar a versão atualizada. Se você criar uma versão atualizada de uma extensão, significam como atualizados aumentando o número de versão do manifesto VSIX.  
  
 As atualizações são instaladas quando o manifesto VSIX da extensão de entrada com o mesmo `ID` como o instalado e uma maior `Version` número. Se o `Version` número é igual ou inferior, o pacote não pode ser instalado. Se o `ID` valores não coincidirem, o pacote ainda não estiver instalado é reconhecido como uma extensão separada.  
  
 Para evitar conflitos durante o desenvolvimento, é recomendável que você desinstale as versões anteriores das extensões em andamento e também Desinstale ou desabilite quaisquer outras extensões potencialmente conflitantes.  
  
### <a name="to-update-an-extension-on-your-system"></a>Para atualizar uma extensão no sistema  
  
1.  Sobre o **ferramentas** menu, clique em **extensões e atualizações**.  
  
2.  No painel esquerdo, clique em **atualizações**.  
  
3.  No painel central, clique na atualização que deseja instalar.  
  
     O número de versão da extensão atualizado é exibido no painel à direita, junto com outras informações.  
  
4.  Na parte inferior do painel direito, clique em **atualização**.  
  
### <a name="to-publish-an-update-of-an-extension"></a>Para publicar uma atualização de uma extensão  
  
1.  No Visual Studio, abra a solução para a extensão que você deseja atualizar. Faça as alterações.  
  
    > [!IMPORTANT]
    >  Sem sinal que todas as extensões de usuário não são atualizadas automaticamente. Você sempre deve assinar suas extensões.  
  
2.  Em **Solution Explorer**, abra source.extension.manifest.  
  
3.  No designer de manifesto, aumente o valor do número no **versão** campo.  
  
4.  Salve a solução e compilá-lo.  
  
5.  Carregue o novo arquivo. VSIX (na pasta \bin\Debug\ do projeto) para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web.  
  
     Quando um usuário que tenha uma versão anterior da extensão abre **extensões e atualizações**, a nova versão será exibido no **atualizações** lista, desde que a ferramenta esteja definida para automaticamente procurar atualizações.  
  
     Você pode habilitar ou desabilitar a verificação automática de atualizações na parte inferior da **atualizações** painel (**ativar/desativar a detecção automática de atualizações disponíveis**), as alterações que o **verificar atualizações** definindo em **Ferramentas / opções / ambiente / extensões e atualizações**.  
  
    > [!NOTE]
    >  A partir do Visual Studio 2015 Atualização 2, é possível especificar (em **Ferramentas/Opções/Ambiente/Extensões e Atualizações**) se você deseja atualizações automáticas para extensões por usuário, todas as extensões do usuário ou ambas (a configuração padrão).  
  
## <a name="see-also"></a>Consulte também  
 [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
