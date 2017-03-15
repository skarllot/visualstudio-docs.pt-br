---
title: Propriedades de diagramas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 25
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fcd30a30bdae896be5aceb9dc685a5fb762ee4af
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-diagrams"></a>Propriedades de diagramas
Você pode definir propriedades que especificam como os diagramas serão exibidos no designer gerado. Por exemplo, você pode especificar uma cor padrão para o texto no diagrama.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 A tabela a seguir lista as propriedades de diagramas.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Cor do preenchimento|A cor de preenchimento para o diagrama.|Branco|  
|Cor do texto|A cor do texto que é exibido no diagrama.|Preto|  
|Modificador de acesso|O modificador de acesso da classe (público ou interno).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe do código gerado.|\<Nenhum >|  
|Gera dois derivados|Se `True`, uma classe base e uma classe parcial (para oferecer suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modificador de Herança|Descreve o tipo de herança da classe de código fonte que é gerado do diagrama (`none`, `abstract` ou `sealed`).|Nenhum|  
|Diagrama base|A classe base deste diagrama.|(nenhum)|  
|Nome|O nome do diagrama.|Nome atual|  
|espaço de nome|O namespace que é associado a este diagrama.|Namespace atual|  
|Classe representada|A classe de domínio raiz que este diagrama representa.|Classe raiz atual se aplicável|  
|Observações|Notas informais associadas esse elemento.|\<Nenhum >|  
|Expõe a cor de preenchimento como propriedade|Se `True`, o usuário pode definir a cor de preenchimento do diagrama do designer gerado. Para configurar isso, clique com botão direito na forma de diagrama e clique em **Explosed adicionar**.|False|  
|Expõe a cor do texto como propriedade|Se `True`, o usuário pode definir a cor do texto do diagrama no designer gerado. Para configurar isso, clique com botão direito na forma de diagrama e clique em **Explosed adicionar**.|False|  
|Descrição|A descrição é usada para documentar o designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para este diagrama.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda F1 do diagrama.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
