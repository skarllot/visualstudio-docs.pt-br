---
title: Propriedades de formas de compartimento | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 24
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 007e1a6468429212ba7d1833157a4c9a2e771652
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-compartment-shapes"></a>Propriedades de formas de compartimento
Formas de compartimento são uma das formas que você pode usar para exibir uma classe de domínio em uma linguagem específica do domínio. Você pode expandir e recolher os compartimentos.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Formas do compartimento têm as propriedades listadas na tabela a seguir.  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Padrão expandir o estado recolhido|Se `Expanded`, os compartimentos são mostrados na criação. Se `Collapsed`, eles não são.|Expandido|  
|Cor do preenchimento|A cor de preenchimento dessa forma.|Branco|  
|Modo de gradação de preenchimento|O modo de preenchimento de gradiente dessa forma.|Horizontal|  
|Geometria|A geometria dessa forma (retângulo ou um retângulo arredondado).|Retângulo|  
|Tem pontos de Conexão padrão|Se `True`, a forma usará superior, inferior, esquerda e direita conexão pontos no designer gerado.|False|  
|Cabeçalho de compartimento único está visível|Se `False`e a forma tem um único compartimento, o cabeçalho do compartimento não será visível.|verdadeiro|  
|Cor do contorno|A cor do contorno dessa forma.|Preto|  
|Estilo do contorno tracejado|O estilo do contorno tracejado dessa forma (sólido, tracejado, ponto, Traçoponto, Traçopontoponto, personalizado).|Sólido|  
|Espessura do contorno|A espessura do contorno dessa forma.|0.03125|  
|Cor do texto|A cor usada para decoradores de texto que estão associados essa forma.|Preto|  
|Modificador de acesso|O nível de acesso de forma do compartimento (`public` ou `internal`).|Público|  
|Atributos personalizados|Usado para adicionar atributos para a classe de código de origem que é gerada a partir dessa forma do compartimento|\<Nenhum >|  
|Gera dois derivados|Se `True`, uma classe base e uma classe parcial (para oferecer suporte a personalização por meio de substituições) será gerada. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Tem um construtor personalizado|Se `True`, um construtor personalizado será fornecido no código-fonte. Para obter mais informações, consulte [substituindo e estendendo as Classes geradas por](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de Herança|Descreve o tipo de herança da classe de código fonte que é gerado de forma do compartimento (`none`, `abstract` ou `sealed`).|Nenhum|  
|Forma do compartimento de base|A classe base dessa forma.|(nenhum)|  
|Nome|O nome dessa forma.|Nome atual|  
|espaço de nome|O namespace que é associado a essa forma.|Namespace atual|  
|Tipo de dica de ferramenta|Como a dica de ferramenta é definida (fixo, variável ou nenhum). Se fixo, em seguida, o valor de `Fixed Tooltip Text` propriedade é usada como a dica de ferramenta; se a variável, em seguida, a dica de ferramenta é definida no código personalizado.|nenhum|  
|Observações|Notas informais associadas essa forma.|\<Nenhum >|  
|Altura inicial|A altura inicial dessa forma, em polegadas. Para formas de compartimento, essa é a altura da seção de cabeçalho só e ela não pode ser redimensionada.|1|  
|Largura inicial|A largura inicial dessa forma, em polegadas.|1.5|  
|Cor de preenchimento exposta da propriedade<br /><br /> Modo de gradiente do preenchimento exposto<br /><br /> Exposto a cor do contorno como propriedade<br /><br /> Exposto estilo do contorno tracejado como propriedade<br /><br /> Exposto como propriedade da espessura do contorno<br /><br /> Expõe a cor do texto|Se `True`, o usuário pode definir a propriedade declarada de uma forma. Para definir isso, clique com botão direito a definição de forma e clique em **adicionar exposto**.|False|  
|Descrição|Usado para documentar o designer gerado.|\<Nenhum >|  
|Nome de Exibição|O nome que será exibido no designer gerado para esta forma.|\<Nenhum >|  
|Texto de dica de ferramenta fixo|O texto que é usado para uma dica de ferramenta fixa.|\<Nenhum >|  
|Palavra-chave de ajuda|A palavra-chave que é usada para indexar a Ajuda de F1 para essa forma.|\<Nenhum >|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
