---
title: "Interface do usuário das ferramentas de visão geral da linguagem específica do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 25
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d76ed4d14e7333678fcf927dfa1b2f21d8573be5
ms.lasthandoff: 02/22/2017

---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Visão geral da interface de usuário das Ferramentas de Linguagem Específica do Domínio
Quando você abre uma solução de ferramentas de linguagem específica do domínio (ferramentas DSL) em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a interface do usuário será semelhante a figura a seguir.  
  
 ![designer de DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 A tabela a seguir explica como as partes da interface do usuário são usadas.  
  
|**Elemento**|**Definição**|  
|-----------------|--------------------|  
|Diagrama|O diagrama mostra o modelo de domínio.<br /><br /> O diagrama tem dois lados. Um lado define os tipos de elementos em seus modelos. O outro lado define como os modelos serão exibidos na tela.|  
|Caixa de Ferramentas|Arraste as ferramentas da caixa de ferramentas para adicionar classes de domínio e tipos para o diagrama de forma. Para adicionar relações, conectores e mapas de formas, clique na ferramenta, clique em nó de origem no diagrama e, em seguida, o nó de destino.|  
|DSL Explorer|**Gerenciador de DSL** aparece quando uma definição de DSL é a janela ativa. Ele mostra a DSL como uma árvore. Gerenciador de DSL permite editar os recursos do modelo que não são exibidos no diagrama. Por exemplo, você pode adicionar itens de caixa de ferramentas e ative o processo de validação usando o **Gerenciador de DSL**.|  
|Janela de detalhes de DSL|O **detalhes de DSL** janela mostra as propriedades do domínio de elementos do modelo que lhe permitem controlar como os elementos são exibidos e como os elementos são copiados e excluídos.<br /><br /> -Por padrão, o **detalhes de DSL** janela aparece ao lado de **Error List** e **saída** windows.|  
  
## <a name="the-domain-model-diagram"></a>O diagrama de modelo de domínio  
 O diagrama de modelo de domínio é dividido em duas partes. Um lado do diagrama mostra os elementos e as relações no modelo. O outro lado mostra como o modelo é exibido e inclui as formas que são usadas para exibir os elementos e as propriedades do diagrama de modelo. A figura a seguir mostra os elementos do diagrama.  
  
 ![designer de DSL com raias](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 A tabela a seguir explica alguns dos elementos do diagrama de modelo de domínio.  
  
|**Termo**|**Definição**|  
|--------------|--------------------|  
|Classe de domínio|Classes de domínio são os tipos de elementos em seus modelos.<br /><br /> Uma classe de domínio pode aparecer mais de uma vez em um diagrama, se ele é o destino de mais de uma relação.<br /><br /> Para adicionar uma classe de domínio, arraste a ferramenta de classe de domínio do **Toolbox** para o **Classes e relacionamentos** lado do diagrama.|  
|Relação de domínio|Relações de domínio são os tipos de links entre elementos nos seus modelos.<br /><br /> Um *relação incorporada* indica que o elemento de destino é de propriedade ou contido no elemento de origem e aparece como uma linha sólida. Cada elemento em um modelo deve ser o destino de uma relação de incorporação, para que o modelo de uma árvore de formulários. A *relação de referência* indica um link geral entre elementos de modelo e aparece como uma linha tracejada. Qualquer elemento pode ter qualquer número de links de referência.<br /><br /> Criar uma relação clicando na ferramenta sobre o **Toolbox**, clicando na classe de domínio de origem e, em seguida, clicando na classe de destino.|  
|Formas e Conectores|Formas de especificar como os elementos de modelo devem ser exibidos em um diagrama DSL., conectores especificar linhas em um diagrama DSL que pode ser usado para exibir relações.<br /><br /> Para criar uma forma ou um conector, arraste a ferramenta para o **elementos do diagrama** lado do diagrama.|  
|Mapas de formas|Um mapa de forma aparece como uma linha no diagrama de modelo de domínio, uma forma de vinculação para a classe de domínio que ele exibe, ou um conector para a relação de domínio que ele exibe.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral das ferramentas de linguagem específica do domínio](../modeling/overview-of-domain-specific-language-tools.md)   
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md)
