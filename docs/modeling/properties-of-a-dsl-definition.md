---
title: "Propriedades de uma definição de DSL | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 13
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7a8fc0474f624785a47a4ba9f970b5a1ca54dd9c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-a-dsl-definition"></a>Propriedades de uma definição de DSL
Definem propriedades de DslDefinition *linguagem específica do domínio* propriedades de definição, como números de versão. As propriedades DslDefinition aparecem no **propriedades** janela quando você clica em uma área aberta do diagrama no *Designer de linguagem específica do domínio*.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition tem as propriedades na tabela a seguir:  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Modificador de acesso|Determina se o modificador de acesso para a classe de domínio público ou interno.|public|  
|Atributos personalizados|Personalizadas definidas atributos para a classe de domínio.<br /><br /> **Observação** Use o botão Procurar para adicionar um atributo.|\<Nenhum >|  
|Nome da Companhia|O nome do nome da empresa no registro do sistema.|Nome da empresa atual|  
|Nome|O nome dessa classe de domínio.|Nome atual|  
|espaço de nome|O namespace associado a essa classe de domínio.|Namespace atual|  
|Guid do pacote|O guid para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacote gerado para esta DSL.|\<Nenhum >|  
|Namespace do pacote|O namespace para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacote gerado para esta DSL.|\<Nenhum >|  
|Nome do produto|O nome do produto que será registrado para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacote gerado para esta DSL.|\<Nenhum >|  
|Observações|Anotações associadas a essa classe de domínio.|\<Nenhum >|  
|Descrição|Descrição para essa classe de domínio.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para esta classe de domínio.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave ajuda associada a essa classe de domínio.|\<Nenhum >|  
|Build|O número de compilação incremental para essa definição de linguagem específica do domínio.|0|  
|Versão Principal|O número de compilação principal incremental para essa definição de linguagem específica do domínio.|1|  
|Versão Secundária |O número da compilação secundária incremental para essa definição de linguagem específica do domínio.|0|  
|Revisão|A revisão incremental número para essa definição de linguagem específica do domínio da compilação.|0|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
