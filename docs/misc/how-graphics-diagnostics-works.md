---
title: "Como o diagn&#243;stico de gr&#225;ficos funciona | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ae14497-c77c-4399-bc0c-595caba23656
caps.latest.revision: 2
caps.handback.revision: 2
ms.author: "mithom"
manager: "douge"
---
# Como o diagn&#243;stico de gr&#225;ficos funciona
Insira a introdução aqui.  
  
## Como funciona o diagnóstico de gráficos  
 Para usar o diagnóstico de gráficos, primeiramente você grava informações sobre como um aplicativo usa a API do Direct3D enquanto ele é executado e, posteriormente, examina o comportamento gravado. Para os quadros especificados, as informações que são registradas incluem chamadas de API, como aqueles que limpam a tela, desenham geometria, distribuem sombreadores de cálculo ou alterar o estado do dispositivo gráfico — junto com seus argumentos e cópias de buffers e objetos que são referenciados indiretamente. Além disso, a API chamadas relacionadas à configuração e inicialização são registradas antes de todos os quadros são renderizados. As informações que serão registradas são gravadas para um *log de gráficos* arquivo \(. vsglog\).  
  
 Recrie o comportamento de renderização é registrado no log de gráficos reproduzindo os eventos de gráficos em sua máquina de desenvolvimento ou em um dispositivo ou computador remoto. A máquina de reprodução pode ser o mesmo computador ou dispositivo em que o log de gráficos foi originalmente capturado ou um diferente. Para a maioria dos recursos de reprodução, o hardware de gráficos do computador de reprodução é usado para reproduzir eventos de gráficos, mas quando o depurador HLSL é usado, o código de sombreador sempre é reproduzido usando uma GPU emulada na CPU. Usar uma GPU emulada possibilita percorrer o código de sombreador, inspecionar variáveis e usar outros recursos de depuração comuns, independentemente se o hardware de gráficos na máquina de reprodução oferece suporte à depuração de hardware.  
  
> [!NOTE]
>  Embora um log de gráficos Capture a maioria das informações relevantes internamente, informações adicionais são necessárias para utilizar totalmente a alguns recursos de diagnóstico de gráficos. Por exemplo, para fazer com que o uso total dos elementos gráficos recurso de pilha de chamada, você também precisa ter o arquivo de banco de dados \(. PDB\) do programa e código\-fonte do aplicativo. Para depurar o código fonte do sombreador HLSL, você também precisa ter o código fonte do sombreador. \(Se o sombreador foi compilado usando o compilador de sombreador D3D 11.1 e as informações de depuração está habilitada, em seguida, código fonte do sombreador será inserido no log de gráficos durante a captura.\)  
  
> [!NOTE]
>  Como determinadas APIs podem não estar disponíveis em versões anteriores do Windows ou do DirectX, é possível reproduzir logs de gráficos capturadas essas chamadas de API em uma máquina de reprodução que não oferece suporte a eles.  
  
### Logs de gráficos  
 Um log de gráficos contém um ou mais quadros capturados de um aplicativo de elementos gráficos DirectX em execução. Como um log de gráficos é independente, esses quadros podem ser recriados posteriormente e sem referências ou informações externas. Isso significa que você pode compartilhar logs de gráficos com outros desenvolvedores, examinar problemas em máquinas diferentes e examinar logs de gráfico antigos mesmo quando os modelos e texturas foram alteradas no desenvolvimento. Você também pode carregar vários arquivos de log \(. vsglog\) de elementos gráficos ao mesmo tempo para comparar dados e resultados de renderização.  
  
##### Para abrir um arquivo de log \(vsglog\) do gráfico  
  
1.  Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], na barra de menus, escolha **arquivo**, **Abrir**, **arquivo**. O **Abrir arquivo** caixa de diálogo é exibida.  
  
2.  Especifique um arquivo de log \(. vsglog\) do gráfico para abrir e, em seguida, escolha o **Abrir** botão.  
  
> [!NOTE]
>  Você pode extrair, modificar e salvar cópias de malhas e texturas de um log de gráficos usando as ferramentas de gráficos que fazem parte do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. No entanto, o conteúdo do log de gráficos não é afetado por essas modificações. Para obter informações sobre essas ferramentas de gráficos, consulte [Trabalhando com ativos 3D para jogos e aplicativos](../designers/working-with-3-d-assets-for-games-and-apps.md).