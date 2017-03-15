---
title: "Controlando a visibilidade de um ícone ou decorador | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 680ac8593c3e30866f4c03afb95d58c400b66b04
ms.lasthandoff: 02/22/2017

---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlando a visibilidade de um ícone ou decorador
A *decorador* é um ícone ou linha de texto que aparece em uma forma em uma linguagem específica do domínio (DSL). Você pode fazer o decorador aparecem e desaparecem dependendo do estado das propriedades no modelo. Por exemplo, em uma forma que representa uma pessoa, você pode ter diferentes ícones exibidos de acordo com o sexo da pessoa, número de filhos, e assim por diante.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Controlando a visibilidade de um ícone ou decorador  
 O procedimento a seguir pressupõe que você já definiu uma forma e seu mapeamento para uma classe de domínio. Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md).  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Para controlar a visibilidade de um decorador de texto ou ícone  
  
1.  No diagrama de definição de DSL, adicione a classe shape ícones ou decoradores de texto que você deseja exibir.  
  
    1.  Clique em classe shape, aponte para **adicionar**e, em seguida, clique no tipo necessário de decorador.  
  
    2.  Defina o decorador **posição** propriedade. Mais de um decorador pode ter a mesma posição. Por exemplo, você poderia ter ícones para masculino e feminino compartilhando a mesma posição.  
  
    3.  Definir o **ícone padrão** propriedade de um decorador de ícone.  
  
2.  Selecione o mapa de elemento do diagrama, que é a linha cinza entre a classe shape e a classe de domínio no diagrama de definição de DSL.  
  
3.  Na janela de detalhes de DSL, no **mapas do decorador** , selecione um decorador. Por exemplo, o MaleDecorator.  
  
4.  Verifique o **filtro de visibilidade** caixa.  
  
5.  Se a propriedade de domínio que deve controlar a visibilidade é da classe de domínio imediato, deixe **caminho para a propriedade Filter** em branco.  
  
     Caso contrário, clique no menu suspenso e navegue até a relação ou onde se encontra a propriedade de classe.  
  
    -   Para evitar um relatório de erros, você não deve navegar por meio de uma relação marcada com "*" na ferramenta de navegação.  
  
6.  Definir o **propriedade Filter** para uma propriedade de domínio. Por exemplo, sexo.  
  
7.  No **visibilidade entradas** lista, adicione os valores dessa propriedade de domínio para o qual o decorador deve estar visível. Por exemplo, masculino.  
  
8.  Repita as etapas para cada ícone.  
  
9. **Transformar todos os modelos**, compilar e executar e abrir um diagrama de teste.  
  
10. Quando você altera o valor da propriedade de controle, os decoradores deverá aparecer e desaparecer.  
  
 Com frequência, convém visibilidade controlado por uma fórmula mais complexa do que um conjunto simple de valores. Por exemplo, ter um ícone dependem do número de links de um tipo específico ou que dependem de se um número está em um determinado intervalo. Nesse caso, use o procedimento a seguir.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Para controlar a visibilidade de um decorador com base em uma fórmula  
  
1.  Adicione uma propriedade de domínio calculada para a classe de domínio. No **propriedades** janela, defina os seguintes valores:  
  
     **IsBrowsable =**`False`**-ocultará a propriedade do usuário    **  
  
     **Tipo =**`Calculated`**-isso significa que você irá fornecer código que calcula seus valores    **  
  
     **Nome** por exemplo **DecoratorControl**  
  
     **Tipo** = `Boolean`  
  
     Para obter mais informações, consulte [calculado e propriedades de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md).  
  
2.  Verifique a nova propriedade controlar a visibilidade do decorador.  
  
    1.  Selecione o mapa de elemento do diagrama, que é a linha cinza da classe de domínio à forma. No **detalhes de DSL** janela, abra o **DecoratorMap** guia.  
  
    2.  Verifique o **filtro de visibilidade** caixa.  
  
    3.  Em **propriedade Filter**, selecione a propriedade do controle **DecoratorControl**.  
  
    4.  Em **visibilidade entradas**, digite `True`.  
  
3.  Clique em **transformar todos os modelos** na barra de ferramentas Solution Explorer.  
  
4.  Clique em **Build Solution** sobre o **criar** menu.  
  
5.  Clique duas vezes no relatório de erro que apareceu: "*YourClass* não contém uma definição para GetDecoratorControlValue...".  
  
     Abre o editor de texto em Dsl\GeneratedCode\DomainClasses.cs. Acima do erro realçado é um comentário que solicita que você adicione um método.  
  
6.  Observe o namespace de classe e método que estão faltando.  Por exemplo, Company.FamilyTree.Person.GetDecoratorControlValue().  
  
7.  Em um arquivo de código separado, escreva uma definição de classe parcial que contém o método ausente. Por exemplo:  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     Para obter mais informações sobre como personalizar o modelo com o código do programa, consulte [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
8.  Recompilar e executar a solução.  
  
## <a name="see-also"></a>Consulte também  
 [Definindo formas e conectores](../modeling/defining-shapes-and-connectors.md)   
 [Definindo uma imagem de plano de fundo em um diagrama](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Navegando e atualizando um modelo no código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
