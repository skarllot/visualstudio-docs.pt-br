---
title: "Como exportar uma textura que contenha mipmaps | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 7
caps.handback.revision: 7
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Como exportar uma textura que contenha mipmaps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O Pipeline de Conteúdo da Imagem pode gerar mipmaps de uma imagem de origem como parte da fase de compilação do projeto.  Quando você não precisa especificar o conteúdo de imagem de cada nível de MIP manualmente \- como você pode fazer para obter certos efeitos \- a geração de mipmaps em tempo de compilação garante que os conteúdos de mipmap nunca se tornem fora de sincronia e elimina os custos de desempenho de geração de mipmaps em tempo de execução.  
  
 Este documento demonstra estas atividades:  
  
-   Configurando a imagem de origem a ser processada pelo Pipeline de Conteúdo da Imagem.  
  
-   Configurando o Pipeline de Conteúdo de Imagem para gerar mipmaps.  
  
## Exportando mipmaps  
 Mipmapping oferece um nível de detalhamento de espaço de tela automático para superfícies texturizadas em um jogo ou aplicativo 3D.  Melhora o desempenho de renderização de um jogo ou aplicativo ao pré\-computar versões com redução de resolução de uma textura de forma que toda a textura não precise ter a resolução reduzida sempre que houver uma amostragem.  
  
#### Para exportar uma textura que tem mipmaps  
  
1.  Comece com uma textura básica.  Carregue um arquivo de imagem existente ou crie um como descrito em [Como: criar uma textura básica](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md).  Para oferecer suporte a mipmaps, especifique uma textura que tenha uma largura e altura que apresentem ambas o mesmo poder de duas, por exemplo, 64x64, 256x256, ou 512x512.  
  
2.  Configure o arquivo de textura você acabou de criar de forma que ele seja processado pelo Pipeline de Conteúdo de Imagem.  No **Gerenciador de Soluções**, abra o menu de atalho para o arquivo de textura que você criou e, em seguida, selecione **Propriedades**.  Na página **Propriedades de Configuração**, **Geral**, defina a propriedade de **Tipo de Item** para **Pipeline de conteúdo de imagem**.  Certifique\-se de que a propriedade **Conteúdo** esteja definido como **Sim** e **Excluir de Compilação** esteja definido como **Não** e então escolha o botão **Aplicar**.  A página de propriedades de configuração **Pipeline de Conteúdo da Imagem** é exibida.  
  
3.  Configure o Pipeline de Conteúdo de Imagem para gerar mipmaps.  Na página **Propriedades de Configuração**, **Pipeline de Conteúdo de Imagem**, **Geral**, defina a propriedade de **Gerar Mips** para **Sim \(\/generatemips\)**.  
  
4.  Escolha o botão **OK**.  
  
 Quando você criar o projeto, o pipeline de conteúdo da imagem converte a imagem de origem de formato trabalhando no formato de saída que você especificou, incluindo níveis de MIP, e o resultado é copiado para o diretório de saída do projeto.