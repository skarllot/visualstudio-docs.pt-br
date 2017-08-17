---
title: Cadeias de caracteres de Data e Hora (JavaScript) | Microsoft Docs
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
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6218ba273b26243382d1e825b6da961d604917ab
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="date-and-time-strings-javascript"></a>Cadeias de caracteres de data e hora (JavaScript)
Você pode usar diversas técnicas para especificar e formatar cadeias de caracteres de data e hora do JavaScript.  
  
## <a name="formatting-dates-using-intldatetimeformat"></a>Formatando datas usando Intl.DateTimeFormat  
 O Internet Explorer 11 introduz o suporte ao [Objeto Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md), que faz parte da [Especificação de API de Internacionalização do ECMAScript](http://www.ecma-international.org/ecma-402/1.0/). Para formatar datas, você pode usar esse objeto diretamente ou você pode usar a implementação atualizada do [método toLocaleDateString (Date)](../javascript/reference/tolocaledatestring-method-date-javascript.md) e do [método toLocaleTimeString (Date)](../javascript/reference/tolocaletimestring-method-date-javascript.md). Esses métodos do [Objeto Date](../javascript/reference/date-object-javascript.md) usam `Intl.DateTimeFormat` internamente para garantir a compatibilidade de novos parâmetros opcionais para a localidade e outras opções de formatação.  
  
 Os exemplos a seguir mostram como usar `toLocaleDateString` e `toLocaleTimeString` para formatar datas e horas. O primeiro parâmetro transmitido a esses métodos é um valor de localidade, como "en-us". Quando presente, o segundo parâmetro especifica as opções de formatação, como o dia útil por extenso.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 Para obter uma lista com todas as opções de formatação, confira [Objeto Intl.DateTimeFormat](../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
## <a name="formatting-dates"></a>Formatando datas  
 Antes do Internet Explorer 11, o JavaScript não tinha métodos específicos para formatar datas e horas. Para fornecer sua própria formatação de data para versões anteriores do navegador, use os métodos [getDay (Date)](../javascript/reference/getday-method-date-javascript.md), [getDate (Date)](../javascript/reference/getdate-method-date-javascript.md), [getMonth (Date)](../javascript/reference/getmonth-method-date-javascript.md) e [getFullYear (Date)](../javascript/reference/getfullyear-method-date-javascript.md). (O [método getYear (Date)](../javascript/reference/getyear-method-date-javascript.md) é obsoleto e não deve ser usado.)  
  
```JavaScript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 Você pode fornecer seu próprio tempo formatação usando os métodos [getHours (Date)](../javascript/reference/gethours-method-date-javascript.md), [getMinutes (Date)](../javascript/reference/getminutes-method-date-javascript.md), [getSeconds (Date)](../javascript/reference/getseconds-method-date-javascript.md) e [getMilliseconds (Date)](../javascript/reference/getmilliseconds-method-date-javascript.md).  
  
```JavaScript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +   
":" + myDate.getMilliseconds());  
  
// Output:   
// 10:30:53:400  
```  
  
## <a name="converting-strings-to-dates"></a>Convertendo cadeias de caracteres em datas  
 Você pode especificar as cadeias de caracteres para criar objetos `Date` com `Date(dateStr)` ou `Date.parse(dateStr)`. O JavaScript usa estas regras para analisar cadeias de caracteres de datas:  
  
-   Primeiro, ele tenta analisar a cadeia de caracteres da data usando o [Formato de data ISO](#ISO).  
  
    > [!NOTE]
    >  O JavaScript usa uma versão simplificada do formato estendido ISO 8601.  
  
-   Se a cadeia de caracteres de data não estiver no formato ISO, o JavaScript tenta analisar a data usando [outros formatos de data](#OtherDateFormats).  
  
<a name="ISO"></a>   
## <a name="iso-date-format"></a>Formato de data ISO  
 O formato ISO é uma versão simplificada do formato estendido ISO 8601. O formato é o seguinte:  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  O formato de data ISO não é compatível com o modo-padrão do Internet Explorer 8 nem com o modo Quirks.  
  
 A tabela a seguir descreve os elementos que compõem esse formato.  
  
|Símbolo|Descrição|Valores|  
|------------|-----------------|------------|  
|`-`, `:`, `.`, `T`|Os caracteres da cadeia. `T` especifica a hora de início.||  
|`YYYY`|Ano. Você pode usar o ano estendido, em vez do ano com quatro dígitos. Para obter mais informações, consulte [Anos Estendidos](../javascript/date-and-time-strings-javascript.md#bkmk_extend) posteriormente neste tópico.||  
|`MM`|Mês|De 01 a 12|  
|`DD`|Dia do mês|De 01 a 31|  
|`HH`|Horas|De 00 a 24|  
|`mm`|Minutos|De 00 a 59|  
|`ss`|Segundos. Os segundos e milésimos de segundos são opcionais.|De 00 a 59|  
|`sss`|Milésimos de segundos|De 00 a 999|  
|`Z`|O valor dessa campo pode ser uma das opções apresentadas a seguir. Se o valor está omitido, é usada a hora do fuso UTC.<br /><br /> -   `Z` indica a hora UTC.<br />-   `+hh:mm` indica que a hora de entrada é o deslocamento especificado à frente da hora UTC.<br />-   `-hh:mm` indica que a hora de entrada é o valor absoluto do deslocamento especificado atrás da hora UTC.||  
  
 A cadeia de caracteres pode incluir somente a data, como nestes formatos: `YYYY`, `YYYY-MM`, `YYYY-MM-DD`.  
  
 O formato ISO não permite usar os nomes dos fusos horários. Você pode usar a posição `Z` para especificar um deslocamento em relação à hora do fuso UTC. Quando você não insere um valor na posição `Z`, a hora do fuso UTC é usada.  
  
 Para especificar meia-noite, use 00:00 ou 24:00 com a data do dia anterior. Estas duas cadeias de caracteres especificam a mesma hora: 2010-05-25T00:00 e 2010-05-24T24:00.  
  
 Para retornar uma data no formato ISO, você pode usar o [método toISOString (Date)](../javascript/reference/toisostring-method-date-javascript.md).  
  
<a name="bkmk_extend"></a>   
### <a name="extended-years"></a>Anos Estendidos  
 Um *ano estendido* tem seis dígitos em vez de quatro e começa com um sinal de mais ou menos. Um exemplo de ano estendido é `+002010`, que equivale a `2010`. Você pode usar o ano estendido para representar os anos anteriores a 0 ou posteriores a 9999.  
  
 Se você usar o formato com seis dígitos, deve haver um sinal de mais ou menos. Quando você usa o formato com quatro dígitos, o sinal não deve aparecer. Portanto, `0000` e `+000000` são aceitos, mas `000000` e `-0001` causam erro. O ano estendido 0 é considerado um valor positivo e, por isso, recebe um sinal de mais.  
  
 O [método toISOString (Date)](../javascript/reference/toisostring-method-date-javascript.md) sempre usa o formato de ano estendido para anos anteriores a 0 e posteriores a 9999.  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## <a name="other-date-formats"></a>Outros Formatos de Data  
 Se a cadeia de caracteres de uma data não estiver no formato ISO, o [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] usa as regras a seguir para analisá-la.  
  
 Datas abreviadas  
  
-   O formato deve seguir a ordem mês/dia/ano (ex.: "06/08/2010").  
  
-   Use "/" ou "-" como separador.  
  
 Datas completas  
  
-   O ano, mês e dia podem aparecer em qualquer ordem. Os opções "8 de junho de 2010" e "2010, 8 de junho" são válidas.  
  
-   O ano pode ter dois ou quatro dígitos. Se o ano tiver apenas dois dígitos, ele deve ser posterior a 70.  
  
-   Os nomes dos meses e dias devem ter pelo menos dois caracteres. Quando há mais de um nome para o mesmo caractere, o problema é resolvido com o último nome correspondente. Por exemplo, "Ju" especifica julho, não junho.  
  
-   O sistema ignora o dia da semana se ele não estiver seguindo o mesmo padrão das demais datas fornecidas. Por exemplo, "Terça-feira, 9 de novembro de 1996" torna-se "Sexta-feira, 9 de novembro de 1996" porque esse é o dia da semana correspondente a essa data.  
  
 Horas  
  
-   As horas, os minutos e os segundos são separados por dois-pontos. No entanto, você pode omitir algumas partes. Estes valores são válidos: "10:", "10:11" e "10:11:12".  
  
-   Se você especificar PM e a hora especificada for igual ou superior a 13, a constante NaN (Não é um Número) é exibida. Por exemplo, "23:15 PM" resulta na constante NaN.  
  
 Geral  
  
-   Uma cadeia de caracteres que contém uma data inválida retorna NaN. Por exemplo, uma cadeia com dois anos ou dois meses retorna NaN.  
  
-   O [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] permite usar todos os fusos horários, além dos fusos UTC (Tempo Universal Coordenado) e GMT (Horário de Greenwich). O formato ISO não permite usar fusos horários.  
  
-   O texto entre parênteses é considerado um comentário. Você pode aninhar os parênteses.  
  
-   As vírgulas e os espaços são considerados delimitadores. Você pode usar diversos delimitadores.  
  
## <a name="example"></a>Exemplo  
 O código a seguir exibe os resultados da análise de diferentes cadeias de caracteres de data e hora.  
  
```  
document.writeln((new Date("2010")).toUTCString());   
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 Quando a hora local é especificada, o resultado varia de acordo com o fuso horário.  
  
> [!IMPORTANT]
>  O formato de data ISO não é compatível com o modo-padrão do Internet Explorer 8 nem com o modo Quirks.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Date](../javascript/reference/date-object-javascript.md)   
 [Função Date.parse](../javascript/reference/date-parse-function-javascript.md)
