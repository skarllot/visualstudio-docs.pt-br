---
title: Propriedades de decoradores | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 23
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 23288d1afe9b9c0a181a5d978b1956071b683218
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-decorators"></a>Propriedades de decoradores
Decoradores são ícones, texto ou expandir/recolher divisas que podem aparecer em formas ou conectores no diagrama. As tabelas a seguir mostram as propriedades para os três tipos de decorador. Algumas das propriedades aparecem somente em decoradores de forma ou somente em decoradores de conector.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Expandir/recolher decorador  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DisplayName|O nome do decorador que será exibido no designer gerado.|Expanda recolher decorador|  
|Nome|O nome do decorador.|ExpandCollapseDecorator|  
|Observações|Notas informais associadas este decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação a posição padrão de decorador, em polegadas. (Nas formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação a posição padrão de decorador, em polegadas. (Nas formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador de shape, relativo à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|OrigemSuperior|  
  
## <a name="icon-decorator"></a>Ícone decorador  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DefaultIcon|O caminho do arquivo de ícone ou imagem a ser exibida.|\<Nenhum >|  
|DisplayName|O nome do decorador a ser exibido no designer gerado.|Ícone decorador|  
|Nome|O nome do decorador.|IconDecorator|  
|Observações|Notas informais associadas decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação a posição padrão de decorador, em polegadas. (Nas formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação a posição padrão de decorador, em polegadas. (Nas formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador de shape, relativo à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|OrigemSuperior|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DefaultText|O texto padrão a ser exibido.|Rotular|  
|DisplayName|O nome do decorador a ser exibido no designer gerado.|Rotular|  
|FontSize|O tamanho da fonte para o texto que é exibido no decorador.|8|  
|FontStyle|O estilo da fonte para o texto que é exibido no decorador.|Normal|  
|Nome|O nome do decorador.|Rotular|  
|Observações|Notas informais associadas decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação a posição padrão de decorador, em polegadas. (Nas formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação a posição padrão de decorador, em polegadas. (Nas formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador de shape, relativo à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|DestinoInferior|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
