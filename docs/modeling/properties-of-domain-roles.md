---
title: "Propriedades de funções de domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 9
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e85c47133509e3f7bf7c54b8cfa7f2121a26b04b
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-domain-roles"></a>Propriedades de funções de domínio
As propriedades na tabela a seguir são associadas a uma função de domínio. Para obter informações sobre as funções de domínio, consulte [compreensão de modelos, Classes e relacionamentos](../modeling/understanding-models-classes-and-relationships.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|Tipo de coleção|Se essa função possui multiplicidade 0.. * ou 1... \*, essa propriedade personaliza o tipo genérico que é usado para armazenar a coleção de links.|`(none)`- <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>é usado</xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>|  
|Atributos personalizados|Atributos que você especificar aqui serão adicionados como atributos para a classe do código gerado.|<>\>|  
|Propriedade é navegável|Se `True`, e se a multiplicidade da relação é 0..1 ou 1..1, a propriedade de função pode ser visitada pelo usuário na **propriedades** janela. A propriedade exibe o nome do elemento na outra extremidade do link de relação.|`True`|  
|É o gerador de propriedade|Se `True`, uma propriedade de função é gerada para essa função, que você pode usar para percorrer a relação no código do programa. Se você definir false, você pode percorrer a relação de forma menos eficiente usando métodos estáticos da relação de domínio.|`True`|  
|Modificador de acesso Getter de propriedade|O modificador de acesso para o getter da propriedade gerado (`public`, `internal`, `private`, `protected`, ou `protected internal`).|`public`|  
|Modificador de acesso Setter de propriedade|O modificador de acesso para o setter da propriedade gerado (`public`, `internal`, `private`, `protected`, ou `protected internal`).|`public`|  
|Multiplicidade|O número de elementos de modelo que pode desempenhar a função oposta (`0..1`, `1..1`, `0..*`, ou `1..*`). Se a multiplicidade for `0..*` ou `1..*`, em seguida, a propriedade gerada representa uma coleção; caso contrário, a propriedade gerada representa um elemento de modelo único.|Depende do tipo de relacionamento e se essa é a função de origem ou destino na relação.|  
|Nome|O nome da função de domínio. Essa propriedade não pode conter espaços em branco.|O nome da classe de domínio do player de função para esta função.|  
|Propaga cópia|`DoNotPropagateCopy`-O player de função copiado não terá nenhuma cópia deste link.<br /><br /> `PropagateCopyToLinkOnly`-O copiados aponta para existente oposto.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-O link copiado aponta para uma cópia do oposto.|`PropagateCopyToLinkAndOppositeRolePlayer`para as funções de origem dos objetos incorporados.<br /><br /> `DoNotPropagateCopy`para outras funções.<br /><br /> Para obter mais informações, consulte [personalizar comportamento de cópia](../modeling/customizing-copy-behavior.md)|  
|Propaga a exclusão|`True`Para excluir o elemento que desempenha essa função quando o link associado será excluído.|`True`para o destino de uma função de inserção.<br /><br /> `False`para outras funções.<br /><br /> Para obter mais informações, consulte [personalizar comportamento de exclusão](../modeling/customizing-deletion-behavior.md).|  
|Nome da Propriedade|O nome da propriedade gerado no código do player de função. Esse nome não pode conter espaços em branco.|O nome da função oposta se essa função tem um zero-para-um ou uma-para-um multiplicidade; Caso contrário, o nome pluralized da função oposta.|  
|Player de função|A classe de domínio do elemento que pode executar essa função na relação. Esta propriedade é somente para leitura.|A classe de domínio do player de função para esta função.|  
|Observações|Notas informais que estão associadas com a função de domínio.|<>\>|  
|Categoria|A categoria sob a qual a propriedade gerada aparece no **propriedades** janela no designer gerado. Se essa propriedade estiver vazia, a propriedade gerada aparece sob o **Misc** categoria|<>\>|  
|Descrição|A descrição que é usada para documentar código e é usada na interface do usuário do designer gerado.<br /><br /> A descrição aparece na dica de ferramenta Intellisense para a propriedade gerada na classe de player de função.|`Description for`*o nome completo da função*|  
|Nome de Exibição|O nome que é exibido no designer gerado para a função de domínio.|O valor ajustado da propriedade Name.|  
|Palavra-chave de ajuda|A palavra-chave opcional que é usada para indexar a Ajuda F1 para a função de domínio.|\<Nenhum >|  
|Nome de exibição da propriedade|O nome que é exibido no designer gerado para a propriedade da função gerada.|O valor ajustado da propriedade nome da propriedade.|  
  
> [!NOTE]
>  O valor padrão de um nome de exibição baseia-se no valor da propriedade associada inserindo espaços antes de cada caractere maiusculo, que é precedida por um caractere em minúscula e que não é seguido por outro caractere maiusculo.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades de relacionamentos de domínios](../modeling/properties-of-domain-relationships.md)
