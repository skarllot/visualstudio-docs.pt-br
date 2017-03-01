---
title: "Política de modelo e na janela Propriedades | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
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
ms.openlocfilehash: 6445d29ba96c90daf9e1eaaaf6ffae5a4a24721c
ms.lasthandoff: 02/22/2017

---
# <a name="template-policy-and-the-properties-window"></a>Política de modelo e na janela Propriedades
Quando um projeto está contido dentro de um projeto de modelo corporativo, esse projeto de modelo corporativo pode impor a política. Política de modelo torna-se um sistema de restrição que pode ser usado para definir valores padrão para propriedades, ocultar propriedades, adicionar propriedades e assim por diante.  
  
 Usando a diretiva de modelo para controlar a exibição de informações de **propriedades** janela é diferente da implementação <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>lida com propriedades do objeto no nível do componente, enquanto a diretiva de modelo pode ser usada para restringir as propriedades de objeto no nível da solução ou projeto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Em outras palavras  
  
-   Implementar os métodos em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>para determinar o que é exibido o **propriedades** janela para objetos específicos</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
-   Usar a diretiva de modelo no nível de projeto e solução para determinar o que é exibido o **propriedades** janela de objetos especificadas anteriormente  
  
 Usando a diretiva de modelo para restringir seletivamente propriedades específicas no **propriedades** janela quando um item de projeto de um tipo específico é selecionado em **Solution Explorer** pode ser benéfica para todos os membros da equipe de desenvolvimento, trabalhando em um projeto. Por exemplo, usando a diretiva de modelo, você pode configurar todas as informações de cadeia de caracteres de conexão em um banco de dados para desenvolvedores e tornar a cadeia de caracteres de conexão somente leitura. Dessa forma, você pode fornecer uma maneira simples de garantir que cada desenvolvedor usa o caminho correto para acesso a dados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing></xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
