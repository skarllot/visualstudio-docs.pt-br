---
title: Gerenciando recursos de aplicativo (.NET) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 85a03270b20b050cc5ca96f57311c98c0d9b53d1
ms.lasthandoff: 04/05/2017

---
# <a name="managing-application-resources-net"></a>Gerenciando recursos de aplicativo (.NET)
Arquivos de recurso são arquivos que fazem parte de um aplicativo, mas não são compilados, por exemplo, arquivos de ícone ou arquivos de áudio. Como esses arquivos não fazem parte do processo de compilação, você pode alterá-los sem precisar recompilar os binários. Se estiver planejando localizar seu aplicativo, você deverá usar arquivos de recurso para todas as cadeias de caracteres e outros recursos que precisam ser alterados ao localizar o aplicativo.  
  
 Para obter mais informações sobre recursos em aplicativos de área de trabalho do .NET, consulte [Recursos em aplicativos de área de trabalho](http://msdn.microsoft.com/Library/8ad495d4-2941-40cf-bf64-e82e85825890). Para obter mais informações sobre recursos em aplicativos de área de trabalho do C++, consulte [Working with Resource Files](/cpp/windows/working-with-resource-files) (Trabalhando com arquivos de recursos).  
  
 Os Aplicativos da Windows Store usam um modelo de recurso diferente dos aplicativos de área de trabalho. Para obter informações sobre recursos em aplicativos da Windows Store, consulte [Definindo os recursos do aplicativo](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) no site do Centro de Desenvolvimento do Windows.  
  
## <a name="working-with-resources"></a>Trabalho com recursos  
 Em um projeto de código gerenciado, abra a janela Propriedades do projeto (clique com botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecione **Propriedades**, digite **propriedades do projeto** na janela **Início Rápido** ou digite ALT+ENTER na janela **Gerenciador de Soluções**). Selecione a guia **Recursos**. Você poderá adicionar um arquivo .resx se o projeto ainda não contiver um, adicionar e excluir diferentes tipos de recursos e modificar os recursos existentes.  
  
 Para saber como trabalhar com recursos em projetos C++, consulte [Como criar um recurso](http://msdn.microsoft.com/Library/aad44914-9145-45a3-a7d8-9de89b366716).
