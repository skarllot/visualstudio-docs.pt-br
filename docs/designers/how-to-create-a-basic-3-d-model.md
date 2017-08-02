---
title: "Como criar um modelo 3D básico | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0d97966-2df8-449b-a8cf-5a19684dc773
caps.latest.revision: 18
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e060cc2d6d66d63dceeb2480b43dd9421106ce88

---
# <a name="how-to-create-a-basic-3-d-model"></a>Como criar um modelo 3D básico
Este documento demonstra como usar o Editor de Modelo para criar um modelo 3D básico.  
  
 Este documento demonstra essas atividades:  
  
-   Adicionar objetos a uma cena  
  
-   Selecionar faces e bordas  
  
-   Converter seleções  
  
-   Uso das ferramentas **Subdivide a face** e **Extrudar face**  
  
-   Uso do comando **Triangular**  
  
## <a name="creating-a-basic-3-d-model"></a>Criando um modelo 3D básico  
 Você pode usar o Editor de Modelo para criar e modificar modelos e cenas 3D para seu jogo ou aplicativo. As etapas a seguir mostram como usar o Editor de Modelo para criar um modelo 3D simplificado de uma casa. Um modelo simplificado pode ser usado como um substituto para ativos de arte final que ainda estão sendo criados, como uma malha para detecção de colisão ou como um modelo de nível baixo de detalhes a ser usado quando o objeto que ele representa está muito longe tirar proveito de uma renderização mais detalhada.  
  
 Ao terminar, o modelo deve ter esta aparência:  
  
 ![O modelo concluído da casa simplificada](~/docs/designers/media/gfx_model_demo_house_final.png "gfx_model_demo_house_final")  
  
 Antes de começar, verifique se a janela **Propriedades** e a **Caixa de Ferramentas** estão sendo exibidas.  
  
#### <a name="to-create-a-simplified-3-d-model-of-a-house"></a>Para criar um modelo 3D simplificado de uma casa  
  
1.  Crie um modelo 3D com o qual trabalhar. Para obter informações sobre como adicionar um modelo ao seu projeto, consulte a seção de Introdução em [Editor de Modelo](../designers/model-editor.md).  
  
2.  Adicione um cubo para a cena. Na janela **Caixa de Ferramentas**, em **Formas**, selecione **Cubo** e mova-o para a superfície de design.  
  
3.  Mude para seleção de face. Na barra de ferramentas do Editor de Modelo, escolha **Selecionar Face**.  
  
4.  Subdivida a parte superior do cubo. No modo de seleção de face, escolha o cubo uma vez para ativá-lo para a seleção e, em seguida, escolha a parte superior do cubo para selecionar a face superior. Na barra de ferramentas do Editor de Modelo, escolha **Subdivide a face**. Isso adiciona novos vértices na parte superior do cubo que o dividem em quatro partições de tamanhos iguais.  
  
     ![A parte superior do cubo foi subdividida](~/docs/designers/media/gfx_model_demo_house_subdiv.png "gfx_model_demo_house_subdiv")  
  
5.  Faça a extrusão de dois lados adjacentes do cubo, por exemplo, a frente e o lado direito do cubo. No modo de seleção de face, escolha uma vez o cubo para ativá-lo para a seleção e, em seguida, escolha um lado do cubo. Pressione e mantenha a tecla Control pressionada, escolha outro lado do cubo que seja adjacente ao lado que foi selecionado primeiro e, em seguida, na barra de ferramentas do Editor de Modelo, escolha **Extrudar face**.  
  
     ![Os lados do cubo foram extrudados](~/docs/designers/media/gfx_model_demo_house_extrude.png "gfx_model_demo_house_extrude")  
  
6.  Estenda uma das extrusões. Escolha uma as faces que você acabou de extrudar e, na barra de ferramentas do Editor de Modelo, escolha a ferramenta **Mover** e mova o manipulador de movimento na mesma direção da extrusão.  
  
     ![Um lado do cubo foi ainda mais extrudado.](~/docs/designers/media/gfx_model_demo_house_extend.png "gfx_model_demo_house_extend")  
  
7.  Triangular o modelo. Na barra de ferramentas do Editor de Modelo, escolha **Avançado**, **Ferramentas** e **Triangular**.  
  
8.  Crie o teto da casa. Mude para o modo de seleção de borda escolhendo **Selecionar Borda** na barra de ferramentas do Editor de Modelo e, em seguida, escolha o cubo para ativá-lo. Pressione e mantenha a tecla Control pressionada enquanto seleciona as bordas que são mostradas aqui:  
  
     ![As bordas que formarão o cume do telhado](~/docs/designers/media/gfx_model_demo_house_edges.png "gfx_model_demo_house_edges")  
  
     Com as bordas selecionadas, na barra de ferramentas do Editor de Modelo, escolha a ferramenta **Mover** e, em seguida, mova o manipulador de movimento para cima a fim de criar o telhado da casa.  
  
 O modelo de casa simplificada está concluído. Aqui está o modelo final novamente, com sombreamento simples aplicado:  
  
 ![O modelo concluído da casa simplificada](~/docs/designers/media/gfx_model_demo_house_final.png "gfx_model_demo_house_final")  
  
 Como uma próxima etapa, você pode aplicar um sombreador a esse modelo 3D. Para obter mais informações, consulte [Como aplicar um sombreador a um modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como modelar terreno 3D](../designers/how-to-model-3-d-terrain.md)   
 [Editor de Modelo](../designers/model-editor.md)   
 [Designer de Sombreador](../designers/shader-designer.md)


<!--HONumber=Feb17_HO4-->


