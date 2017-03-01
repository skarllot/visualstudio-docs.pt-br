---
title: 'Como: criar um Atom Feed para uma galeria privada | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 9
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
ms.openlocfilehash: 751b440d51756a98844c0fdd51995dd51a0576ad
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Como: criar um Atom Feed para uma galeria privada
Você pode criar um átomo (RSS) para um local de intranet que contém as extensões e adicionar o feed para **extensões e atualizações** como uma galeria privada. Para obter mais informações, consulte [galerias particular](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Criar um Atom Feed  
 Para criar um feed como uma galeria privada Atom, primeiro, reúna as extensões (arquivos. VSIX) em uma pasta. Você pode organizá-los em subpastas, se desejar. Você precisará também os seguintes recursos:  
  
-   Um arquivo atom.xml que torna as extensões disponíveis como uma galeria privada. Para obter informações sobre como conectar-se o arquivo atom.xml **extensões e atualizações**, consulte [galerias particular](../extensibility/private-galleries.md).  
  
-   Uma pasta que contém os arquivos de imagem que foram extraídos das extensões (por exemplo, capturas de tela). O arquivo atom.xml contém links relativos para essas imagens para que elas estão disponíveis em **extensões e atualizações**.  
  
 Por exemplo, suponha que você coletou as duas extensões a seguir em uma pasta:  
  
-   Template_Wizard_239.VSIX, que é um modelo de projeto do VSIX vazio.  
  
-   SelectionHighlight.vsix, que é uma ferramenta para realçar todas as instâncias de uma palavra selecionada.  
  
 O conteúdo do arquivo atom.xml seria semelhante a exemplo a seguir:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 Observe que as marcas de dois link consultem capturas de tela na pasta gerada de imagens.  
  
## <a name="see-also"></a>Consulte também  
 [Galerias privadas](../extensibility/private-galleries.md)
