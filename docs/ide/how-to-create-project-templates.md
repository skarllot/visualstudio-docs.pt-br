---
title: Como criar modelos de projeto | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 279a123088308a54dccfa9abe0bfbcdb18e5aaf1
ms.contentlocale: pt-br
ms.lasthandoff: 05/31/2017

---
# <a name="how-to-create-project-templates"></a>Como criar modelos de projeto
Este procedimento permite criar um modelo usando o assistente de **Exportação de Modelo**, que empacota seu modelo em um arquivo .zip. Também é possível criar modelos no formato de arquivo VSIX para implantação aprimorada usando a extensão do Assistente para Exportação de Modelo, usando modelos incluídos no [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)], ou você pode, ainda, criar modelos manualmente.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Para criar um modelo de projeto personalizado com o Assistente de Exportação de Modelo padrão  
  
1.  Criar um projeto.  
  
    > [!NOTE]
    >  Use apenas caracteres identificadores válidos para nomear um projeto que será a origem de um modelo. Um modelo exportado de um projeto nomeado com caracteres inválidos pode causar erros de compilação em projetos futuros baseados no modelo. Para obter mais informações sobre caracteres identificadores válidos, consulte [Nomes de Elementos Declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Edite o projeto até que ele esteja pronto para ser exportado como um modelo.  
  
3.  Conforme apropriado, edite os arquivos de código para indicar em que ponto a substituição de parâmetro deve ocorrer. Para obter mais informações sobre a substituição de parâmetros, consulte [Como substituir parâmetros em um modelo](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  No menu **Projeto**, clique em **Exportar Modelo**. O assistente de **Exportação de Modelo** é aberto.  
  
5.  Clique em **Modelo de Projeto**.  
  
6.  Se você tiver mais de um projeto em sua solução atual, selecione os projetos que deseja exportar como um modelo.  
  
7.  Clique em **Avançar**.  
  
8.  Selecione um ícone e uma imagem de visualização para o modelo. Eles aparecerão na caixa de diálogo **Novo Projeto**.  
  
9. Insira um nome e uma descrição para o modelo.  
  
10. Clique em **Finalizar**. Seu projeto é exportado para um arquivo .zip e colocado no local de saída especificado e, se selecionado, é importado para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Se tiver o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalado, você poderá encapsular o modelo concluído em um arquivo .vsix para implantação usando o modelo **VSIX Project**. Para obter mais informações, consulte [Introdução ao modelo de projeto do VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)   
 [Como criar modelos de item](../ide/how-to-create-item-templates.md)

