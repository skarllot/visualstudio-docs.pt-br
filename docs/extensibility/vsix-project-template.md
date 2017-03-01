---
title: Modelo de projeto do VSIX | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 21
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
ms.openlocfilehash: 63aeb94ca42ed7bc0fdd51072021aaa90ad5ff33
ms.lasthandoff: 02/22/2017

---
# <a name="vsix-project-template"></a>Modelo de projeto do VSIX
Você pode usar o modelo de projeto do VSIX para encapsular uma ou mais extensões do Visual Studio em um projeto do VSIX e, em seguida, publique o pacote no [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web.  
  
 Oferece suporte à implantação VSIX VSPackages, assemblies, componentes MEF, modelos de projeto, modelos de item, controles de caixa de ferramentas e tipos de extensão personalizada.  
  
> [!NOTE]
>  Para usar projetos do VSIX, você deve instalar o SDK do Visual Studio. Para obter mais informações sobre o SDK do Visual Studio, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="where-to-find-the-vsix-project-template"></a>Onde encontrar o modelo de projeto do VSIX  
 O modelo de projeto do VSIX está disponível na **novo projeto** caixa de diálogo. Expanda o **Visual Basic** nó ou o **Visual C#** nó e escolha **extensibilidade**.  
  
> [!TIP]
>  Você deve certificar-se que o .NET Framework 4.5 ou superior é especificado na lista suspensa na parte superior do **novo projeto** caixa de diálogo.  
  
## <a name="uses-of-the-vsix-project-template"></a>Usos do modelo de projeto do VSIX  
 O modelo de projeto do VSIX tem dois usos principais:  
  
-   Para implantar modelos de projeto, modelos de item e outras extensões que não têm suporte do VSIX.  
  
-   Para encapsular as saídas de várias extensões em pacote de uma implantação.  
  
 Você não precisa usar o modelo de projeto do VSIX para implantar os VSPackages ou outros tipos de extensões que tenham VSIX suporte.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empacotando a extensão em um projeto do VSIX vazio  
 Você pode empacotar uma extensão existente ou uma extensão que não tenham VSIX suporte, encapsulando-os em um projeto do VSIX vazio. A extensão a ser encapsulada deve ser de um tipo que é compatível com o [esquema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Para empacotar uma extensão usando um projeto do VSIX  
  
1.  Crie os projetos que compõem sua extensão.  
  
2.  Criar um projeto do VSIX usando o **projeto VSIX** modelo.  
  
     Source.Extension.vsixmanifest abre em **Designer de manifesto**.  
  
3.  Sobre o **ativos** guia, escolha o **novo** botão.  
  
     O **adicionar novo ativo** caixa de diálogo é exibida.  
  
4.  No **tipo** lista, escolha o tipo de extensão para adicionar.  
  
5.  Para adicionar um elemento de extensão ou conteúdo que está incluído na solução atual (por exemplo, um modelo de item ou um assembly compilado), execute as seguintes etapas:  
  
    1.  No **fonte** , escolha **um projeto na solução atual**.  
  
    2.  No **projeto** lista, escolha o nome da extensão.  
  
    3.  No **inserir nessa pasta** , digite o nome de uma pasta na qual incorporar o ativo e, em seguida, escolha o **Okey** botão.  
  
6.  Para adicionar uma extensão ou um elemento de conteúdo que não está incluído na solução atual, execute as seguintes etapas:  
  
    1.  No **fonte** caixa de listagem, escolha **arquivo no sistema de arquivos**.  
  
    2.  No **caminho** campo, digite o caminho completo para o arquivo de extensão compilado ou compactado ou usar o **procurar** botão para procurar o arquivo.  
  
    3.  No **inserir nessa pasta** , digite o nome de uma pasta na qual incorporar o ativo e, em seguida, escolha o **Okey** botão.  
  
7.  Se desejar que seu pacote incluir extensões adicionais, você deve adicioná-los da mesma maneira.  
  
8.  Compile a solução.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]cria um arquivo. VSIX que contém um arquivo de manifesto VSIX, um arquivo do [Content_Types]. XML e todos os ativos de extensão que você adicionou ao projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de esquema 2.0 de extensão do VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
