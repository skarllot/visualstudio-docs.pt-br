---
title: Matrizes tipadas (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 5fc3b29a4593e7c627a6e606242229e87fa5be54
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="typed-arrays-javascript"></a>Matrizes Tipadas (JavaScript)
Você pode usar matrizes tipadas para lidar com dados binários de fontes como protocolos de rede, formatos de arquivo binário e buffers de gráficos brutos. Matrizes tipadas também pode ser usadas para gerenciar dados binários na memória com layouts de bytes conhecidos.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar um [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) como a resposta de um [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Você pode manipular os bytes na resposta usando os diferentes métodos do [objeto DataView](../../javascript/reference/dataview-object.md) ou então copiando os bytes para a matriz tipada apropriada.  
  
> [!TIP]
>  Para saber mais sobre como usar tipos diferentes de resposta com um `XmlHttpRequest`, consulte [XMLHttpRequest.responseType](http://msdn.microsoft.com/en-us/8d7738d1-4bfd-4cf1-8015-174def089556), [Melhorias de XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069) e [Baixando diferentes tipos de conteúdo (Aplicativos da Windows Store)](http://msdn.microsoft.com/en-us/c0006bbd-17f9-4c6a-af81-2acaf109111d).  
  
```JavaScript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## <a name="arraybuffer"></a>ArrayBuffer  
 Um [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) representa um buffer de dados brutos usado para armazenar dados para as diferentes matrizes tipadas. Você não pode ler ou gravar em um `ArrayBuffer`, mas pode passá-lo para uma matriz tipada ou um [Objeto DataView](../../javascript/reference/dataview-object.md) para interpretar o buffer bruto. Você pode usar um `ArrayBuffer` para armazenar qualquer tipo de dados (ou tipos mistos de dados).  
  
## <a name="dataview"></a>DataView  
 Você pode usar um [Objeto DataView](../../javascript/reference/dataview-object.md) para ler e gravar os diferentes tipos de dados binários em qualquer parte do `ArrayBuffer`.  
  
## <a name="typed-arrays"></a>Matrizes Tipadas  
 Os tipos de matriz tipada representam modos de exibição de um [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md), que podem ser indexadas e manipuladas. Todos os tipos de matriz são de comprimento fixo.  
  
||||  
|-|-|-|  
|Nome|Tamanho (em bytes)|Descrição|  
|[Objeto Int8Array](../../javascript/reference/int8array-object.md)|1|Inteiro com sinal do complemento de dois de oito bits|  
|[Objeto Uint8Array](../../javascript/reference/uint8array-object.md)|1|Um inteiro de oito bits sem sinal|  
|[Objeto Int16Array](../../javascript/reference/int16array-object.md)|2|Inteiro com sinal do complemento de dois de 16 bits|  
|[Objeto Uint16Array](../../javascript/reference/uint16array-object.md)|2|Um inteiro de 16 bits sem sinal|  
|[Objeto Int32Array](../../javascript/reference/int32array-object.md)|4|Inteiro com sinal do complemento de dois de 32 bits|  
|[Objeto Uint32Array](../../javascript/reference/uint32array-object.md)|4|Um inteiro de 32 bits sem sinal|  
|[Objeto Float32Array](../../javascript/reference/float32array-object.md)|4|Ponto flutuante IEEE de 32 bits|  
|[Objeto Float64Array](../../javascript/reference/float64array-object.md)|8|Ponto flutuante IEEE de 64 bits|
