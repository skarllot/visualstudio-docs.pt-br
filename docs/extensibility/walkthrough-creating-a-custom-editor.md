---
title: 'Passo a passo: Criando um Editor personalizado | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 17
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
ms.openlocfilehash: 9fc8462a8807d5a3859ea76ca0b9f6d3a20d71cf
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-custom-editor"></a>Passo a passo: Criando um Editor personalizado
O modelo de projeto de VSPackage pode criar um editor personalizado simple em C++.  O modelo de projeto de VSPackage não oferece suporte a projetos c# ou Visual Basic. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>O modelo de projeto de pacote do Visual Studio  
 O modelo de projeto do pacote do Visual Studio pode ser encontrado no **novo projeto** caixa de diálogo na pasta de extensibilidade do C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Para criar um VSPackage usando o modelo de pacote do Visual Studio  
  
1.  Crie um projeto com o modelo de pacote do Visual Studio.  
  
2.  Selecione o **Editor personalizado** opção e clique em **próxima**. O **opções do Editor** página é exibida.  
  
3.  Digite o nome do seu editor no **nome do Editor** caixa. Digite a extensão de arquivo que você deseja ser associado com seu editor no **extensão** caixa. O editor está disponível para arquivos com essa extensão. A extensão de arquivo é registrada para o Visual Studio apenas, não para o Windows. Digite o nome de arquivo padrão para novos documentos criados com o editor no **nome de arquivo padrão** caixa.  
  
4.  Clique em **concluir** para criar o VSPackage na pasta que você especificou.  
  
### <a name="to-test-your-custom-editor"></a>Para testar o editor personalizado  
  
1.  Sobre o **arquivo** , aponte para **novo** e, em seguida, clique em **arquivo**.  
  
2.  No **modelos instalados** painel do **novo arquivo** caixa de diálogo, selecione o modelo de arquivo, o arquivo tipo que você acabou de registrar.  
  
3.  Clique em **abrir** para exibir e editar o documento.  
  
     O editor dá suporte a operações de recortar e colar, localizar e substituir e abra e de carga.  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)
