---
title: "Propriedades de relações de domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 20
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 011be65e453de8f9d8010b74670b4efdf7905d06
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-domain-relationships"></a>Propriedades de relacionamentos de domínio
As propriedades na tabela a seguir são associadas uma relação de domínio. Para obter informações sobre relações de domínio, consulte [compreensão de modelos, Classes e relacionamentos](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Modificador de acesso|O nível de acesso da relação de domínio (`public` ou `internal`).|`public`|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código de origem que é gerada a partir de relação de domínio.|\<Nenhum >|  
|Gera dois derivados|Se `True`, uma classe base e uma classe parcial (para oferecer suporte a personalização por meio de substituições) é gerado. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Tem um construtor personalizado|Se `True`, indica que um construtor personalizado é fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificador de Herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir de relação de domínio (`none`, `abstract` ou `sealed`).|\<Nenhum >|  
|Permite duplicatas|Se `True`, links duplicados da relação de domínio pode ser criado entre os mesmos dois elementos.|`False`|  
|Relações de base|Se a relação de domínio é derivada, a relação de base da relação de domínio.|\<Nenhum >|  
|Está inserindo|Se `True`, a relação de domínio é uma relação de incorporação. Se `False`, a relação é uma relação de referência.|\<ambos >|  
|Nome|O nome da relação de domínio.|Nome atual|  
|espaço de nome|O namespace associado a relação de domínio.|Namespace atual|  
|Observações|Notas informais associadas a relação de domínio.|\<Nenhum >|  
|Descrição|A descrição que é usada para documentar código e é usada na interface do usuário do designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que é exibido no designer gerado para a relação de domínio.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a Ajuda F1 para a relação de domínio.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
