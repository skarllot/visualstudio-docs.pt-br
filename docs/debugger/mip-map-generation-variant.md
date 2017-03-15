---
title: "Variante de gera&#231;&#227;o de Mip-map | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Variante de gera&#231;&#227;o de Mip-map
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Habilita mapas mip em texturas que não são destinos de renderização.  
  
## Interpretação  
 Os mapas mip são usados principalmente para eliminar artefatos de suavização das texturas que estão passando por minificação. Isso é possível com o cálculo prévio de versões menores da textura.  Embora essas texturas adicionais consumam cerca de 33% mais memória da GPU que a textura original, elas também são mais eficientes porque o cache da textura da GPU comporta uma área de superfície maior dessa textura, o que faz com que seu conteúdo seja mais utilizado.  
  
 Recomendamos usar mapas mip nas cenas 3D quando houver memória disponível para armazenar texturas adicionais porque eles aumentam o desempenho da renderização e a qualidade da imagem.  
  
 Se essa variante tiver um ganho de desempenho considerável, é sinal de que você está usando as texturas sem habilitar os mapas mip e, por isso, não está aproveitando ao máximo o cache da textura.  
  
## Comentários  
 A geração do mapa mip é forçada em cada chamada de `ID3D11Device::CreateTexture2D` que cria uma textura de origem.  A geração do mapa mip é forçada, especificamente, quando o objeto D3D11\_TEXTUR2D\_DESC apresentado a `pDesc` descreve um recurso do sombreador inalterável, ou seja:  
  
-   O membro BindFlags tem apenas o sinalizador D3D11\_BIND\_SHADER\_RESOURCE definido.  
  
-   O membro Uso está definido como D3D11\_USAGE\_DEFAULT ou D3D11\_USAGE\_IMMUTABLE.  
  
-   O membro CPUAccessFlags está definido como 0 \(sem acesso à CPU\).  
  
-   O membro SampleDesc tem seu membro Count definido como 1 \(sem MSAA \(suavização de amostra múltipla\)\).  
  
-   O membro MipLevels está definido como 1 \(não há mapas mip\).  
  
 Quando o aplicativo fornece os dados iniciais, o formato da textura deve permitir a geração de mapas mip automaticamente — conforme determinado por D3D11\_FORMAT\_SUPPORT\_MIP\_AUTOGEN —, a menos que o formato usado seja BC1, BC2 ou BC3. Caso contrário, a textura não é modificada e o mapa mip não é gerado após o fornecimento dos dados iniciais.  
  
 Quando há mapas mip gerados automaticamente para uma textura, as chamadas de `ID3D11Device::CreateShaderResourceView` são modificadas durante a reprodução para usar a cadeia de mip durante a amostragem da textura.  
  
## Exemplo  
 A variante **Geração de Mapa Mip** pode ser reproduzida por um código como este:  
  
```  
D3D11_TEXTURE2D_DESC texture_description;  
  
// ...  
  
texture_description.MipLevels = 0; // generate a full mipchain  
  
std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);  
  
for (auto&& mip_level : initial_data)  
{  
    // fill mip_level with the application-supplied initial data  
}  
  
d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)  
```  
  
 Para criar uma textura com cadeia de mip completa, defina `D3D11_TEXTURE2D_DESC::MipLevels` como 0.  A quantidade de níveis de mip presentes em uma cadeia de mip completa é expressa por floor\(log2\(n\) \+ 1\), em que n é a maior dimensão da textura.  
  
 Lembre\-se de que ao fornecer os dados iniciais para `CreateTexture2D`, você também deve fornecer um objeto D3D11\_SUBRESOURCE\_DATA para cada nível de mip.  
  
> [!NOTE]
>  Se quiser fornecer seu próprio conteúdo aos níveis de mip em vez de gerá\-lo automaticamente, crie as texturas usando um editor de imagens compatível com texturas com mapas mip. Em seguida, carregue o arquivo e transmita os níveis de mip a `CreateTexture2D`.  
  
## Consulte também  
 [Variante de metade\/um quarto nas dimensões de textura](../debugger/half-quarter-texture-dimensions-variant.md)