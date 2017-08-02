---
title: Estendendo propriedades | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 18
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
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>Estendendo propriedades
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **propriedades** janela é um navegador de propriedade universal para componentes COM e COM+ e oferece suporte a todos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] produtos. O **propriedades** janela funciona com `ITypeInfo` digite informações e metadados COM+ para listar as propriedades de tempo de design para o objeto atualmente selecionado em qualquer outra janela no ambiente de desenvolvimento integrado (IDE).  
  
 O **propriedades** janela, que pode ser aberta pressionando F4 no teclado ou selecionando **janela propriedades** no **exibição** menu, é usado para exibir e editar propriedades de tempo de design, independente de configuração e os eventos dos objetos selecionados. Propriedades de configuração dependente, associadas com soluções e projetos, são exibidas na [páginas de propriedade](../../extensibility/internals/property-pages.md). Para obter mais informações, consulte [NIB: Project Properties](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [opções de configuração de gerenciamento de](../../extensibility/internals/managing-configuration-options.md), e [NIB: Item Management in Projects](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Visão geral da janela Propriedades](~/docs/extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Janela de Propriedades  
  
 Esta seção fornece informações detalhadas que se relacionam às áreas individuais do **propriedades** janela e as interfaces que você deve implementar e chamada para preencher a janela.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral da janela Propriedades](../../extensibility/internals/properties-window-overview.md)  
 Explica a finalidade do **propriedades** janela em relação a janela da ferramenta e a janela de documento.  
  
 [Política de modelo e na janela Propriedades](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Discute como um projeto está contido em um projeto de modelo corporativo e como esse projeto de modelo corporativo pode impor a política.  
  
 [Interfaces e os campos da janela de propriedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Explica a base para a seleção que determina quais informações são exibidas no **propriedades** janela.  
  
 [Lista de objetos de janela de propriedades](../../extensibility/internals/properties-window-object-list.md)  
 Descreve a finalidade de **propriedades** lista de objetos de janela, descrevendo como, quando um objeto diferente desta lista dispara uma chamada, o ambiente é informado que um novo objeto foi selecionado.  
  
 [Botões da janela de propriedades](../../extensibility/internals/properties-window-buttons.md)  
 Explique a finalidade dos botões de quatro padrão exibidos no **propriedades** de ferramentas da janela.  
  
 [Grade de exibição de propriedades](../../extensibility/internals/properties-display-grid.md)  
 Explica onde os nomes de propriedade e os campos de valores de propriedade são encontrados na grade.  
  
 [Anunciando o acompanhamento da seleção da janela Propriedades](../../misc/announcing-property-window-selection-tracking.md)  
 Descreve a seleção de controle para o **propriedades** janela.  
  
 [Ocultar propriedades que têm propriedades filho](../../misc/hiding-properties-that-have-child-properties.md)  
 Explica como ocultar propriedades que têm propriedades filho Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
 [Fornecendo uma janela Propriedades personalizada](../../misc/providing-a-custom-properties-window.md)  
 Detalha as etapas para fornecer seu próprio navegador de propriedade.  
  
 [Obtendo descrições dos campos na janela Propriedades](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Explica onde encontrar a área de descrição que exibe informações relacionadas ao campo de propriedade selecionada.  
  
 [Atualizando valores de propriedade na janela Propriedades](../../misc/updating-property-values-in-the-properties-window.md)  
 Fornece instruções passo a passo que mostram as duas formas de manter o **propriedades** janela sincronizadas com as alterações de valor de propriedade.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de projeto](../../extensibility/internals/project-types.md)  
 Discute projetos como os blocos de construção de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compilando e criando](../../ide/compiling-and-building-in-visual-studio.md)  
 Descreve como você pode usar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plataforma para continuamente testar e depurar aplicativos ao criá-los.  
  
 [Propriedades do documento HTML, janela de propriedades](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Fornece instruções para editar um documento HTML diretamente na janela de propriedades e fornece uma tabela detalhando os campos em um documento HTML na janela Propriedades.  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Descreve o `IDispatch` interface, que primeiro foi projetado para oferecer suporte a automação, fornecendo um mecanismo de associação tardia para acessar e recuperar informações sobre os métodos e propriedades de um objeto.  
  
 [NIB: Introdução a propriedades dinâmicas (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 Fornece uma visão geral das propriedades dinâmicas que permitem que você configure seu aplicativo para que os valores de propriedade são armazenados em um arquivo de configuração externo em vez de código compilado do aplicativo.  
  
 [NIB: projetos como contêineres](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 Descreve a função do projeto como um contêiner em uma solução para gerenciar, criar e depurar os itens que compõem o aplicativo logicamente.  
  
 [Propriedades do projeto de PONTA:](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Descreve como o projeto gerencia configurações que permitem que você controle propriedades que se aplicam a todo o projeto e também que são limitadas a determinadas configurações de compilação do projeto.  
  
 [Soluções e projetos](../../ide/solutions-and-projects-in-visual-studio.md)  
 Explica como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerencia com eficiência os itens como referências, conexões de dados, pastas e arquivos que são exigidos por seu esforço de desenvolvimento por meio de soluções e projetos.  
  
 [Estendendo a outras partes do Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] serviços para criar elementos de interface do usuário que correspondem ao restante da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
