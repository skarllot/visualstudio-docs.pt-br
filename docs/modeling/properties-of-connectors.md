---
title: Propriedades de conectores | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 21
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 503f171b2af5e06fd3c890caf07525ba880d0658
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-connectors"></a>Propriedades de conectores
Conectores representam relações de domínio em um designer gerado.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Conectores têm as propriedades listadas na tabela a seguir.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Cor|A cor deste conector.|Preto|  
|Estilo do tracejado|O estilo de traço para a linha para esse conector (sólido, tracejado, ponto, Traçoponto, Traçopontoponto ou personalizado).|Sólido|  
|Estilo de final do código-fonte|O estilo de final de origem para esse conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou None).|Nenhum|  
|Estilo do destino final|O estilo de final de destino para esse conector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond ou None).|Nenhum|  
|Cor do texto|A cor usada para decoradores de texto que estão associados esse conector.|Preto|  
|Espessura|A espessura da linha para esse conector, medida em polegadas.|0.03125|  
|Modificador de acesso|O nível de acesso da classe (`public` ou `internal`).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código de origem que é gerada a partir desse conector.|\<Nenhum >|  
|Gera dois derivados|Se `True`, uma classe base e uma classe parcial (para oferecer suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de Herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir do conector (`none`, `abstract` ou `sealed`).|nenhum|  
|Conector de base|A classe base deste conector.|(nenhum)|  
|Nome|O nome desse conector.|Nome atual|  
|espaço de nome|O namespace que é associado a esse conector.|Namespace atual|  
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixo, variável ou nenhum). Se fixo, em seguida, o valor de `Fixed Tooltip Text` propriedade é usada como a dica de ferramenta; se a variável, em seguida, a dica de ferramenta é definida no código personalizado.|\<Nenhum >|  
|Observações|Notas informais associadas esse conector.|\<Nenhum >|  
|Estilo de roteamento|O estilo que é usado para o conector de roteamento. A `Rectilinear` conector torna ativa ângulo à direita conforme necessário; um `Straight` conector não.|Retilíneo|  
|Cor exposto como propriedades<br /><br /> Estilo do traço expostos como propriedade<br /><br /> Espessura exposta como propriedade<br /><br /> Expõe a cor do texto|Se `True`, o usuário pode definir a propriedade declarada de uma forma. Para definir isso, clique com botão direito a definição de forma e clique em **adicionar exposto**.|False|  
|Descrição|Usado para documentar o designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para esse conector.|\<Nenhum >|  
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para esse elemento.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
