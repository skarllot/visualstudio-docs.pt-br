---
title: Calcular datas e horas (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- date and time arithmetic [JavaScript]
- JavaScript, date and time
- date comparison [JavaScript]
- date and time calculations [JavaScript]
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 18b4ff307c8f2c48a37ed9ca50e7c5f1ff693ece
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="calculating-dates-and-times-javascript"></a>Calculando datas e horas (JavaScript)
Você pode usar o [objeto Date](../javascript/reference/date-object-javascript.md) para executar tarefas de relógio e calendário comuns, tais como comparar datas e calcular o tempo decorrido.  
  
## <a name="setting-a-date-to-the-current-date"></a>Definindo uma Data como a Data Atual  
 Quando você cria uma instância do [objeto Date](../javascript/reference/date-object-javascript.md) sem especificar uma data, ela retorna um valor que representa a data e hora atuais, incluindo o ano, mês, dia, hora, minuto, segundo e milissegundo. Em seguida, você pode ler ou modificar essa data e hora.  
  
 O exemplo a seguir mostra como instanciar uma data sem o uso de parâmetros e exibi-la no formato *mm-dd-aa*.  
  
```JavaScript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## <a name="setting-a-specific-date"></a>Definindo uma Data Específica  
 Você pode definir uma data específica, passando uma cadeia de caracteres de data para o construtor.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  O fuso horário exibido na cadeia de caracteres de data corresponde ao fuso horário definido no computador local.  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] é flexível quanto ao formato da cadeia de caracteres que você pode usar como o parâmetro. Por exemplo, você pode inserir "8-24-2009", "24 de agosto de 2009" ou "24 ago 2009".  
  
 Você também pode especificar uma hora. O exemplo a seguir mostra uma maneira de especificar uma data e hora no formato ISO. "Z" indica a hora UTC.  
  
```JavaScript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 Para obter mais informações sobre formatos de data, tais como ISO, consulte [Cadeias de caracteres de data e hora](../javascript/date-and-time-strings-javascript.md).  
  
 O exemplo a seguir mostra outras maneiras de especificar uma hora.  
  
```JavaScript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## <a name="adding-and-subtracting-days-months-and-years"></a>Adicionando e Subtraindo Dias, Meses e Anos  
 Você pode usar os métodos de getX e setX do objeto `Date` para definir datas e horas específicas.  
  
 O exemplo a seguir mostra como você pode definir uma data para o dia anterior. Observe que, se necessário, os valores de mês e ano também são alterados.  
  
```JavaScript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 O exemplo a seguir define a data para o último dia do mês subtraindo um dia do primeiro dia do mês seguinte.  
  
> [!TIP]
>  Os meses do ano são numerados de 0 (janeiro) a 11 (dezembro). Os dias da semana são numerados de 0 (domingo) a 6 (sábado).  
  
```JavaScript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## <a name="working-with-days-of-the-week"></a>Trabalhando com Dias da Semana  
 O [método getDay](../javascript/reference/getday-method-date-javascript.md) obtém o dia da semana como um número entre 0 (domingo) e 6 (sábado). (Isso não é o mesmo que o [método getDate](../javascript/reference/getdate-method-date-javascript.md), que obtém o dia do mês como um número entre 1 e 31).  
  
 O exemplo a seguir define a data de Ação de Graças, que nos Estados Unidos é a quarta quinta-feira de novembro. O script encontra o dia 1º de novembro do ano atual, depois localiza a primeira quinta-feira e, em seguida, adiciona três semanas.  
  
```JavaScript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## <a name="calculating-elapsed-time"></a>Calculando Tempo Decorrido  
 O [método getTime](../javascript/reference/gettime-method-date-javascript.md) Retorna o número de milissegundos decorridos desde 1º de janeiro de 1970. Para qualquer data antes dessa, ele retorna um número negativo.  
  
 Você pode usar o [método getTime](../javascript/reference/gettime-method-date-javascript.md) para definir uma hora de início e de término para calcular um tempo decorrido. Ele pode ser usado para medir unidades pequenas, tais como alguns segundos e unidades grandes, tais como dias.  
  
 O exemplo a seguir calcula o tempo decorrido em segundos. O [método getTime](../javascript/reference/gettime-method-date-javascript.md) obtém o número de milissegundos desde a data zero.  
  
```JavaScript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 Para trabalhar com unidades mais gerenciáveis, você pode dividir os milissegundos fornecidos pelo [método getTime](../javascript/reference/gettime-method-date-javascript.md) por um número apropriado. Por exemplo, para transformar milissegundos em dias, divida o número por 86.400.000 (1.000 milissegundos x 60 segundos x 60 minutos x 24 horas).  
  
 O exemplo a seguir mostra o tempo decorrido desde o primeiro dia do ano especificado. Ele usa operações de divisão para calcular o tempo decorrido em dias, horas, minutos e segundos. Ele não considera o horário de verão.  
  
```JavaScript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### <a name="determining-the-users-age"></a>Determinando a Idade do Usuário  
 O exemplo a seguir usa o aniversário do usuário e calcula a idade dele em anos. Ele subtrai o ano do aniversário do ano atual e, em seguida, subtrai 1 se o aniversário ainda não ocorreu no ano atual.  
  
```JavaScript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## <a name="comparing-dates"></a>Comparando Datas  
 Ao comparar datas em [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], você deve ter em mente que o operador `==` retorna `true` somente se as datas em ambos os lados do operador se referem ao mesmo objeto. Portanto, se você tiver dois separado objetos `Date` definidos com a mesma data, `date1 == date2` retorna `false`. Além disso, um objeto `Date` definido com apenas a data e não o horário é inicializado para meia-noite dessa data. Portanto, se você comparar um `Date` definido sem uma hora especificada para `Date.now`, por exemplo, você deverá estar ciente de que o primeiro `Date` é definido para meia-noite e `Date.now` não é.  
  
 O exemplo a seguir verifica se a data atual é a mesmo, antes ou após uma data especificada. Para definir a data atual em `todayAtMidn`, o script cria um objeto `Date` para o ano, mês e dia atuais.  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 Modificando o exemplo anterior, podemos verificar se a data fornecida está dentro de um intervalo específico.  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Date](../javascript/reference/date-object-javascript.md)
