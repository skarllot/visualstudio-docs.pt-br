---
title: "Explica&#231;&#227;o passo a passo: Criando uma bola de bilhar real&#237;stica em 3D | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
caps.latest.revision: 9
caps.handback.revision: 9
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Explica&#231;&#227;o passo a passo: Criando uma bola de bilhar real&#237;stica em 3D
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa explicação passo a passo demonstra como criar uma bola de bilhar realística em 3d utilizando o Shader Designer e o Image Editor em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  A aparência 3\-D de bola de bilhar é obtida combinando várias técnicas do sombreador com os recursos de textura apropriados.  
  
 Este documento demonstra estas atividades:  
  
-   Criando a aparência básica de uma bola de bilhar usando a forma e textura.  
  
-   Adicionando a profundidade usando o modelo de iluminação Lamberto.  
  
-   Aprimorar a aparência básica usando realces especulares.  
  
-   Criando uma noção de espaço refletindo o ambiente.  
  
## Pré-requisitos  
 Você precisa dos seguintes componentes e habilidades de concluir esta explicação passo a passo:  
  
-   Uma ferramenta para montar texturas em um mapa do cubo, como a Ferramenta de Textura do DirectX incluída no DirectX SDK de junho de 2010.  
  
-   Familiaridade com o Editor de Imagem no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Familiaridade com o Shader Designer no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Criando a aparência básica com a forma e textura  
 Na computação gráfica, os elementos mais básicos da aparência são a forma e a cor.  Em uma simulação em computador, é comum usar um modelo 3\-D para representar a forma de um objeto do mundo real.  O detalhe de cores é aplicado na superfície do modelo usando um mapa de textura.  
  
 Normalmente, você pode precisar pedir a um artista para criar um modelo 3\-D que você pode usar, mas como uma bola de bilhar é uma forma comum \(uma esfera\), o designer do Shader já possui um modelo apropriado incorporado.  
  
 A esfera é a maneira padrão de exibição no Shader Designer; se você estiver atualmente usando uma forma diferente para visualizar seu sombreador, mude de volta para esfera.  
  
#### Para visualizar o sombreador usando uma esfera  
  
-   Na barra de ferramentas Designer de Sombreador, escolha **Visualizar com esfera**.  
  
 Na próxima etapa, você criará um programa de sombreamento que aplica uma textura ao modelo, mas primeiro você tem que criar uma textura que você pode usar.  Essa explicação passo a passo demonstra como criar textura usando o Image Editor, que é uma parte de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mas você pode usar qualquer editor de imagem que pode salvar a textura em um formato adequado.  
  
 Certifique\-se de que a janela **Propriedades** e **Caixa de Ferramentas** são exibidos.  
  
#### Para criar uma textura de bola de bilhar usando o Editor de Imagem  
  
1.  Crie uma textura para trabalhar.  Para obter informações sobre como adicionar textura ao seu projeto, consulte a seção Introdução em [Editor de Imagem](../designers/image-editor.md).  
  
2.  Defina o tamanho da imagem de forma que sua largura seja duas vezes sua altura; isso é necessário por causa da maneira que uma textura é mapeada na superfície esférica da bola de bilhar.  Para redimensionar a imagem, na janela **Propriedades** , especifique os novos valores para as propriedades **Largura** e **Altura** .  Por exemplo, defina a largura para 512 e a altura para 256.  
  
3.  Desenhe uma textura para a bola de bilhar, tendo em mente como uma textura é mapeada em uma esfera.  
  
     A textura deve se parecer com isso:  
  
     ![A textura da bola de bilhar](../designers/media/gfx_shader_demo_billiard_art_ball_texture.png "gfx\_shader\_demo\_billiard\_art\_ball\_texture")  
  
4.  Um alternativa recomendada é diminuir os requisitos de armazenamento dessa textura.  Você pode fazer isto reduzindo a largura de textura para corresponder a sua altura.  Isso compacta a textura ao longo de sua largura, mas devido à maneira que a textura é mapeada para esfera, ela será expandida quando a bola de bilhar for renderizada.  Após redimensionar, a textura deve ser semelhante a isso:  
  
     ![A textura de bilhar compactada em um quadrado](../designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png "gfx\_shader\_demo\_billiard\_art\_ball\_texture\_square")  
  
 Agora você pode criar um sombreador que aplique a textura ao modelo.  
  
#### Para criar um sombreador básico de textura  
  
1.  Crie um shader de DGSL para trabalhar.  Para obter informações sobre como adicionar um sombreador DGSL ao seu projeto, consulte a seção Introdução em [Designer de sombreador](../designers/shader-designer.md).  
  
     Por padrão, um gráfico do sombreador tem esta aparência:  
  
     ![O gráfico de sombreador padrão](../designers/media/gfx_shader_demo_billiard_step_0.png "gfx\_shader\_demo\_billiard\_step\_0")  
  
2.  Modifique o sombreador padrão para que ele aplique o valor de um exemplo de textura ao pixel atual.  O elemento gráfico do sombreador deve ser assim:  
  
     ![Um gráfico de sombreador que se aplica a textura a um objeto](../designers/media/gfx_shader_demo_billiard_step_1.png "gfx\_shader\_demo\_billiard\_step\_1")  
  
3.  Aplicar a textura que você criou no procedimento anterior configurando as propriedades de textura.  Defina o valor da propriedade de **Textura** do nó de **Exemplo de Cubemap** como **Textura2** e, depois, especifique o arquivo de textura por meio da propriedade **Nome do arquivo** do grupo de propriedades de **Texture2**.  
  
 Para obter mais informações sobre como aplicar uma textura em seu sombreador, consulte [Como: criar um sombreador de textura básica](../designers/how-to-create-a-basic-texture-shader.md).  
  
 Sua bola de bilhar agora deve ser semelhante a isto:  
  
 ![Um Close&#45;up da bola de bilhar texturizado](../designers/media/gfx_shader_demo_.png "gfx\_shader\_demo\_")  
  
## Criando a profundidade com o modelo de iluminação Lamberto  
 Até agora, você criou uma bola de bilhar facilmente reconhecível.  No entanto, ele aparece plano e desinteressante \- mais como uma imagem dos desenhos animados de uma bola de bilhar do que uma réplica convincente.  A aparência plana resulta do sombreador simplista, que se comporta como se cada pixel na superfície da bola de bilhar recebesse a mesma quantidade de luz.  
  
 No mundo real, a luz aparece mais brilhante em superfícies que enfrentam diretamente uma fonte de luz e aparece menos brilhante em superfícies que estão em um ângulo oblíquo em relação à fonte de luz.  Isso ocorre porque a energia nos raios de luz é distribuída pela menor área de superfície quando a superfície encara diretamente a fonte de luz.  Como a superfície sai do foco, a mesma quantidade de energia é distribuída por uma superfície de área cada vez maior.  Uma superfície que esteja longe de uma fonte de luz não recebe nenhuma energia, resultando em uma aparência completamente escura.  Essa variação no brilho através da superfície de um objeto é uma importante indicação visual que ajuda a indicar a forma de um objeto; sem ele, o objeto parece plano.  
  
 Na computação gráfica, aproximações simplificadas de *modelos de iluminação* de complexos, interações de iluminação do mundo real \- são usadas para replicar a aparência de iluminação do mundo real.  O modelo de iluminação Lambert varia a quantidade de luz refletida de forma difusa na superfície de um objeto conforme descrito no parágrafo anterior.  Você pode adicionar o modelo de iluminação de Lambert ao seu sombreador para dar à bola de bilhar uma aparência 3D mais convincente.  
  
#### Para adicionar iluminação Lambert ao seu sombreador  
  
-   Modifique o sombreador para modular o valor de exemplo de textura pelo valor de iluminação Lambert.  O gráfico do seu sombreador deve ser assim:  
  
     ![O gráfico de sombreador com iluminação Lambert adicionado](../designers/media/gfx_shader_demo_billiard_step_2.png "gfx\_shader\_demo\_billiard\_step\_2")  
  
-   Como opção, você pode ajustar o comportamento da iluminação configurando a propriedade **MaterialDiffuse** do gráfico do sombreador.  Para acessar propriedades do gráfico shader, escolha uma área vazia na superfície de design e então localize a propriedade que você deseja acessar na janela **Propriedades**.  
  
 Para obter mais informações sobre como aplicar iluminação Lamberto em seu sombreador, consulte [Como: criar um sombreador Lambert básico](../designers/how-to-create-a-basic-lambert-shader.md).  
  
 Com iluminação de Lambert aplicada, sua bola de bilhar deve ficar semelhante a isto:  
  
 ![Um Close&#45;up da bola de bilhar texturizados e aceso](../designers/media/gfx_shader_demo_billiard_ball_2.png "gfx\_shader\_demo\_billiard\_ball\_2")  
  
## Aprimorar a aparência básica com realces especulares  
 O modelo de iluminação Lambert fornece a sensação de forma e de dimensão que estava faltando no sombreador só de textura.  No entanto, a bola de bilhar ainda tem uma aparência um pouco fosca.  
  
 Uma bola de bilhar real geralmente possui um acabamento lustroso que reflete uma parte da luz que bate nela.  Parte dessa luz refletida resulta em realces especulares que simulam as propriedades reflexivas de uma superfície.  Dependendo das propriedades da finalização, os destaques podem ser localizados ou amplos, intensos ou sutis.  Essas reflexos especulares são modelados usando a relação entre uma fonte de luz, a orientação da superfície e a posição da câmera — ou seja, o realce é mais intenso quando a orientação da superfície reflete a fonte de luz diretamente na câmera, e é menos intenso quando o reflexo é menos direto.  
  
 O modelo de iluminação Phong amplia o modelo de iluminação Lambert para incluir realces especulares, conforme descrito no parágrafo anterior.  Você pode adicionar o modelo de iluminação Phong ao seu sombreador para dar à bola de bilhar um botão simulado que resulta em uma aparência mais interessante.  
  
#### Para adicionar realces especulares ao seu sombreador  
  
1.  Modifique o sombreador para incluir a contribuição especular usando combinação aditiva.  O gráfico do seu sombreador deve ser assim:  
  
     ![O gráfico de sombreador com iluminação especular adicionado](../designers/media/gfx_shader_demo_billiard_step_3.png "gfx\_shader\_demo\_billiard\_step\_3")  
  
2.  Como alternativa, você pode ajustar o comportamento do realce especular configurando as propriedades especulares \(**MaterialSpecular** e **MaterialSpecularPower**\) do gráfico do sombreador.  Para acessar propriedades do gráfico shader, escolha uma área vazia na superfície de design e, na janela **Propriedades**, localize a propriedade que você deseja acessar.  
  
 Para obter mais informações sobre como aplicar realces especulares em seu sombreador, consulte [Como: criar um sombreador Phong básico](../designers/how-to-create-a-basic-phong-shader.md).  
  
 Com o realce especular aplicado, sua bola de bilhar deve ficar semelhante a isto:  
  
 ![Adicionado um Close&#45;up de bola de bilhar com especulares](../designers/media/gfx_shader_demo_billiard_ball_3.png "gfx\_shader\_demo\_billiard\_ball\_3")  
  
## Criando uma noção de espaço refletindo o ambiente  
 Com realce especular aplicado, sua bola de bilhar parece consideravelmente convincente.  Tem a forma correta, o trabalho de pintura correta e o acabamento correto.  No entanto, ainda há mais uma técnica que fará sua bola de bilhar se parecer mais com parte do seu ambiente.  
  
 Se você revise uma bola de bilhar real de perto, você pode ver que sua superfície brilhante não exibe apenas reflexos especulares, mas também reflete uma fraca imagem do mundo em torno dele.  Você pode simular esta reflexão usando uma imagem de ambiente como uma textura e combinando com a própria textura de modelo para determinar a cor final de cada pixel.  Dependendo do tipo de finalização que você deseja, é possível combinar mais ou menos da textura de reflexão juntamente com o restante do sombreador.  Por exemplo, um sombreador que simula uma superfície altamente reflexiva como um espelho pode usar somente a textura de reflexo, mas um sombreador que simula um reflexo mais sutil como a encontrada em uma bola de bilhar pode combinar apenas uma pequena parte do valor da textura de reflexão juntamente com o restante do cálculo do sombreador.  
  
 É claro que você não pode aplicar a imagem refletida ao modelo da mesma maneira que aplica o mapa de textura.  Se você fez, o reflexo do mundo moverá com a bola de bilhar como se a reflexão estivesse colada a ele.  Como um reflexo pode vir de qualquer direção, você precisa de uma maneira de fornecer um valor de mapa de reflexão para qualquer ângulo e uma forma de manter o mapa de reflexão orientado de acordo com o mundo.  Para satisfazer esses requisitos você pode usar um tipo especial de textura mapa–chamada *um cubo mapa\-*––que fornece seis texturas organizadas para formar os lados de um cubo.  De dentro deste cubo, você pode apontar em qualquer direção para localizar um valor de textura.  Se as texturas de cada lado do cubo contêm imagens do ambiente, você pode simular qualquer reflexão pela amostragem do local correto sobre a superfície do cubo.  Mantendo o cubo alinhado com o mundo, você terá um reflexo exato do ambiente.  Para determinar onde o cubo deve ser provado, você calcula apenas a reflexão do vetor da câmera fora da superfície do objeto, e em seguida usá\-o como a textura 3d coordena.  O uso de mapas do cubo dessa maneira é uma técnica comum conhecida como *mapeamento de ambiente*.  
  
 O mapeamento de ambiente fornece uma aproximação eficiente de reflexos reais, como descrito nos parágrafos anteriores.  Você pode misturar reflexos mapeadas do ambiente em seu sombreador para dar à bola de bilhar um botão simulado que faz a bola de bilhar parecer mais aterrada na cena.  
  
 A primeira etapa é criar uma textura do mapa do cubo.  Em muitos tipos de aplicativos, o conteúdo do mapa em cubo não tem que ser perfeito para ser eficaz, especialmente quando a reflexão é sutil ou não ocupa um espaço proeminente na tela.  Por exemplo, vários jogos usam mapas de cubo pré\-computados para o mapeamento de ambiente e apenas usam o mais próximo de cada objeto refletivo, embora isso significa que o reflexo não está correto.  Mesmo uma boa aproximação é geralmente boa o suficiente para um efeito convincente.  
  
#### Para criar texturas para um mapa de ambiente usando o editor de imagem  
  
1.  Crie uma textura para trabalhar.  Para obter informações sobre como adicionar textura ao seu projeto, consulte a seção Introdução em [Editor de Imagem](../designers/image-editor.md).  
  
2.  Defina o tamanho da imagem de modo que sua largura seja igual a sua altura e é uma potência de dois em tamanho; isso é necessário por causa da maneira como um mapa do cubo é indexado.  Para redimensionar a imagem, na janela **Propriedades** , especifique os novos valores para as propriedades **Largura** e **Altura** .  Por exemplo, defina o valor das propriedades de **Largura** e de **Altura** para 256.  
  
3.  Use uma cor sólida para preencher a textura.  Essa textura será a parte inferior do mapa do cubo, que corresponde à superfície da mesa de bilhar.  Manter a cor que você usou em mente para a próxima textura.  
  
4.  Crie uma segunda textura que é do mesmo tamanho da primeira.  Esta textura será repetida nos quatro lados do mapa do cubo, que corresponde à superfície e aos lados de uma mesa de bilhar, e à área em torno da mesa de bilhar.  Certificar\-se de desenhar a superfície da tabela de bilhar nesta textura usando a mesma cor da textura inferior.  A textura deve se parecer com isso:  
  
     ![A textura para os lados do cubemap](../designers/media/gfx_shader_demo_billiard_art_env_texture_side.png "gfx\_shader\_demo\_billiard\_art\_env\_texture\_side")  
  
     Lembre\-se de que um mapa de reflexão não tem que ser fotorrealista para ser mais eficiente; por exemplo, o mapa do cubo usado para criar as imagens este artigo contém apenas quatro bolsos em vez de seis.  
  
5.  Crie uma terceira textura que é do mesmo tamanho das outras.  Essa textura será a parte superior do mapa do cubo, que corresponde ao teto acima da mesa de bilhar.  Para tornar essa parte de reflexão mais interessante, você pode desenhar uma luz de sobrecarga para reforçar o realce especular que você adicionou ao sombreador no procedimento anterior.  A textura deve se parecer com isso:  
  
     ![A textura na parte superior do cubemap](../designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png "gfx\_shader\_demo\_billiard\_art\_env\_texture\_top2")  
  
 Agora que criou texturas individuais para as laterais do mapa de cubo, você pode usar uma ferramenta para montá\-las em um mapa de cubo que possa ser armazenado em uma única textura .dds.  Você pode usar qualquer programa que você deseja criar o mapa do cubo como pode salvar o mapa do cubo no formato de textura de .dds.  Essa explicação passo a passo demonstra como criar textura usando a ferramenta de textura de DirectX que é uma parte do DirectX SDK de junho de 2010 .  
  
#### Para montar um mapa do cubo usando a ferramenta de textura do DirectX  
  
1.  Na Ferramenta de Textura DirectX, no menu principal, escolher **Arquivo**, **Nova Textura**.  A caixa de diálogo **Nova textura** aparece.  
  
2.  No grupo **Tipo de Textura**, escolher **Textura do Cubemap**.  
  
3.  No grupo de **Dimensões**, digitar o valor correto para a **Largura** e a **Altura**, e, em seguida, escolher **OK**.  Um novo documento de textura aparece.  Por padrão, a textura mostrada primeiro no documento de textura corresponde à face do cubo **Positivo X**.  
  
4.  Carregar a textura que você criou para o lado do cubo de textura na face do cubo.  No menu principal, escolha **Arquivo** e **Abrir nesta Face de Mapa de Cubo**. Em seguida, selecione a textura criada para a lateral do cubo e clique em **Abrir**.  
  
5.  Repita a etapa 4 para as faces de cubo **X Negativo**, **Z Positivo** e **Z Negativo** .  Para fazer isso, você deve exibir a face que deseja carregar.  Para exibir uma face diferente do mapa do cubo, no menu principal, escolha **Exibição**, **Face do Mapa do Cubo**, e selecione a face que você deseja exibir.  
  
6.  Para a face do cubo **Y Positivo**, carregar a textura que você criou para a parte superior do cubo de textura.  
  
7.  Para a face do cubo **Y Negativo**, carregar a textura que você criou para a parte inferior do cubo de textura.  
  
8.  Salve a textura.  
  
 Você pode imaginar o layout do mapa de cubos como este:  
  
 ![O layout do mapa de cubo do ambiente](../designers/media/gfx_shader_demo_billiard_art_env_texture_top.png "gfx\_shader\_demo\_billiard\_art\_env\_texture\_top")  
  
 A imagem na parte superior é a face do cubo Y positivo \(\+Y\); no meio, da esquerda para a direita, são as faces do cubo – X, \+Z, \+X, e –Z; na parte inferior, é a face do cubo –Y.  
  
 Agora você pode modificar o sombreador para mesclar o exemplo de mapa de cubo ao restante do sombreador.  
  
#### Para adicionar um mapeamento de ambiente ao seu sombreador  
  
1.  Modifique o sombreador para incluir a contribuição de mapeamento de ambiente usando combinação aditiva.  O gráfico do seu sombreador deve ser assim:  
  
     ![Um Close&#45;up de ambos os nós Refletivo tipo de sombreador](../designers/media/gfx_shader_demo_billiard_step_4b.png "gfx\_shader\_demo\_billiard\_step\_4b")  
  
     Observe que você pode usar um nó **Adicionar Multiplicação** para simplificar o gráfico do sombreador.  
  
     Aqui está uma visão mais detalhada dos nós do sombreador que implementam o mapeamento de ambiente:  
  
     ![O gráfico de sombreador com mapeamento de ambiente adicionado](../designers/media/gfx_shader_demo_billiard_step_4a.png "gfx\_shader\_demo\_billiard\_step\_4a")  
  
2.  Aplicar a textura que você criou no procedimento anterior configurando as propriedades de textura do mapa do cubo.  Defina o valor da propriedade de **Textura** do nó de **Exemplo de Cubemap** como **Textura2** e, depois, especifique o arquivo de textura por meio da propriedade **Nome do arquivo** do grupo de propriedades de **Texture2**.  
  
3.  Como alternativa, você pode ajustar a reflexibilidade da bola de bilhar configurando a propriedade **Saída** do nó **Constante**.  Para acessar propriedades do nó, selecione\-o e, na janela **Propriedades** , localize a propriedade que você deseja acessar.  
  
 Com o mapeamento do ambiente aplicado, sua bola de bilhar deve ficar semelhante a isto:  
  
 ![Um Close&#45;up do ambiente mapeado bola de bilhar](../designers/media/gfx_shader_demo_billiard_ball_4.png "gfx\_shader\_demo\_billiard\_ball\_4")  
  
 Nesta imagem final, observe como os efeitos que você adicionou se reúnem para criar uma bola de bilhar muito convincente.  A forma, a textura e iluminação criam a aparência básica de um objeto 3D, e os realces especulares e reflexos fazem a bola de bilhar ficar mais interessante, e são como parte do seu ambiente.  
  
## Consulte também  
 [Como: exportar um sombreador](../designers/how-to-export-a-shader.md)   
 [Como: aplicar um sombreador a um modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Designer de sombreador](../designers/shader-designer.md)   
 [Editor de Imagem](../designers/image-editor.md)   
 [Nós do Designer de Sombreador](../designers/shader-designer-nodes.md)