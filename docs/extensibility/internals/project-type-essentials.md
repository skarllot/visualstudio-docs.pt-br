---
title: "Conceitos básicos do tipo de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 11
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
ms.openlocfilehash: 77ac7852a4fe42e69602edcd7e75354b404e315e
ms.lasthandoff: 02/22/2017

---
# <a name="project-type-essentials"></a>Conceitos básicos do tipo de projeto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]inclui vários tipos de projeto para idiomas como [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]também permite que você crie seus próprios tipos de projeto.  
  
 Se você quiser apenas adicionar comandos personalizados, editores ou janelas de ferramenta para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você pode fazer isso sem criar um novo tipo de projeto. Para mais informações, consulte os seguintes tópicos:  
  
-   [Barras de ferramentas, Menus e comandos](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Editor e extensões do serviço de linguagem](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Estendendo e personalizando janelas de ferramenta](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Da mesma forma, se você deseja personalizar o comportamento do fornecido [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos de projeto, você pode fazer isso usando os subtipos de projeto. Para obter mais informações, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
 Você deve criar um novo tipo de projeto para projetos baseados em um idioma diferente do [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] se você deseja oferecer suporte a um ou mais dos seguintes:  
  
-   Build  
  
-   Implantação  
  
-   Várias configurações  
  
-   Controle do código-fonte  
  
-   Depuração  
  
-   Itens de projeto no Solution Explorer  
  
-   O **Abrir projeto** ou **novo projeto** caixas de diálogo  
  
-   Aninhamento de projeto  
  
-   Para obter mais informações sobre os recursos de tipos de projeto, consulte o seguinte:  
  
-   Tipos de projeto são objetos em um VSPackage que implementam o conjunto de interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] espera. Se você estiver usando c# para desenvolver um tipo de projeto, as classes do projeto de estrutura de pacote gerenciado implementam as interfaces necessárias para você e permitem que você herdar dessa implementação. Para obter mais informações, consulte [usando a estrutura de pacote gerenciado para implementar um tipo de projeto (c#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Para desenvolvedores de C++, as classes na biblioteca HierUtil funcionam de maneira semelhante. Para obter mais informações, consulte [fora da compilação: usando Classes do projeto HierUtil7 para implementar um tipo de projeto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Tipos de projeto podem dar suporte a dados diferentes de arquivos de código fonte típico que se baseiam em um assembly .exe ou. dll. Por exemplo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos de banco de dados contêm referências a arquivos de script e consulta armazenados em disco e adicionar comandos ao **Solution Explorer** para executar os scripts e consultas em um banco de dados, mas os projetos não oferecem suporte a comportamento de compilação. Para obter mais informações, consulte [abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Um tipo de projeto não precisa usar arquivos. Por exemplo, um tipo de projeto pode armazenar todos os seus dados em um banco de dados. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]tipos de projeto oferece controle completo sobre como eles persistirem dados para projetos e itens de projeto. Para obter mais informações, consulte [decisões de Design de tipo de projeto](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Tipos de projeto devem fornecer um *factory projeto*, que é um objeto que cria uma instância do projeto sempre que digitar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] foi solicitado a abrir ou criar um projeto com base nesse tipo de projeto. Para obter mais informações, consulte [criar projeto instâncias por usando projeto fábricas](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Tipos de projeto devem fornecer modelos de projetos e itens de projeto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa os modelos quando os usuários criam novos projetos e adicionar novos itens de projetos existentes. Para obter mais informações, consulte [Adicionar projeto e modelos de Item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Tipos de projeto podem dar suporte a várias configurações, como Debug e Release. Os usuários podem alterar as configurações diferentes de um projeto usando páginas de propriedades que você fornecer. Para obter mais informações, consulte [opções de configuração de gerenciamento de](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de projeto de implantação](../../extensibility/internals/deploying-project-types.md)
