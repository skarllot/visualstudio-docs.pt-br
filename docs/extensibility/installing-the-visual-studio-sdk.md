---
title: Instalar o SDK do Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio
O SDK do Visual Studio é um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalar o SDK do Visual Studio como parte de uma instalação do Visual Studio  
 Se você gostaria de incluir o VSSDK em sua instalação do Visual Studio, você deve instalar o **o desenvolvimento de extensões do Visual Studio** cargas de trabalho em **outros conjuntos de ferramentas**. Isso instalará o SDK do Visual Studio, bem como os pré-requisitos necessários. Você pode ajustar a instalação selecionando ou exibir componentes desmarque o resumo. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalando o SDK do Visual Studio depois de instalar o Visual Studio  
 Se você optar por instalar o SDK do Visual Studio depois de concluir a instalação do Visual Studio, execute novamente o instalador do Visual Studio e selecione o **o desenvolvimento de extensões do Visual Studio** carga de trabalho.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalar o SDK do Visual Studio de uma solução  
 Se você abrir uma solução com um projeto de extensibilidade sem precisar instalar primeiro o VSSDK, você será solicitado por uma barra de informações realçadas acima do Gerenciador de soluções. Ele deve ser semelhante ao seguinte:  
  
 ![SolutionExplorerInstall](~/docs/extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalar o SDK do Visual Studio na linha de comando  
Assim como acontece com qualquer componente ou carga de trabalho do Visual Studio, você também pode instalar o item da linha de comando. Consulte [usar parâmetros de linha de comando para instalar o Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para obter detalhes sobre as opções de linha de comando apropriada e como determinar os identificadores de carga de trabalho ou componente.
  
 Observe que você deve usar o instalador do Visual Studio que corresponda à versão instalada do Visual Studio. Por exemplo, se você tiver o Visual Studio Enterprise instalado no seu computador, você deve executar o instalador do Visual Studio Enterprise (vs_enterprise.exe).
