---
title: Como exportar uma textura que contenha mipmaps | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 7
author: BrianPeek
ms.author: brpeek
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 2176086d813109a92f1e2467498d3f1ad4b18c5e
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Como exportar uma textura que contenha mipmaps
O Pipeline de conteúdo de imagem pode gerar mipmaps de uma imagem de origem como parte da fase de build do projeto. Quando você não precisa especificar o conteúdo da imagem de cada nível MIP manualmente, como você poderia fazer para obter certos efeitos, gerar mipmaps em tempo de build garante que o conteúdo de mipmap nunca fique fora de sincronia e elimina o custo de desempenho de gerar mipmaps no tempo de execução.  
  
 Este documento demonstra essas atividades:  
  
-   Configurando a imagem de origem a ser processada pelo Pipeline de conteúdo da imagem.  
  
-   Configurando o Pipeline de conteúdo de imagem para gerar mipmaps.  
  
## <a name="exporting-mipmaps"></a>Exportando mipmaps  
 O mapeamento mip fornece o nível de detalhe do espaço de tela automático para superfícies com textura em um aplicativo ou jogo 3D. Aumenta o desempenho de renderização de um jogo ou aplicativo ao pré-computar versões de resolução reduzida de uma textura para que toda a textura não precise ser convertida sempre que for amostrada.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Para exportar uma textura que contenha mipmaps  
  
1.  Comece com uma textura básica. Carregue um arquivo de imagem existente ou crie um conforme descrito em [Como criar uma textura básica](../designers/how-to-create-a-basic-texture.md). Para oferecer suporte a mipmaps, especifique uma textura que tenha uma largura e altura que sejam as mesmas, por exemplo, 64x64, 256x256 ou 512x512.  
  
2.  Configure o arquivo de textura que você acabou de criar para que ele seja processado pelo Pipeline de conteúdo de imagem. No **Gerenciador de Soluções**, abra o menu de atalho do arquivo de textura que acabou de criar e selecione **Propriedades**. Na página **Propriedades de Configuração**, **Geral**, defina a propriedade **Tipo de Item** como **Pipeline de Conteúdo de Imagem**. Verifique se a propriedade **Conteúdo** está definida como **Sim** e se **Excluir do Build** está definido como **Não** e, em seguida, escolha o botão **Aplicar**. A página de propriedades de configuração **Pipeline de Conteúdo de Imagem** é exibida.  
  
3.  Configure o Pipeline de conteúdo de imagem para gerar mipmaps. Na página **Propriedades de Configuração**, **Pipeline de Conteúdo de Imagem**, **Geral**, defina a propriedade **Gerar mips** como **Sim (/generatemips)**.  
  
4.  Selecione o botão **OK**.  
  
 Quando você cria o projeto, o Pipeline de conteúdo de imagem converte a imagem de origem do formato de trabalho para o formato de saída que você especificou, incluindo níveis de MIP e o resultado é copiado para o diretório de saída do projeto.
