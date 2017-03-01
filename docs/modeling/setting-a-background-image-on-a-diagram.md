---
title: Definindo uma imagem de plano de fundo em um diagrama | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 13e52e30ebeda4d881474bcf990068d1a92bb7f4
ms.lasthandoff: 02/22/2017

---
# <a name="setting-a-background-image-on-a-diagram"></a>Definindo uma imagem de plano de fundo em um diagrama
No SDK de Visualização e Modelagem do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você pode configurar a imagem de plano de fundo para um designer gerado usando código personalizado.  
  
## <a name="setting-the-background-image"></a>Configurando a imagem de plano de fundo  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Para configurar uma imagem de plano de fundo de um designer gerado  
  
1.  Copie o arquivo de imagem que você deseja usar como plano de fundo do diagrama no diretório Dsl\Resources do projeto atual.  
  
2.  Em **Solution Explorer**, clique na pasta Dsl\Resources, aponte para **adicionar**e, em seguida, clique em **Item existente**.  
  
3.  No **Add Existing Item** caixa de diálogo, navegue até a pasta dsl\resources..  
  
4.  No **arquivos do tipo** lista, clique em **arquivos de imagem**.  
  
5.  Clique no arquivo de imagem que você copiou para o diretório e, em seguida, clique em **adicionar**.  
  
6.  Clique com botão direito Dsl e, em seguida, clique em **propriedades** para abrir as propriedades do projeto Dsl.  
  
7.  Sobre o **recursos** , clique em **este projeto não contém um arquivo de recursos padrão. Clique aqui para criar um.**  
  
8.  Adicione o arquivo de imagem ao arquivo de recursos arrastando a imagem do **Solution Explorer** na janela de recursos.  
  
9. Abra o menu Arquivo e clique na opção para salvar as propriedades do projeto.  
  
10. Verifique se o arquivo Dsl\Properties\Resources.resx existe e se possui o arquivo Resources.Designer.cs nele.  
  
11. Se Resources.Designer.cs estiver ausente, clique no arquivo resx em **Solution Explorer**.  
  
12. No **propriedades** janela, defina a `Custom Tool` propriedade `ResXFileCodeGenerator`.  
  
13. Em **Solution Explorer**, com o botão direito no projeto Dsl, aponte para **adicionar**e clique em **nova pasta**.  
  
14. O nome da pasta **personalizado**.  
  
15. Com o botão direito na pasta personalizado, aponte para **adicionar**e clique em **Novo Item**.  
  
16. No **Adicionar Novo Item** na caixa de **modelos** lista, clique em **arquivo de código**.  
  
17. No **nome** , digite `BackgroundImage.cs`e clique em **adicionar**.  
  
18. Copie o código a seguir no arquivo BackgroundImage.cs, ajustando o namespace, o nome da classe do diagrama e o nome do recurso do arquivo de imagem.  
  
     Substitua "MyDiagramClass" pelo nome da classe parcial do diagrama definido em Dsl\GeneratedCode\Diagrams.cs. Também é possível recuperar o namespace correto do arquivo Dsl\GeneratedCode\Diagrams.cs.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Para obter mais informações sobre como personalizar o modelo com o código do programa, consulte [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Consulte também  
 [Definindo formas e conectores](../modeling/defining-shapes-and-connectors.md)   
 [Personalizando campos de imagem e texto](../modeling/customizing-text-and-image-fields.md)   
 [Navegando e atualizando um modelo no código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

