---
title: "Preparando extensões para a implantação do Windows Installer | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 15
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
ms.openlocfilehash: d9a7edf62994d8cb69bc0b4652f08652e7c3a589
ms.lasthandoff: 02/22/2017

---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Preparando extensões para a implantação do Windows Installer
Você não pode usar um pacote do Windows Installer (MSI) para implantar um pacote VSIX. No entanto, você pode extrair o conteúdo de um pacote VSIX para implantação MSI. Este documento mostra como preparar um projeto cuja saída padrão é um pacote VSIX para inclusão em um projeto de instalação.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Preparando um projeto de extensão para a implantação do Windows Installer  
 Execute estas etapas em novos projetos de extensão antes de adicionar a um projeto de instalação.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Para preparar um projeto de extensão para a implantação do Windows Installer  
  
1.  Crie um VSPackage, componente MEF, Editor adorno ou outro tipo de projeto de extensibilidade que inclua um manifesto VSIX.  
  
2.  Abra o manifesto VSIX no editor de códigos.  
  
3.  Defina o elemento InstalledByMsi do manifesto VSIX para `true`. Para obter mais informações sobre o manifesto VSIX, consulte [VSIX extensão de esquema 2.0 referência](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Isso impede que o instalador VSIX tentar instalar o componente.  
  
4.  Clique com botão direito no projeto no **Solution Explorer** e clique em **propriedades**.  
  
5.  Selecione o **VSIX** guia.  
  
6.  Marque a caixa denominada **conteúdo VSIX de cópia no seguinte local** e digite o caminho para onde o projeto de instalação irá pegar os arquivos.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extrair arquivos de um pacote existente do VSIX  
 Execute estas etapas para adicionar o conteúdo de um pacote VSIX existente para um projeto de instalação quando você não tiver os arquivos de origem.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Para extrair os arquivos de um pacote existente do VSIX  
  
1.  Renomeie o. Arquivo VSIX que contém a extensão de *filename*. VSIX para *nome de arquivo*. zip.  
  
2.  Copie o conteúdo do arquivo. zip em um diretório.  
  
3.  Exclua arquivo [Content_types]. XML do diretório.  
  
4.  Edite o manifesto VSIX, conforme mostrado no procedimento anterior.  
  
5.  Adicione os arquivos restantes ao seu projeto de instalação.  
  
## <a name="see-also"></a>Consulte também  
 [Implantação de instalador do Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Passo a passo: Criando uma ação personalizada](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)
