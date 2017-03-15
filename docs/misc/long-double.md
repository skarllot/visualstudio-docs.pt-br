---
title: "Duplo longo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "10 bytes duplos longos"
  - "Windows de 16 bits"
  - "Windows de 32 bits"
  - "8 bytes duplos longos"
  - "precisão de 80 bits"
  - "precisão de 80 bits"
  - "8 bytes duplos longos"
  - "duplo longo"
ms.assetid: bb581e20-b5c2-4079-8ee8-ac6739a37852
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Duplo longo
As versões de 16 bits anteriores do Microsoft C\/C\+\+ e Microsoft Visual C\+\+ com suporte `long double`, tipo de dados de precisão de 80 bits.  No Win32 que programas, no entanto, os mapas a `double`, tipo de dados de 64 bits do tipo de dados de `long double` de precisão.  A biblioteca de tempo de execução Microsoft fornece versões de `long double` das funções matemáticas somente para compatibilidade com versões anteriores.  Os protótipos de função de `long double` são idênticos aos protótipos para suas contrapartes de `double` , exceto que o tipo de dados de `long``double` substitui o tipo de dados de `double` .  As versões de `long double` dessas funções não devem ser usadas no novo código.  
  
### Funções duplas e suas contrapartes duplas demoradas  
  
|Função|Double longo<br /><br /> contrapartes|Função|Double longo<br /><br /> contrapartes|  
|------------|-----------------------------------|------------|-----------------------------------|  
|[acos](/visual-cpp/c-runtime-library/reference/acos-acosf-acosl)|`acosl`|[frexp](/visual-cpp/c-runtime-library/reference/frexp)|`frexpl`|  
|[asin](/visual-cpp/c-runtime-library/reference/asin-asinf-asinl)|`asinl`|[\_hypot](/visual-cpp/c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl)|`_hypotl`|  
|[atan](/visual-cpp/c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l)|`atanl`|[ldexp](/visual-cpp/c-runtime-library/reference/ldexp)|`ldexpl`|  
|[atan2](/visual-cpp/c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l)|`atan2l`|[log](/visual-cpp/c-runtime-library/reference/log-logf-log10-log10f)|`logl`|  
|[atof](/visual-cpp/c-runtime-library/reference/atof-atof-l-wtof-wtof-l)|`_atold`|[log10](/visual-cpp/c-runtime-library/reference/log-logf-log10-log10f)|`log10l`|  
|[Funções de Bessel j0, j1, jn](../misc/bessel-functions-j0-j1-jn.md)|`j0l, j1l, jnl`|[\_matherr](/visual-cpp/c-runtime-library/reference/matherr)|`_matherrl`|  
|[Funções de Bessel YO, y1, yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|`y0l, y1l, ynl`|[modf](/visual-cpp/c-runtime-library/reference/modf-modff-modfl)|`modfl`|  
|[\_cabs](/visual-cpp/c-runtime-library/reference/cabs)|`_cabsl`|[prisioneiro de guerra](/visual-cpp/c-runtime-library/reference/pow-powf-powl)|`powl`|  
|[ceil](/visual-cpp/c-runtime-library/reference/ceil-ceilf-ceill)|`ceill`|[sin](/visual-cpp/c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl)|`sinl`|  
|[cos](/visual-cpp/c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl)|`cosl`|[sinh](/visual-cpp/c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl)|`sinhl`|  
|[moca](/visual-cpp/c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl)|`coshl`|[SQRT](/visual-cpp/c-runtime-library/reference/sqrt-sqrtf-sqrtl)|`sqrtl`|  
|[EXP](/visual-cpp/c-runtime-library/reference/exp-expf)|`expl`|[strtod](/visual-cpp/c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l)|`_strtold`|  
|[fabs](/visual-cpp/c-runtime-library/reference/fabs-fabsf-fabsl)|`fabsl`|[tan](/visual-cpp/c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl)|`tanl`|  
|[floor](/visual-cpp/c-runtime-library/reference/floor-floorf-floorl)|`floorl`|[tanh](/visual-cpp/c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl)|`tanhl`|  
|[fmod](/visual-cpp/c-runtime-library/reference/fmod-fmodf)|`fmodl`|||  
  
## Consulte também  
 [Rotinas de tempo de execução por categoria](/visual-cpp/c-runtime-library/run-time-routines-by-category)