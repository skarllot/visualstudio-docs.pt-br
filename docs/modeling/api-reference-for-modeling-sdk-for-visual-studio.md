---
title: "Referência de API do SDK de modelagem para Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 8
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 88a35ad56924c4e1df22927e64a48c42edb21d4d
ms.lasthandoff: 02/22/2017

---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referência de API do SDK de Modelagem para Visual Studio
O Visual Studio SDK de visualização e modelagem fornece a plataforma em que suas ferramentas de linguagens específicas de domínio (DSL) são criadas.  
  
 Esta seção contém material de referência para namespaces que têm nomes que começam com "Microsoft.VisualStudio.Modeling".  
  
|espaço de nome|Conteúdo|  
|---------------|-------------|  
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classes como ModelElement, que é a classe base de todas as classes de domínio que você define em uma DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classes que fazem parte de uma definição de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Os modelo Visualizador de armazenamento e desempenho ferramentas de medição.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classes como ShapeElement, que é a classe base de todas as formas que você define em uma DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de seleção e gestos.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|A API do designer de definição de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classes internas do designer de definição de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permitem estender o designer DSL com comandos, gestos e validação.|  
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensão para ModelElement que implementam extensibilidade de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidade|  
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Permite que você faça a partes de um modelo somente leitura.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|A API do Modelbus, que ajuda a integrar modelos diferentes.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|A caixa de diálogo que permite aos usuários navegarem para modelos e elementos para criar referências do Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|O serviço de seletor.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Estrutura de adaptador do Modelbus para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|A caixa de diálogo Seletor que permite aos usuários navegarem para modelos e elementos para criar referências do Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|A interface entre DSLs e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite definir comandos de menu de atalho (contexto).|  
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName></xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite que você defina restrições de validação.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API para extensibilidade de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md)   
 [Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md)

