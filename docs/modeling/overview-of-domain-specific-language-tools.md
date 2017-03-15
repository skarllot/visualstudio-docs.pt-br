---
title: "Visão geral das ferramentas de linguagem específica do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 54
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 20d4222f96958a730c563ff9bc84b2b5d0b08538
ms.lasthandoff: 02/22/2017

---
# <a name="overview-of-domain-specific-language-tools"></a>Visão geral das Ferramentas de Linguagem Específica do Domínio
Ferramentas de linguagem específica do domínio (ferramentas DSL), que são hospedados no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vamos criar uma linguagem específica do domínio e, em seguida, gerar tudo o que os usuários devem ter para criar modelos com base no idioma.  
  
 As seguintes ferramentas estão incluídas nas ferramentas de DSL:  
  
-   Assistente de projeto que usa modelos de solução diferentes para ajudá-lo a começar a desenvolver sua linguagem específica do domínio.  
  
-   Um designer gráfico para criar e editar a definição de linguagem específica do domínio.  
  
-   Um mecanismo de validação que garante que a definição de linguagem específica do domínio é bem formada e exibe os erros e avisos se houver problemas.  
  
-   Um gerador de código que usa uma definição de linguagem específica do domínio como entrada e produz código-fonte como saída.  
  
## <a name="the-dsl-tools-solution"></a>A solução de ferramentas DSL  
 O Assistente de Designer específico do domínio fornece os seguintes modelos de solução:  
  
-   Fluxo de tarefa  
  
-   Diagramas de classe  
  
-   Linguagem mínima  
  
-   Modelos do componente  
  
-   WPF mínima  
  
-   Windows mínima  
  
-   Biblioteca DSL  
  
 Para obter mais informações, consulte [escolhendo um modelo de solução de linguagem específica do domínio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 O assistente cria um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução que tem os seguintes projetos:  
  
-   DSL  
  
     O projeto Dsl define a linguagem específica do domínio e suas ferramentas de edição e o processamento.  
  
-   **DslPackage**  
  
     O projeto DslPackage determina como integram as ferramentas de linguagem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>A Interface gráfica de ferramentas DSL  
 Você pode usar a interface gráfica de ferramentas DSL para adicionar elementos e relações para sua linguagem específica do domínio. Depois de adicionar os elementos, você pode definir sua aparência mapeando-os às formas, personalizando cores e adicionando decoradores. Você também pode adicionar os elementos a caixa de ferramentas.  
  
## <a name="validation-in-dsl-tools"></a>Validação em ferramentas DSL  
 DSL fornece um nível de validação para verificar se o modelo de domínio atende os requisitos básicos para geração de código. Normalmente, quando você cria sua própria linguagem específica do domínio, você poderia adicionar sua própria validação para expressar as regras de lógica de negócios. Para obter mais informações sobre validação personalizada, consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).  
  
 É recomendável que você valide sua linguagem específica do domínio geralmente quando você criá-lo. Se a sua linguagem específica do domínio tem erros de validação, você não pode gerar o código-fonte. O processo de geração de código-fonte dos modelos é executado clicando **transformar todos os modelos** na barra de ferramentas do Gerenciador de soluções. Sempre que você modificar a definição de linguagem, certifique-se de **transformar todos os modelos**. Para obter mais informações, consulte [como: criar uma solução de linguagem específica do domínio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Personalização das ferramentas DSL  
 Você pode fornecer código adicional para refinar o comportamento do modelo e definir restrições em seu idioma. Se necessário, você pode fazer alterações significativas, modificando os modelos de texto.  
  
## <a name="distributing-your-dsl-solution"></a>Distribuir sua solução DSL  
 Ferramentas DSL gera um pacote hospedado em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. O pacote exibe uma caixa de ferramentas, um Gerenciador de DSL e outros elementos de interface do usuário que permitem aos usuários criar modelos usando a sua linguagem específica do domínio.  
  
 Quando você compilar e executar a solução de ferramentas DSL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], uma segunda instância do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mostra a aparência de sua linguagem específica do domínio para o usuário da linguagem. Depois de verificar se tudo está funcionando corretamente, você pode distribuir o `.vsix` arquivo será localizado na pasta de compilação do projeto DslPackage. Esse arquivo pode ser usado para instalar a DSL como uma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão em outros computadores.  Para obter mais informações, consulte [implantar soluções de linguagem específica do domínio](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Consulte também  
 [A instância Experimental](../extensibility/the-experimental-instance.md)   
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
