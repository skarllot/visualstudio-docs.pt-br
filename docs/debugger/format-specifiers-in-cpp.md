---
title: "Especificadores de formato em C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Caixa de diálogo QuickWatch, especificadores de formato em C++"
  - "variáveis [depurador], símbolos de variável de inspeção"
  - "símbolos de formatação de variável de inspeção"
  - "Caixa de diálogo QuickWatch, usando especificadores de formato"
  - "expressões [C++], especificadores de formato"
  - "especificadores de formato de variável de inspeção"
  - "especificadores"
  - "Janela de inspeção, especificadores de formato em C++"
  - "símbolos de variável de inspeção"
  - "especificadores de formato, o depurador"
  - "especificadores de formato reconhecidos pelo depurador"
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 40
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Especificadores de formato em C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode alterar o formato no qual um valor é exibido no **inspeção** janela usando especificadores de formato.  
  
 Você também pode usar especificadores de formato no **imediato** janela, o **comando** janela e até mesmo em janelas de origem. Se você pausar em uma expressão nessas janelas, o resultado será exibido em um DataTip. Tela DataTip reflete o especificador de formato.  
  
> [!NOTE]
>  O depurador nativo do Visual Studio alterado para um novo mecanismo de depuração. Como parte dessa alteração, alguns novos especificadores de formato foram adicionados e alguns antigos foram removidos. O depurador antigo ainda é usado quando você fizer interop \(nativa e gerenciada combinadas\) depuração com c\+\+ \/CLI. As seções a seguir neste tópico mostram os especificadores de formato para cada mecanismo de depuração.  
>   
>  -   [Especificadores de formato](#BKMK_Visual_Studio_2012_format_specifiers) Descreve os especificadores de formato no novo mecanismo de depuração.  
> -   [Especificadores de formato para depuração interop com c++ /CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) Descreve os especificadores de formato no mecanismo de depuração antigo.  
  
## Usando especificadores de formato  
 Se você tiver o código a seguir:  
  
```cpp  
int main() { int my_var1 = 0x0065; int my_var2 = 0x0066; int my_var3 = 0x0067; }  
```  
  
 Adicionar o `my_var1` variável para o **inspeção** janela \(durante a depuração, **Depurar \/ Windows \/ Assista \/ Assista 1**\) e defina a exibição hexadecimal \(no **inspeção** janela, a variável e selecione **Exibir Hexadecimal**\). Agora, a janela Watch mostra que ela contém o valor 0x0065. Para ver esse valor é expresso como um caractere em vez de um número inteiro, na coluna Nome, após o nome da variável, adicione o especificador de formato de caractere **, c**. O **valor** coluna agora é exibida com **101 'e'**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Especificadores de formato  
 As tabelas a seguir mostram os especificadores de formato que você pode usar no Visual Studio. Especificadores em negrito não têm suporte para depuração interop com c\+\+ \/CLI.  
  
|Especificador|Formato|Valor original de inspeção|Valor exibido|  
|-------------------|-------------|--------------------------------|-------------------|  
|d|inteiro decimal|0x00000066|102|  
|o|inteiro octal não assinado|0x00000066|000000000146|  
|x<br /><br /> **h**|inteiro hexadecimal|102|0xCCCCCCCC|  
|X<br /><br /> **H**|inteiro hexadecimal|102|0xCCCCCCCC|  
|c|caractere único|0x0065, c|101 'e'|  
|s|Const char \* de cadeia de caracteres|\< local \> "hello world"|"hello world"|  
|**SB**|Const char \* de cadeia de caracteres|\< local \> "hello world"|Olá mundo|  
|s8|Const char \* de cadeia de caracteres|\< local \> "hello world"|"hello world"|  
|**s8b**|Const char \* de cadeia de caracteres|\< local \> "hello world"|"hello world"|  
|Su|Const wchar\_t \* const<br /><br /> a cadeia de caracteres char16\_t \*|\< Local \> L "hello world"|L "hello world"<br /><br /> u "hello world"|  
|sub|Const wchar\_t \* const<br /><br /> a cadeia de caracteres char16\_t \*|\< Local \> L "hello world"|Olá mundo|  
|bstr|Cadeia de caracteres BSTR|\< Local \> L "hello world"|L "hello world"|  
|**s32**|Cadeia de caracteres UTF\-32|\< Local \> U "hello world"|U "hello world"|  
|**s32b**|Cadeia de caracteres UTF\-32 \(sem aspas\)|\< Local \> U "hello world"|Olá mundo|  
|**en**|enum|Saturday\(6\)|Sábado|  
|**hv**|Tipo de ponteiro \- indica que o valor de ponteiro que está sendo inspecionado é o resultado da alocação de heap de uma matriz, por exemplo, `new int[3]`.|\< local \> {\< primeiro membro \>}|\< local \> {\< primeiro membro \>, \< segundo membro \>,...}|  
|**na**|Suprime o endereço de memória de um ponteiro para um objeto.|\< local \> {membro \= value...}|{membro \= value...}|  
|**ND**|Exibe apenas as informações de classe base, ignorando as classes derivadas|`(Shape*) square` inclui a classe base e derivadas informações de classe|Exibe somente informações de classe de base|  
|hr|Código de erro HRESULT ou Win32. \(O depurador agora decodifica HRESULTs automaticamente, portanto esse especificador não é necessário nesses casos.|S\_OK|S\_OK|  
|WC|Sinalizador de classe de janela|0x0010|WC\_DEFAULTCHAR|  
|WM|Números de mensagens do Windows|16|WM\_CLOSE|  
|\!|formato bruto, ignorando qualquer personalização de exibições de tipo de dados|\< representação personalizada \>|4|  
  
> [!NOTE]
>  Quando o **hv** especificador de formato estiver presente, o depurador tenta determinar o comprimento do buffer e exibir o número apropriado de elementos. Como nem sempre é possível que o depurador encontrar o tamanho do buffer exata de uma matriz, você deve usar um especificador de tamanho `(pBuffer,[bufferSize])` sempre que possível. O **hv** especificador de formato é destinado a cenários onde o tamanho do buffer não está prontamente disponível  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Especificadores de tamanho para ponteiros como matrizes  
 Se você tiver um ponteiro para um objeto que você deseja exibir como uma matriz, você pode usar um número inteiro ou uma expressão para especificar o número de elementos da matriz:  
  
|Especificador|Formato|Valuen original de inspeção|Valor exibido|  
|-------------------|-------------|---------------------------------|-------------------|  
|n|Decimal ou **hexadecimal** inteiro|pBuffer, \[32\]<br /><br /> pBuffer,**\[0x20\]**|Exibe `pBuffer` como uma matriz de 32 elementos.|  
|**\[exp\]**|Uma expressão C\+\+ válida que é avaliada como um inteiro.|pBuffer, \[bufferSize\]|Exibe pBuffer como uma matriz de `bufferSize` elementos.|  
|**expand\(n\)**|Uma expressão C\+\+ válida que é avaliada como um inteiro|pBuffer, expand\(2\)|Exibe o terceiro elemento de  `pBuffer`|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Especificadores de formato para depuração interop com c\+\+ \/CLI  
 Especificadores em **negrito** têm suporte apenas para depuração nativos e c\+\+ \/CLI.  
  
|Especificador|Formato|Valor original de inspeção|Valor exibido|  
|-------------------|-------------|--------------------------------|-------------------|  
|**d, i**|inteiro decimal assinado|0xF000F065|\-268373915|  
|**u**|inteiro decimal não assinado|0x0065|101|  
|o|inteiro octal não assinado|0xF065|0170145|  
|x, X|Inteiro hexadecimal|61541|0x0000F065|  
|**l, h**|prefixo longo ou curto para: d, i, u, s, x, X|00406042|0x0c22|  
|**f**|ponto flutuante assinado|\(3. \/ 2.\), f|1.500000|  
|**e**|notação científica assinada|\(3.0\/2.0\)|1.500000e \+ 000|  
|**g**g|ponto flutuante assinado ou notação científica assinada, o que for menor|\(3.0\/2.0\)|1.5|  
|c|caractere único|\< local \>|101 'e'|  
|s|Const char \*|\< local \>|"hello world"|  
|Su|Const wchar\_t \*<br /><br /> Const char16\_t \*|\< local \>|L "hello world"|  
|sub|Const wchar\_t \*<br /><br /> Const char16\_t \*|\< local \>|Olá mundo|  
|s8|Const char \*|\< local \>|"hello world"|  
|hr|Código de erro HRESULT ou Win32. \(O depurador agora decodifica HRESULTs automaticamente, portanto esse especificador não é necessário nesses casos.|S\_OK|S\_OK|  
|WC|Sinalizador de classe de janela.|0x00000040,|WC\_DEFAULTCHAR|  
|WM|Números de mensagens do Windows|0x0010|WM\_CLOSE|  
|\!|formato bruto, ignorando qualquer personalização de exibições de tipo de dados|\< representação personalizada \>|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Formatar locais de memória de especificadores em depuração interop com c\+\+ \/CLI  
 A tabela a seguir contém símbolos de formatação usados para locais de memória. Você pode usar um especificador de local da memória com qualquer valor ou expressão que é avaliada para um local.  
  
|Símbolo|Formato|Valor original de inspeção|Valor exibido|  
|-------------|-------------|--------------------------------|-------------------|  
|**ma**|64 caracteres ASCII|0x0012ffac|0x0012ffac. 4... 0... ". 0W &... 1s &.0.:W... 1....".. 1. JOANA &.1.2... "... 1... 0y... 1|  
|**m**|16 bytes em hexadecimal, seguido por 16 caracteres ASCII|0x0012ffac|0X0012FFAC B3 34 FF CB 00 84 30 94 80 22 8A 30 57 26 00 00. 4... 0... ". 0W &...|  
|**MB**|16 bytes em hexadecimal, seguido por 16 caracteres ASCII|0x0012ffac|0X0012FFAC B3 34 FF CB 00 84 30 94 80 22 8A 30 57 26 00 00. 4... 0... ". 0W &...|  
|**mW**|8 palavras|0x0012ffac|0X0012FFAC 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**MD**|4 palavra duplas|0x0012ffac|0X0012FFAC 00CB34B3 80943084 308A22FF 00002657|  
|**MQ**|2 palavras quádruplas|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**MU**|caracteres de 2 bytes \(Unicode\)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Especificador de tamanho para ponteiros como matrizes em depuração interop com C\+\+ \/CLI CLIt  
 Se você tiver um ponteiro para um objeto que você deseja exibir como uma matriz, você pode usar um número inteiro para especificar o número de elementos da matriz:  
  
|Especificador|Formato|Expressão|Valor exibido|  
|-------------------|-------------|---------------|-------------------|  
|n|Inteiro decimal|pBuffer \[32\]|Exibe `pBuffer` como uma matriz de 32 elementos.|