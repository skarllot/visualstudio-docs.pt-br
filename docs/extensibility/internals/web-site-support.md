---
title: Suporte de Site | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 17
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 636cbee868bb53be2d0ef85bd309459570eb84c0
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support"></a>Suporte do Site da Web
Um sistema de projeto de site da Web é um sistema de projeto que cria projetos da Web. Projetos da Web por sua vez criar aplicativos Web. Um projeto de site gera um arquivo executável para cada página da Web que tem o código associado. Arquivos executáveis adicionais são gerados a partir de arquivos de código fonte na pasta /App_Code.  
  
 Sistemas de projeto de site da Web são criados com a adição de modelos e atributos de registro para um sistema de projeto existente. Um desses atributos seleciona o provedor do IntelliSense para o idioma. A implementação do provedor IntelliSense trata referências e chama o compilador de linguagem quando uma página da Web inteligente não armazenada em cache é solicitada.  
  
 O compilador de linguagem usado para compilar páginas da Web deve ser registrado com [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Você pode usar o [ \<compilador > elemento](http://msdn.microsoft.com/Library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) em um arquivo Web. config para registrar o compilador, como no exemplo a seguir:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modelos de suporte do Site da Web](../../extensibility/internals/web-site-support-templates.md)  
 Lista os modelos que você pode usar para criar novos projetos de site da Web e itens associados.  
  
 [Atributos de suporte do Site da Web](../../extensibility/internals/web-site-support-attributes.md)  
 Apresenta os atributos de registro que se conectam a um projeto de site da Web para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Projetos da Web](../../extensibility/internals/web-projects.md)  
 Apresenta uma visão geral dos dois tipos de projetos da Web, projetos de site da Web e projetos de aplicativos Web.
