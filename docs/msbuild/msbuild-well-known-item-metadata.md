---
title: Metadados de itens conhecidos do MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 89e1497061d0720590d8abd6e35fbb3422ba51ef
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-well-known-item-metadata"></a>Metadados de itens conhecidos do MSBuild
A tabela a seguir descreve os metadados atribuído a cada item no momento da criação. Em cada exemplo, a seguinte declaração de item foi usada para incluir o arquivo `C:\MyProject\Source\Program.cs` no projeto.  
  
```xml  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Metadados de item|Descrição|  
|-------------------|-----------------|  
|%(FullPath)|Contém o caminho completo do item. Por exemplo:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Contém o diretório raiz do item. Por exemplo:<br /><br /> `C:\`|  
|%(Filename)|Contém o nome do arquivo do item, sem a extensão. Por exemplo:<br /><br /> `Program`|  
|%(Extension)|Contém a extensão de nome de arquivo do item. Por exemplo:<br /><br /> `.cs`|  
|%(RelativeDir)|Contém o caminho especificado no atributo `Include`, até a barra invertida final (\\). Por exemplo:<br /><br /> `Source\`|  
|%(Directory)|Contém o diretório do item, sem o diretório raiz. Por exemplo:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Se o atributo `Include` contiver o caractere curinga \*\*, esses metadados especificarão a parte do caminho que substitui o caractere curinga. Para obter mais informações sobre curingas, consulte [Como selecionar os arquivos a serem compilados](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Se a pasta *C:\MySolution\MyProject\Source\\* contiver o arquivo Program.cs e se o arquivo de projeto contiver este item:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> em seguida, o valor de `%(MyItem.RecursiveDir)` seria *MySolution\MyProject\Source\\*.|  
|%(Identity)|O item especificado no atributo `Include`. Por exemplo:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Contém o carimbo de data/hora da última vez que o item foi modificado. Por exemplo:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Contém o carimbo de data/hora de quando o item foi criado. Por exemplo:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Contém o carimbo de data/hora da última vez que o item foi acessado.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Consulte também  
 [Itens](../msbuild/msbuild-items.md)   
 [Envio em lote](../msbuild/msbuild-batching.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)
