---
title: Portar, migrar e atualizar projetos do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: TerryGLee
ms.author: tglee
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
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Portar, migrar e atualizar projetos do Visual Studio
Ao mudar para uma versão mais recente do Visual Studio, pode ser útil saber se você deve modificar alguma das soluções, projetos, arquivos e outros ativos criados em versões anteriores *antes de* executá-los em versões recentes.

 Muitos ativos amplamente usados se comportam da mesma maneira em nossa versão mais nova, o Visual Studio 2017 RC, da mesma forma que em nossa versão recente, Visual Studio 2015. Eles também se comportarão da mesma forma em nossas versões anteriores, o Visual Studio 2013 e o Visual Studio 2012.

 Por exemplo, no Visual Studio 2017 RC, você pode abrir um projeto que foi criado no Visual Studio 2015 ou Visual Studio 2013, alterá-lo e reabri-lo no Visual Studio 2017 RC; suas alterações serão mantidas e o projeto se comportará da mesma forma que na versão anterior. Isso também vale para muitos ativos que foram criados no Visual Studio 2012.  

 Se usar o Visual Studio 2015 junto com o Visual Studio 2013, Visual Studio 2012 ou Visual Studio 2010 SP1, você também poderá criar e modificar projetos e arquivos em qualquer uma dessas versões. É possível transferir projetos e arquivos entre as versões, contanto que você não adicione recursos que não tenham suporte em uma das versões. (Para obter mais informações sobre quais recursos são específicos para quais versões, consulte nossa [Notas de Versão](https://www.visualstudio.com/vs/release-notes/).)



<!--HONumber=Feb17_HO4-->


