---
title: "Segurança no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 20
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 8e34062596ab2f87ae97934b89b4c292e8f28f32
ms.lasthandoff: 02/22/2017

---
# <a name="security-in-visual-studio"></a>Segurança no Visual Studio
Você deve considerar a segurança em todos os aspectos do desenvolvimento do aplicativo, do design à implantação. Comece executando o Visual Studio com a máxima segurança possível. Consulte [Permissões de usuário](../ide/user-permissions-and-visual-studio.md).  
  
 Para que você desenvolva aplicativos efetivamente seguros, é preciso ter um entendimento básico dos conceitos e dos recursos de segurança das plataformas para as quais você está desenvolvendo. Também é preciso entender as técnicas de codificação segura.  
  
## <a name="understanding-security"></a>Noções básicas de segurança  
 [Segurança](http://msdn.microsoft.com/Library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)  
 Descreve a segurança de acesso do código, a segurança baseada em função, a política de segurança e as ferramentas de segurança do .NET Framework.  
  
 [Defenda seu código com as dez principais dicas de segurança que todo desenvolvedor deve conhecer](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Descreve os problemas com os quais você deve tomar cuidado para que não comprometam os dados ou o sistema.  
  
## <a name="coding-for-security"></a>Codificação de segurança  
 A maioria dos erros de codificação resulta em vulnerabilidades de segurança que ocorrem porque os desenvolvedores fazem suposições incorretas ao trabalhar com a entrada do usuário ou porque eles não entendem completamente a plataforma para a qual estão desenvolvendo.  
  
 [Diretrizes de codificação segura](http://msdn.microsoft.com/Library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)  
 Fornece diretrizes de classificação de componentes para solucionar problemas de segurança.  
  
 [Práticas Recomendadas de segurança](/visual-cpp/top/security-best-practices-for-cpp)  
 Aborda estouros de buffer e a visão completa do recurso de verificações de segurança do Microsoft Visual C++ fornecido pelo sinalizador de tempo de compilação /GS.
