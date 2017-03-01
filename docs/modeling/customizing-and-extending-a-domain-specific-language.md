---
title: "Personalizando e estendendo uma linguagem específica do domínio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
ms.assetid: b155eb79-4e0a-4a99-a6f2-ca4f811fb5ca
caps.latest.revision: 48
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 00a120fc470393f8ab843636ca5d3400b004232b
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personalizando e estendendo uma linguagem específica do domínio
O Visual Studio de modelagem e SDK de visualização (VMSDK) fornece vários níveis na qual você pode definir as ferramentas de modelagem:  
  
1.  Defina uma linguagem específica do domínio (DSL) usando o diagrama de definição de DSL. Você pode criar rapidamente uma DSL com uma notação diagramática, uma forma XML legível e as ferramentas básicas necessárias para gerar código e outros artefatos.  
  
     Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md).  
  
2.  Ajuste a DSL usando recursos mais avançados da definição de DSL. Por exemplo, você pode fazer com que links adicionais aparecem quando o usuário cria um elemento. Essas técnicas são obtidas principalmente na definição de DSL e alguns requerem algumas linhas de código do programa.  
  
3.  Amplie suas ferramentas de modelagem usando o código do programa. O VMSDK foi projetado especificamente para facilitar a integração de suas extensões com o código gerado a partir da Definição de DSL.  Para obter mais informações, consulte [escrevendo código para personalizar uma linguagem específica do domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
> [!NOTE]
>  Quando você atualizou o arquivo de definição de DSL, não se esqueça de clicar **transformar todos os modelos** na barra de ferramentas do Gerenciador de soluções antes de recompilar sua solução.  
  
##  <a name="a-namecustomshapesa-in-this-section"></a><a name="customShapes"></a>Nesta seção  
  
|Para obter esse efeito|Consulte este tópico|  
|----------------------------|-------------------------|  
|Permitir que o usuário defina as propriedades de estilo e a cor de uma forma.|A classe shape ou conector de atalho, aponte para **adicionar exposto**e clique em um item.<br /><br /> Consulte [Personalizando a apresentação no diagrama](../modeling/customizing-presentation-on-the-diagram.md).|  
|No diagrama, compartilhar propriedades como inicial altura e largura, cor, dicas de ferramenta semelhante diferentes classes de elemento de modelo.|Use a herança entre formas ou classes do conector. Mapeamentos entre as formas derivadas e classes de domínio derivadas herdam os detalhes de mapeamento dos pais.<br /><br /> Ou então, mapear classes de domínio diferentes para a mesma classe de forma.|  
|Uma classe de elemento de modelo é exibida por contextos de formas diferentes.|Mapear mais de uma classe de forma para a mesma classe de domínio. Quando você compila a solução, execute o relatório de erros e fornecer o código solicitado para decidir qual forma será usada.|  
|Cor da forma ou outros recursos como fonte indicam o estado atual.|Consulte [atualizando formas e conectores para refletir o modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Crie uma regra que atualiza as propriedades expostas. Consulte [regras propagam alterações dentro do modelo](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> Ou, use OnAssociatedPropertyChanged() para atualizar recursos não exposto como fonte ou setas de link.|  
|Ícone de alterações de forma para indicar o estado.|Defina a visibilidade do decorador mapeamento na janela de detalhes de DSL. Localize vários decoradores de imagem na mesma posição. Consulte [atualizando formas e conectores para refletir o modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Ou, substituir `ImageField.GetDisplayImage()`. Consulte o exemplo <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>|  
|Definir uma imagem de plano de fundo em qualquer forma|Substitua InitializeInstanceResources() para adicionar um ImageField ancorado. Consulte [Personalizando a apresentação no diagrama](../modeling/customizing-presentation-on-the-diagram.md).|  
|Aninhar formas em qualquer profundidade|Configure uma recursiva incorporação de árvore. Defina BoundsRules para conter as formas. Consulte [Personalizando a apresentação no diagrama](../modeling/customizing-presentation-on-the-diagram.md).|  
|Anexe conectores em pontos fixos em limites de um elemento.|Defina elementos incorporados de terminal, representados por portas pequeno no diagrama. Use BoundsRules para corrigir as portas no lugar. Consulte o exemplo de diagrama de circuito em [SDK de visualização e modelagem](http://go.microsoft.com/fwlink/?LinkID=186128).|  
|Campo de texto exibe um valor derivado de outros valores.|Mapear o decorador de texto para uma propriedade de domínio calculado ou armazenamento personalizado. Para obter mais informações, consulte [calculado e propriedades de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md).|  
|Propagar alterações entre elementos de modelo ou entre formas|Consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md).|  
|Propagar alterações para recursos, como outros [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões fora da loja.|Consulte [manipuladores de eventos propagam alterações fora do modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).|  
|Janela Propriedades exibe as propriedades de um elemento relacionado.|Configure o encaminhamento de propriedade. Consulte [Personalizando a janela de propriedades](../modeling/customizing-the-properties-window.md).|  
|Categorias de propriedades|A janela Propriedades é dividida em seções chamadas categorias. Definir o **categoria** de seu domínio. Propriedades com o mesmo nome de categoria aparecerão na mesma seção. Você também pode definir o **categoria** de uma função de relação.|  
|Controlar o acesso do usuário para propriedades de domínio|Definir **é navegável** false para impedir que uma propriedade de domínio que aparecem na janela Propriedades em tempo de execução. Você ainda poderá mapeá-lo para decoradores de texto.<br /><br /> **É IU somente leitura** impede que os usuários de alterar uma propriedade de domínio.<br /><br /> Acesso a programas para a propriedade de domínio não é afetado.|  
|Altere o nome, o ícone e a visibilidade de nós no Gerenciador de modelos da DSL.|Consulte [Personalizando o Gerenciador de modelos](../modeling/customizing-the-model-explorer.md).|  
|Habilitar copiar, recortar e colar|Definir o **habilitar copiar e colar** propriedade o **Editor** nó no Gerenciador de DSL.|  
|Copiar suas metas e links de referência sempre que um elemento é copiado. Por exemplo, copie os comentários anexados a um item.|Definir o **propaga cópia** propriedade da função de origem (representada pela linha em um dos lados da relação de domínio no diagrama de definição de DSL).<br /><br /> Escreva código para substituir ProcessOnCopy para atingir efeitos mais complexos.<br /><br /> Consulte [personalizar o comportamento de cópia](../modeling/customizing-copy-behavior.md).|  
|Excluir, reassociar ou vincular elementos relacionados quando um elemento é excluído.|Definir o **propaga exclusão** valor de uma função de relação. Para efeitos mais complexos, substituir `ShouldVisitRelationship` e `ShouldVisitRolePlayer` métodos o `MyDslDeleteClosure` classe, definida em **DomainModel.cs**<br /><br /> Consulte [personalizar o comportamento de exclusão](../modeling/customizing-deletion-behavior.md)|  
|Preserve o layout de forma e a aparência em copiar e arrastar e soltar.|Adicionar as formas e conectores para o copiados `ElementGroupPrototype`. É o método mais conveniente para substituir`ElementOperations.CreateElementGroupPrototype()`<br /><br /> Consulte [personalizar o comportamento de cópia](../modeling/customizing-copy-behavior.md).|  
|Cole formas em um local escolhido, como a posição atual do cursor.|Substituir `ClipboardCommandSet.ProcessOnCopy()` para usar a versão específica do local de `ElementOperations.Merge().` consulte [personalizar comportamento de cópia](../modeling/customizing-copy-behavior.md).|  
|Criar links adicionais ao colar|Substituir ClipboardCommandSet.ProcessOnPasteCommand()|  
|Habilitar arrastar e soltar este diagrama para outras DSLs e Windows elementos|Consulte [como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md)|  
|Permitir que uma forma ou a ferramenta para ser arrastado para uma forma filha, como uma porta, como se ele foi arrastado para o pai.|Defina uma diretiva Element Merge na classe de objeto de destino para encaminhar o objeto solto ao pai. Consulte [Personalizando a criação de elemento e o movimento](../modeling/customizing-element-creation-and-movement.md).|  
|Permitir uma forma ou a ferramenta para ser arrastado para uma forma e têm links adicionais ou objetos criados. Por exemplo, para permitir um comentário a ser solto em um item para o qual é a ser vinculado.|Defina uma diretiva Element Merge na classe de domínio de destino e defina os vínculos a serem gerados. Em casos complexos, você pode adicionar código personalizado. Consulte [Personalizando a criação de elemento e o movimento](../modeling/customizing-element-creation-and-movement.md).|  
|Crie um grupo de elementos com uma ferramenta. Por exemplo, um componente com um conjunto fixo de portas.|Substitua o método de inicialização de ferramentas em ToolboxHelper.cs. Crie um protótipo de grupo de elemento (EGP) que contém os elementos e seus links de relacionamento. Consulte [personalizando ferramentas e a caixa de ferramentas](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Inclua as formas principais e a porta em que o EGP ou definir BoundsRules para posicionar as formas de porta quando o EGP é instanciado. Consulte [BoundsRules restringem o tamanho e local na forma](../modeling/boundsrules-constrain-shape-location-and-size.md).|  
|Use uma ferramenta de conexão para instanciar a vários tipos de relação.|Adicione Link conectar diretivas (LCD) para o construtor de Conexão que é invocado pela ferramenta. Os LCDs determinam o tipo de relação entre os tipos de dois elementos. Para fazer isso depende dos estados dos elementos, você pode adicionar código personalizado. Consulte [personalizando ferramentas e a caixa de ferramentas](../modeling/customizing-tools-and-the-toolbox.md).|  
|Ferramentas de adesivas – o usuário pode clicar duas vezes qualquer ferramenta para criar muitas formas ou conectores em sucessão.|No Gerenciador de DSL, selecione o `Editor` nó. Na janela Propriedades, defina **usa adesivo Toolbox Items**.|  
|Definir comandos de menu|Consulte [como: modificar um comando de Menu padrão](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|  
|Restringir o modelo com regras de validação|Consulte [validação em uma linguagem específica do domínio](../modeling/validation-in-a-domain-specific-language.md)|  
|Gere código, arquivos de configuração ou documentos de uma DSL.|[Gerando código com base em uma linguagem específica de domínio](../modeling/generating-code-from-a-domain-specific-language.md)|  
|Personalizar como os modelos são salvos ao arquivo.|Consulte [Personalizando a serialização de XML e armazenamento de arquivos](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Salve modelos de bancos de dados ou outras mídias.|Substituir *YourLanguage*DocData<br /><br /> Consulte [Personalizando a serialização de XML e armazenamento de arquivos](../modeling/customizing-file-storage-and-xml-serialization.md)|  
|Integre diversas DSLs para que eles funcionem como parte de um aplicativo.|Consulte [integrando modelos usando o Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|  
|Permitir DSL seja estendida por terceiros e a extensão de controle.|[Estender a DSL usando MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Compartilhando classes entre DSLs por meio de uma biblioteca de DSLs](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definindo uma política de bloqueio para criar segmentos somente leitura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|  
|||  
  
## <a name="see-also"></a>Consulte também  
 [Como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Escrevendo código para personalizar uma linguagem específica do domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [SDK de Modelagem para Visual Studio – linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


