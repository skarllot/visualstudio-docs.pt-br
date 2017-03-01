---
title: "Respondendo a alterações e propagando | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 24
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f33e0f71bc651761fd1d97269b711b214c46b9f1
ms.lasthandoff: 02/22/2017

---
# <a name="responding-to-and-propagating-changes"></a>Respondendo a alterações e propagando-as
Quando um elemento é criado, excluído ou atualizado, você pode escrever código que propaga a alteração para outras partes do modelo ou a recursos externos como arquivos, bancos de dados ou outros componentes.  
  
## <a name="in-this-section"></a>Nesta seção  
 Como diretriz, considere estas técnicas na seguinte ordem:  
  
|Técnica|Cenários|Para obter mais informações|  
|---------------|---------------|--------------------------|  
|Defina uma propriedade de domínio calculada.|Uma propriedade de domínio cujo valor é calculado a partir de outras propriedades no modelo. Por exemplo, um preço que é a soma dos preços dos elementos relacionados.|[Propriedades calculadas e de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md)|  
|Defina uma propriedade de domínio de armazenamento personalizado.|Uma propriedade de domínio armazenada em outras partes do modelo ou externamente. Por exemplo, você pode analisar uma cadeia de caracteres de expressão em uma árvore no modelo.|[Propriedades calculadas e de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md)|  
|Substitua os manipuladores de alteração como OnValueChanging e OnDeleting|Mantenha elementos diferentes em sincronia e valores externos em sincronia com o modelo.<br /><br /> Restringir os valores em intervalos definidos.<br /><br /> Chamado imediatamente antes e após o valor da propriedade e outras alterações. Você pode finalizar a alteração lançando uma exceção.|[Manipuladores de alterações nos valores da propriedade de domínio](../modeling/domain-property-value-change-handlers.md)|  
|Regras|Você pode definir regras que estão enfileiradas para execução antes do final de uma transação em que uma alteração tiver ocorrido. Elas não são executados em Desfazer ou refazer. Usá-las para manter uma parte do armazenamento em sincronia com o outro.|[Regras propagam alterações dentro do modelo](../modeling/rules-propagate-changes-within-the-model.md)|  
|Eventos de armazenamento|O armazenamento de modelagem fornece notificações de eventos, como adicionar ou excluir um elemento ou um link ou alterar o valor de uma propriedade. O evento também é executado em Desfazer e refazer. Use eventos de armazenamento para atualizar valores que não estão no repositório.|[Manipuladores de eventos propagam alterações fora do modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|Eventos .NET|Formas têm manipuladores de eventos que respondem a cliques do mouse e outros gestos. Você deve registrar esses eventos para cada objeto. O registro é geralmente feito na substituição de InitializeInstanceResources e deve ser feito para cada elemento.<br /><br /> Esses eventos ocorrem normalmente fora de uma transação.|[Como interceptar um clique em uma forma ou um decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|Regras de limites|Uma regra de associação é usada especificamente para restringir os limites de uma forma.|[BoundsRules restringem o local e o tamanho de uma forma](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|Regras de seleção|Regras de seleção restringem especificamente o que o usuário pode selecionar.|[Como acessar e restringir a seleção atual](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Indica estados dos elementos de modelo usando recursos de formas e conectores, como sombra, pontas de seta, cor e larguras de linha e estilo.|[Atualizando formas e conectores para refletir o modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**Comparando as regras e eventos de armazenamento**  
 Alterar notifiers, regras e eventos são executados quando ocorrerem alterações em um modelo.  
  
 Geralmente, as regras são aplicadas na transação final na qual a alteração ocorreu e eventos são aplicados depois que as alterações em uma transação serão confirmadas.  
  
 Use eventos de armazenamento para sincronizar o modelo com objetos fora da loja e regras para manter a consistência na loja.  
  
-   **Criação de regras personalizadas** criar uma regra personalizada como uma classe derivada de uma regra abstrata. Você também deve notificar o framework sobre a regra personalizada. Para obter mais informações, consulte [propagar alterações dentro do modelo de regras](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **Assinando eventos** antes de assinar um evento, crie um manipulador de eventos e representante. Em seguida, use o <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>propriedade para assinar o evento.</xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> Para obter mais informações, consulte [manipuladores de propagar alterações fora do modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **Desfazendo alterações** ao desfazer uma transação, os eventos são gerados, mas as regras não serão aplicadas. Se uma regra altera um valor e desfaça a alteração, o valor será redefinido para o valor original durante a ação de desfazer. Quando um evento é gerado, você deve alterar manualmente o valor para seu valor original. Para saber mais sobre transactons e desfazer, consulte [como: usar transações para atualizar o modelo](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   **Passando argumentos de evento para eventos e regras** ambos os eventos e as regras são passadas um `EventArgs` parâmetro que tem informações sobre como o modelo foi alterado.  
  
## <a name="see-also"></a>Consulte também  
 [Como: interceptar um clique em uma forma ou um decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
