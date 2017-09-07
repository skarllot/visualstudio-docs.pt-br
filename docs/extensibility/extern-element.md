---
title: Elemento externo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
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
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d4559aa03af16faf955594c3850281e6cf7b4903
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="extern-element"></a>Elemento extern
O elemento externo faz referência a qualquer arquivo de cabeçalho externo (. h) para mesclar com o arquivo. VSCT em tempo de compilação. Os arquivos a serem mescladas devem estar no caminho de inclusão fornecida ao compilador VSCT ou referenciada por uma [incluir elemento](../extensibility/include-element.md). Os arquivos podem ser outros arquivos. VSCT ou arquivos de cabeçalho do C++.  
  
 Definições em arquivos de cabeçalho devem estar no formato "#define [símbolo] [valor]" o valor pode ser outro símbolo se ele for definido anteriormente. Definições podem ser usadas em instruções condicionais de itens do comando. Nenhum símbolo usado na verdade não será descartado.  
  
 Elemento CommandTable  
Elemento extern  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|href|Necessário. O caminho para o arquivo de cabeçalho:<br /><br /> href="stdidcmd.h"|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|linguagem|Opcional. O idioma padrão de todos os [ \<cadeias de caracteres >](../extensibility/strings-element.md) elementos na tabela de comandos:<br /><br /> Language = "en-us"|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|nenhuma.|nenhuma.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam comandos — ou seja, itens de menu, menus, barras de ferramentas e caixas de combinação, que fornece um VSPackage ao IDE.|  
  
## <a name="example"></a>Exemplo  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Como VSPackages adicionar elementos da Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
