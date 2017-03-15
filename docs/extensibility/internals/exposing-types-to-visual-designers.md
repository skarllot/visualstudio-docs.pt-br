---
title: Expondo tipos de Designers visuais | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
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
ms.openlocfilehash: de2985169995fef899ac4e4f0beeb9d7239d935b
ms.lasthandoff: 02/22/2017

---
# <a name="exposing-types-to-visual-designers"></a>Expondo tipos de Designers visuais
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deve ter acesso a definições de classe e tipo em tempo de design para exibir um designer visual. Classes são carregadas de um conjunto predefinido de assemblies que incluem o conjunto completo de dependência do projeto atual (referências além de suas dependências). Ele também pode ser necessário para designers visuais acesso classes e tipos que são definidos nos arquivos gerados por ferramentas personalizadas.  
  
 O [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemas de projeto fornecem suporte para acessar tipos e classes geradas por meio portátil temporário arquivos executáveis (PEs temporária). Qualquer arquivo gerado por uma ferramenta personalizada pode ser compilado em um assembly temporário para que os tipos podem ser carregados a partir desses assemblies e expostos aos designers. A saída de cada ferramenta personalizada é compilada em um PE temporário separado e o sucesso ou fracasso desta compilação temporário depende apenas se o arquivo gerado pode ser compilado. Mesmo que um projeto não pode ser compilado como um todo, individuais PEs temporário ainda pode estar disponível para os designers.  
  
 O sistema de projeto fornece suporte completo para o controle de alterações para o arquivo de saída de uma ferramenta personalizada, desde que essas alterações são o resultado da execução da ferramenta personalizada. Cada vez que a ferramenta personalizada é executada, um novo PE temporário é gerado e notificações apropriadas são enviadas para os designers.  
  
> [!NOTE]
>  Porque o arquivo de geração de executáveis de programas temporários ocorre em segundo plano, sem erros são relatados ao usuário se a compilação falhará.  
  
 Ferramentas personalizadas que tiram proveito do suporte do PE temporária devem seguir as regras a seguir:  
  
-   `GeneratesDesignTimeSource`deve ser definido como 1 no registro.  
  
     Nenhuma compilação do arquivo executável de programa ocorre sem essa configuração.  
  
-   O código gerado deve estar no mesmo idioma em que a configuração do projeto global.  
  
     O PE temporário é compilado, independentemente de qual ferramenta personalizada relata como a extensão solicitada no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>desde que `GeneratesDesignTimeSource` é definido como 1 no registro.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> A extensão não precisa ser. vb,. cs ou. jsl; pode ser qualquer extensão.  
  
-   O código gerado pela ferramenta personalizada deve ser válido e ele deve compilar em seu próprio usando apenas o conjunto de referências presentes no projeto no momento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>termina a execução.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>  
  
     Quando um PE temporário é compilado, o único arquivo de origem fornecido ao compilador é a saída da ferramenta personalizada. Portanto, uma ferramenta personalizada que usa um PE temporário deve gerar arquivos de saída que podem ser compilados independentemente dos outros arquivos no projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao objeto BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementando geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)   
 [Determinando o Namespace padrão de um projeto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Registrar geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md)
