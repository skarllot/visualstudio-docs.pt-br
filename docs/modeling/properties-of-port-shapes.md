---
title: Propriedades de formas de porta | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 21
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6a645957ce06f77fe9cfb9d3bc3475a21a4213d6
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-port-shapes"></a>Propriedades de formas de porta
Você pode usar formas de porta para representar as classes de domínio no designer gerado.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formas de porta têm as propriedades listadas na tabela a seguir.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Cor do preenchimento|A cor de preenchimento dessa forma.|Branco|  
|Modo de gradação de preenchimento|O modo de preenchimento de gradiente dessa forma.|Horizontal|  
|Geometria|A geometria dessa forma (retângulo, retângulo arredondado, elipse ou um círculo).|Retângulo|  
|Tem pontos de Conexão padrão|Se `True`, a forma usará superior, inferior, esquerda e direita conexão pontos no designer gerado.|False|  
|Cor do contorno|A cor do contorno dessa forma.|Preto|  
|Estilo do contorno tracejado|O estilo do contorno tracejado dessa forma (sólido, tracejado, ponto, Traçoponto, Traçopontoponto ou personalizado).|Sólido|  
|Espessura do contorno|A espessura do contorno dessa forma.|0.03125|  
|Cor do texto|A cor usada para decoradores de texto que estão associados essa forma.|Preto|  
|Modificador de acesso|O nível de acesso da classe (`public` ou `internal`).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código de origem que é gerada a partir dessa forma.|\<Nenhum >|  
|Gera dois derivados|Se `True`, uma classe base e uma classe parcial (para oferecer suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|Tem um construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de Herança|Descreve o tipo de herança da classe de código fonte que é gerada a partir da porta (`none`, `abstract` ou `sealed`).|nenhum|  
|Porta de base|A classe base dessa forma.|(nenhum)|  
|Nome|O nome dessa forma.|Nome atual|  
|espaço de nome|O namespace que é associado a essa forma.|Namespace atual|  
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixo, variável ou nenhum). Se fixo, em seguida, o valor de `Fixed Tooltip Text` propriedade é usada como a dica de ferramenta; se a variável, em seguida, a dica de ferramenta é definida no código personalizado.|nenhum|  
|Observações|Notas informais associadas essa forma.|\<Nenhum >|  
|Altura inicial|A altura inicial dessa forma, em polegadas.|1|  
|Largura inicial|A largura inicial dessa forma, em polegadas.|1.5|  
|Cor de preenchimento exposta da propriedade<br /><br /> Modo de gradiente do preenchimento exposto<br /><br /> Exposto a cor do contorno como propriedade<br /><br /> Exposto estilo do contorno tracejado como propriedade<br /><br /> Exposto como propriedade da espessura do contorno<br /><br /> Expõe a cor do texto|Se `True`, o usuário pode definir a propriedade declarada de uma forma. Para definir isso, clique com botão direito a definição de forma e clique em **adicionar exposto**.|False|  
|Descrição|Usado para documentar o designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para esta forma.|\<Nenhum >|  
|Texto da dica de ferramenta fixa|O texto que é usado para uma dica de ferramenta fixa.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para essa forma.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
