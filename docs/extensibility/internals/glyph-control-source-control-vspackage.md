---
title: Controle de glifo (VSPackage de controle de origem) | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 20
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
ms.openlocfilehash: 9e47179734911412cab82e7efd54b498046f05c5
ms.lasthandoff: 02/22/2017

---
# <a name="glyph-control-source-control-vspackage"></a>Controle de glifo (VSPackage de controle de origem)
Parte da profunda integração disponível para os VSPackages do controle de origem é a capacidade de exibir suas próprias glifos para indicar o status dos itens no controle de origem.  
  
## <a name="levels-of-glyph-control"></a>Níveis de controle de glifo  
 Um glifo de estado é um ícone que indica o status atual de um item quando exibidas, por exemplo **Solution Explorer** ou **Class View**. Um controle de origem VSPackage pode exercer dois níveis de controle de glifo. Ele pode limitar a escolha de glifos para um conjunto predefinido de glifos fornecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE ou pode definir um conjunto personalizado de glifos para ser exibido.  
  
### <a name="default-set-of-glyphs"></a>Conjunto padrão de glifos  
 Para determinar os glifos de estado que estão associados um item no **Solution Explorer**, um projeto solicita o glifo de estado do controle de origem usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> Um controle de fonte VSPackage pode optar por manter a opção de glifos limitado a glifos predefinidos fornecidos pelo IDE. Nesse caso, o VSPackage volta passa uma matriz de valores que representam as enumerações de glifos que são definidas em vsshell.idl. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Este é um conjunto predefinido de glifos definida pelo IDE, como um cadeado para glifo "Check In" e uma marca de seleção como o glifo "Check-Out".</xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>  
  
### <a name="custom-set-of-glyphs"></a>Conjunto personalizado de glifos  
 Um controle de origem VSPackage pode usar seus próprio glifos para uma exclusiva "aparência" quando ele está instalado. Quando um novo controle de origem VSPackage está ativo, ele deve ser capaz de começar a usar seus próprio glifos mesmo se uma fonte anterior controlar VSPackage ainda é carregado mas inativo. Nesse modo, o controle de origem VSPackage ainda pode usar os ícones existentes para manter uma aparência consistente com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se ele escolhe.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>serviço oferece suporte a uma interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, que pode implementar o VSPackage e que será solicitado pelo IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> </xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Quando o IDE faz uma solicitação, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] por sua vez tentar obter essa interface o registrados atualmente do controle de origem VSPackage. Se a interface existir o VSPackage registrado, a solicitação do IDE para glifos personalizados for bem-sucedida; Caso contrário, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE usa seu conjunto padrão de glifos.  
  
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>método é usado pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obter uma lista de imagens, mostrando o controle da fonte de vários estados.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> O controle de origem VSPackage retorna ao IDE um identificador para a lista de imagens para seus glifos personalizados. O IDE faz uma cópia da lista de imagens neste ponto e usa-o posteriormente para escolher os glifos para exibir. Se não há suporte para a nova interface ou a `IVsSccGlyphs::GetCustomGlyphList` método retornar E_NOTIMPL, em seguida, o IDE obtém seus glifos na lista padrão de glifos fornecido pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon></xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager></xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
