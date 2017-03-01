---
title: "Várias DSLs em uma única solução | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 3
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b55d1d5ec8e84c8d16681ffd0ac738291e1bc39d
ms.lasthandoff: 02/22/2017

---
# <a name="multiple-dsls-in-one-solution"></a>Várias DSLs em uma mesma solução
É possível empacotar diversas DSLs como parte de uma única solução para serem instaladas juntas.  
  
 É possível usar diversas técnicas para integrar múltiplas DSLs. Para obter mais informações, consulte [integrando modelos usando o Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md) e [personalizar comportamento de cópia](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Compilar mais de uma DSL na mesma solução  
  
1.  Crie duas ou mais soluções DSL e um projeto VSIX e adicione todos os projetos a uma única solução.  
  
    -   Para criar um novo projeto do VSIX: no **novo projeto** caixa de diálogo, selecione **Visual C#**, **extensibilidade**, **projeto VSIX**.  
  
    -   Crie duas ou mais soluções DSL no diretório da solução VSIX.  
  
         Abra uma nova instância do Visual Studio para cada DSL. Crie a nova DSL e especifique a mesma pasta da solução que a solução VSIX.  
  
         Certifique-se de criar cada DSL com uma extensão de nome de arquivo diferente.  
  
    -   Alterar os nomes do **Dsl** e **DslPackage** projetos para que fiquem todos diferentes. For example: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   Em cada **DslPackage\*\source.extension.tt**, atualize essa linha para o nome do projeto Dsl correto:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   Na solução VSIX, adicione o Dsl * e DslPackage\* projetos.  
  
         É aconselhável colocar cada par em sua própria pasta da solução.  
  
2.  Combine os manifestos VSIX das DSLs:  
  
    1.  Abra *YourVsixProject***\source.extension.manifest**.  
  
    2.  Para cada DSL, escolha **adicionar conteúdo** e adicione:  
  
        -   `Dsl*`do projeto como um **componente MEF**  
  
        -   `DslPackage*`do projeto como um **componente MEF**  
  
        -   `DslPackage*`do projeto como um **pacote VS**  
  
3.  Compile a solução.  
  
 O VSIX resultante instalará as duas DSLs. Você pode testá-las usando F5 ou implantar *YourVsixProject***\bin\Debug\\\*. VSIX**.  
  
## <a name="see-also"></a>Consulte também  
 [Integrando modelos por meio do Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personalizando o comportamento de cópia](../modeling/customizing-copy-behavior.md)
