---
title: Projetos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
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
ms.openlocfilehash: 842bef303d7a3211b8711920ef6cec357a876f8a
ms.lasthandoff: 02/22/2017

---
# <a name="projects"></a>Projetos
No Visual Studio, os projetos são contêineres que os desenvolvedores usam para organizar arquivos de código fonte e outros recursos que aparecem no **Solution Explorer**. Normalmente, os projetos são arquivos (por exemplo, um arquivo. csproj para um projeto c#) que armazenam referências a arquivos de código fonte e recursos, como arquivos de bitmap. Projetos permitem organizar, compilar, depurar e implantar o código-fonte, as referências a serviços Web e bancos de dados e outros recursos. Os VSPackages pode estender o sistema de projetos do Visual Studio em três maneiras: *tipos de projeto*, *projeto subtipos*, e *ferramentas personalizadas*.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 *Tipos de projeto* adicionar suporte para novos tipos de projetos, como linguagens de programação. Por exemplo, cada idioma com suporte para Visual Studio tem seu próprio tipo de projeto, e o exemplo de integração do IronPython inclui um tipo de projeto para o idioma de IronPython. Você deve criar um tipo de projeto em idiomas diferentes do c# ou Visual Basic para personalizar como itens são criados, depurados, implantados e exibidos no **Solution Explorer**. Para obter mais informações, consulte [tipos de projeto](../../extensibility/internals/project-types.md).  
  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)  
 *Projeto subtipos* são baseados nos tipos de projeto e pode ser usado para personalizar o modo como os projetos são criados, depurados e implantados. O Visual Studio usa subtipos de projeto com projetos de dispositivo inteligente; Personalizar a implantação copiando um programa recentemente criado de um computador de desenvolvimento para o dispositivo de destino. O c# e tipos de projeto do Visual Basic podem ser usados como base para os subtipos de projeto. Tipos de projeto C++ não podem. Seus próprios tipos de projeto também podem ser usados como base para os subtipos de projeto. Para obter mais informações, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
 [Projetos da Web](../../extensibility/internals/web-projects.md)  
 Explica o projeto da Web, que por sua vez, criar aplicativos da Web.  
  
 [Nova geração de projeto: Nos bastidores, parte&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nova geração de projeto: nos bastidores, parte&2;](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Explica o que realmente ocorre quando você cria um novo projeto.  
  
 [Exemplos de VSSDK](../../misc/vssdk-samples.md)  
 Descreve os exemplos de VSSDK que lidam com projetos e soluções.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Dentro do Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Explica os diferentes aspectos de extensibilidade do Visual Studio.
