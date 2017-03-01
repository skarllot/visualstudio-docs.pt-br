---
title: Web Essentials projeto | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
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
ms.openlocfilehash: 3fa6480780cfaa30b8e384b5cbf3ab44488c8186
ms.lasthandoff: 02/22/2017

---
# <a name="web-project-essentials"></a>Conceitos básicos de projeto da Web
Projetos da Web criar aplicativos Web. Você pode usar um projeto da Web para criar um aplicativo Web que tem inteligentes páginas da Web. Uma página da Web inteligente tem código do lado do servidor que processa a página da Web sob demanda.  
  
 Usando linguagens de programação tradicionais, como [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], você pode criar páginas da Web inteligentes para coletar e processar informações de um usuário, armazene-o em um banco de dados e assim por diante.  
  
-   O modelo code-behind associa arquivos de código fonte dependentes de páginas da Web com o. asmx ou. aspx de extensão de arquivo. Por exemplo, Hello pode ter o hello.aspx.cs de arquivo de código fonte dependentes.  
  
-   O código do lado do servidor associado a uma página da Web inteligente é compilado em um arquivo executável que está localizado na pasta /bin do site.  
  
-   Arquivos de código de origem adicionais, como classes auxiliares que não estão associados uma página da Web específica, estão localizados na pasta /App_Code site da Web.  
  
    -   Um projeto de site da Web (WSP) gera um arquivo executável para cada página da Web inteligente. Arquivos executáveis adicionais são gerados a partir de qualquer arquivo de código fonte na pasta /App_Code.  
  
    -   Um projeto de aplicativo Web (WAP) produz um único arquivo executável que combina o código para todas as páginas da Web inteligentes, bem como todos os arquivos de código-fonte na pasta /App_Code.  
  
-   O arquivo de solução para um projeto da Web está localizado separadamente do site da Web propriamente dito. Por padrão, arquivos de solução estão localizados em \Documents and Settings\\*YourAccount*\My Documents\\*\<Visual Studio # # # >*\Projects\\*YourWebSite*.  
  
    > [!NOTE]
    >  Se você deseja manter o arquivo de solução com o site da Web, movê-lo lá e reabri-lo.  
  
-   Se você abrir um site que não tem nenhum arquivo de solução no Visual Studio, um novo arquivo de solução é gerado automaticamente para ele.  
  
-   Projetos da Web não tem nenhum arquivo de projeto. Informações do projeto são armazenadas no arquivo de solução, o arquivo Web. config e em outro lugar.  
  
-   Adicionando propriedades globais para um projeto Web automaticamente cria um arquivo de armazenamento na pasta de solução de projeto da Web.  
  
-   Uma página da Web inteligente pode ser associada uma linguagem de programação do lado do servidor usando a diretiva de página ou o \<script runat = "server" > marca.  
  
-   Além disso, páginas da Web pode ter qualquer número de blocos de scripts do lado do cliente escritos em qualquer linguagem de script.  
  
-   Um sistema de projeto de site da Web é implementado pela adição de modelos de projeto e item e o registro de [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projeto.  
  
-   Um sistema WAP é implementado como um subtipo de projeto, também chamado de um tipo de projeto. O [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projeto é tipo, o subtipo WAP para criar o sistema WAP. Para obter mais informações sobre os subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
-   Uma página da Web inteligente combina HTML com uma linguagem de programação do lado do servidor. O idioma do servidor é chamado de idioma independente. Para dar suporte a uma linguagem independente, o sistema de projeto da Web deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>família de interfaces.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>  
  
    -   Para oferecer suporte o idioma contido em um editor, o serviço de linguagem HTML deve adiar exibindo código independente de linguagem para um serviço independente de linguagem.  
  
    -   Marcadores de erro (vermelho squigglies) sempre devem ser criados no buffer principal do editor de códigos.  
  
## <a name="see-also"></a>Consulte também  
 [Projetos da Web](../../extensibility/internals/web-projects.md)
