---
title: Atributos de suporte do Site da Web | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
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
ms.openlocfilehash: dba1aeb8f8e3ad368f050ef425f76cc6c94f99e8
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support-attributes"></a>Atributos de suporte do Site da Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Projeto de site pode ser estendido para oferecer suporte para Web linguagens de programação. O idioma deve ser registrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que os modelos de projeto podem aparecer no **New Web Site** caixa de diálogo quando o idioma é selecionado.  
  
 O exemplo do Studio de IronPython inclui suporte de site. Você pode encontrar com o [VSSDK exemplos](../../misc/vssdk-samples.md). Ele inclui as seguintes classes de atributo para registrar o IronPython como uma linguagem de code-behind para novos projetos da Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Esse atributo é colocado no projeto de linguagem. Ele adiciona o idioma para a lista de idiomas em de programação da Web a **idioma** lista no **New Web Site** caixa de diálogo. Por exemplo, o seguinte adiciona IronPython à lista:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Esse atributo também define o caminho de modelos para apontar para a pasta de modelos. Para obter mais informações sobre o local da pasta de modelos, consulte [modelos de suporte do Site](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Esse atributo é colocado no projeto de linguagem. Ele permite que o projeto de Site da Web aninhar um tipo de arquivo (relacionado) em outro tipo de arquivo (primário) no **Solution Explorer**.  
  
 Por exemplo:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Especifica que um arquivo de code-behind do IronPython está relacionado a um arquivo. aspx. Quando uma nova página da Web. aspx é criada em uma solução de site da Web da IronPython, um novo arquivo de origem de py é gerado e aparece como um nó filho da página. aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Esse atributo é colocado no pacote de idiomas do projeto. Seleciona o provedor do Intellisense para o idioma.  
  
 Por exemplo:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Especifica que uma instância de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, devem ser criadas sob demanda para fornecer serviços de linguagem.</xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>  
  
 A implementação IVsIntellisenseProject trata referências e chama o compilador de linguagem quando uma página da Web com o código é solicitada, mas não é armazenado em cache.  
  
## <a name="see-also"></a>Consulte também  
 [Suporte do Site da Web](../../extensibility/internals/web-site-support.md)
