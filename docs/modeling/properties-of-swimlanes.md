---
title: Propriedades de raias | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 24
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1b8eacf8fdd74fc9fe0703dc50beb46a2442e939
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-swimlanes"></a>Propriedades de swimlanes
Você pode adicionar raias em um diagrama. As raias dividem um diagrama em áreas verticais ou horizontais. Você pode definir outras formas a ser exibido dentro de raias. Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 As raias têm as propriedades listadas na tabela a seguir.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Cor de preenchimento do corpo|A cor de preenchimento para o corpo da Raia.|Branco|  
|Cor de preenchimento de cabeçalho|A cor de preenchimento para o cabeçalho da Raia.|Azul escuro|  
|Cor do separador|A cor da linha do separador.|LightGray|  
|Estilo de linha do separador|O estilo da linha do separador (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, ou `Custom`).|`Dash`|  
|Espessura do separador|A espessura da linha do separador em polegadas.|0.03125|  
|Cor do texto|A cor usada para decoradores de texto que estão associados este Raia.|Preto|  
|Modificador de acesso|O nível de acesso da classe (`public` ou `internal`).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código que é gerada a partir esse Raia.|\<Nenhum >|  
|Gera dois derivados|Se `True`, uma classe base e uma classe parcial (para oferecer suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de Herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir de Raia (`none`, `abstract` ou `sealed`).|nenhum|  
|Base de Raia|A classe base desse Raia.|(nenhum)|  
|Nome|O nome desse Raia.|Nome atual|  
|espaço de nome|O namespace que é associado a esse Raia.|Namespace atual|  
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (`fixed`, `variable`, ou `none`). Se `fixed`, em seguida, o valor da `Fixed Tooltip Text` propriedade é usada; se `variable`, a dica de ferramenta é definido no código personalizado.|\<Nenhum >|  
|Observações|Notas informais associadas este Raia.|\<Nenhum >|  
|Alinhamento|Alinhamento horizontal ou vertical.|Vertical|  
|Altura inicial|A altura inicial desse Raia, em polegadas. Aplicável somente a raias horizontais.|0|  
|Largura inicial|A largura inicial desse Raia, em polegadas. Aplicável somente a raias verticais.|0|  
|Expõe a cor do texto|Se `True`, o usuário pode definir a cor de uma raia no designer gerado. Para configurar isso, com o botão direito na forma de Raia e clique em **adicionar exposto**.|False|  
|Descrição|Usado para documentar o designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para se referir a essa classe de Raia.|\<Nenhum >|  
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para este Raia.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
