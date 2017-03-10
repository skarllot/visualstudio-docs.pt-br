---
title: "Pr&#225;ticas recomendadas e exemplos (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Pr&#225;ticas recomendadas e exemplos (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aqui estão algumas maneiras de tirar o máximo proveito fora do idioma da anotação do código\-fonte SAL \(\) e de evitar alguns problemas comuns.  
  
## \_In\_  
 Se a função deve gravar no elemento, use `_Inout_` em vez de `_In_`.  Isso é particularmente relevante em casos de conversão automática de um macros mais antigos para o SAL.  Antes de SAL, muitos desenvolvedores usam macros como os comentário\- macros que foram nomeadas `IN`, `OUT`, `IN_OUT`, ou variantes desses nomes.  Embora recomendemos as que você converter esses macros ao SAL, é também incitamo\-lo ter cuidado quando você converte os porque o código pode ter modificado desde que o protótipo original foi gravada e a macro antigo pode não refletir o que o código faz.  É muito cuidado a macro de comentário de `OPTIONAL` porque é colocado frequentemente incorreto\- por exemplo, no lado incorreto de uma vírgula.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ int *p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
// Correct  
void Func2(_Inout_ PCHAR p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
```  
  
## \_opt\_  
 Se não é permitido ao chamador passar um ponteiro nulo, use `_In_` ou em `_Out_` em vez de `_In_opt_` ou de `_Out_opt_`.  Isso se aplica a uma função que verifica os parâmetros e retornará um erro se for NULL quando não deve ser.  Embora tendo uma verificação de função NULL para o parâmetro e inesperados retorno normalmente é uma boa prática de codificação defensiva, não significa que a anotação do parâmetro pode ser de um tipo opcional \(\_*Xxx*\_opt\_\).  
  
```cpp  
  
// Incorrect  
void Func1(_Out_opt_ int *p1)  
{  
    *p = 1;  
}  
  
// Correct  
void Func2(_Out_ int *p1)  
{  
    *p = 1;  
}  
  
```  
  
## \_Pre\_defensive\_ e \_Post\_defensive\_  
 Se uma função é exibida em um limite confiável, recomendamos que você use a anotação de `_Pre_defensive_` .  O modificador “defensivo” altera algumas anotações para indicar que, no ponto da chamada, a interface deve ser verificada restrita, mas no corpo da implementação deve considerar que os parâmetros incorretos podem ser passados.  Nesse caso, `_In_ _Pre_defensive_` é preferencial em um limite confiável indicar que embora um chamador obter um erro se tenta transmitir NULL, o corpo da função será analisada como se o parâmetro pode ser NULL e, todas a eliminação de referência de tentativas o ponteiro sem verificar primeiro para NULL será sinalizada.  Uma anotação de `_Post_defensive_` também está disponível, para uso nos retornos de chamada onde a parte de confiança é usada para ser o chamador e o código não confiável é o código chamado.  
  
## \_Out\_writes\_  
 O exemplo a seguir demonstra um significado errado comuns de `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 A anotação `_Out_writes_` significa que você tem um buffer.  Tem bytes de `cb` atribuídos, com o primeiro byte inicializado na saída.  Essa anotação não é estritamente incorreta e é útil expressar o tamanho alocado.  Porém, o não informa quantos elementos são inicializados pela função.  
  
 O exemplo a seguir mostra três maneiras corretas de especificar completamente o tamanho exato da parte inicializada de buffer.  
  
```cpp  
  
// Correct  
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,   
    DWORD size,  
    PDWORD pCount  
);  
  
void Func2(_Out_writes_all_(size) CHAR *pb,   
    DWORD size  
);  
  
void Func3(_Out_writes_(size) PSTR pb,   
    DWORD size  
);  
  
```  
  
## \_Out\_ PSTR  
 O uso de `_Out_ PSTR` é quase sempre errado.  Isso é interpretado como o ter um parâmetro de saída que aponta para um caractere armazenam no buffer e tiver terminação.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Uma anotação como `_In_ PCSTR` é comum e útil.  Aponta para uma cadeia de caracteres de entrada que tem uma terminação NULL porque a pré\-requisito de `_In_` permite o reconhecimento de uma cadeia de caracteres com terminação nula.  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` diz que há um ponteiro `p` de entrada que aponta para um caractere.  Porém, na maioria dos casos, essa não é provável que a especificação que for pretendida.  Em vez disso, o que tem o objetivo é provável a especificação de uma matriz com terminação nula; para fazer isso, use `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Não ter a especificação adequada de término NULL é comum.  Use a versão apropriada de `STR` para substituir o tipo, conforme mostrado no exemplo a seguir.  
  
```cpp  
  
// Incorrect  
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
// Correct  
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
```  
  
## \_Out\_range\_  
 Se o parâmetro for um ponteiro e você deseja expressar o intervalo de valor do elemento que está apontado pelo ponteiro, use `_Deref_out_range_` em vez de `_Out_range_`.  No exemplo a seguir, o intervalo de \*pcbFilled é expresso, não pcbFilled.  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Out_range_(0, cbSize) DWORD *pcbFilled  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled   
);  
  
```  
  
 `_Deref_out_range_(0, cbSize)` não é necessário estritamente para algumas ferramentas como o pode ser inferido de `_Out_writes_to_(cbSize,*pcbFilled)`, mas é mostrado aqui para manter a integridade.  
  
## Contexto incorreto em \_When\_  
 Outro erro comum é usar a avaliação após o estado de pré\-requisitos.  No exemplo a seguir, `_Requires_lock_held_` é um pré\-requisito.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 A expressão `result` se refere a um valor após o estado que não está disponível no estado anterior.  
  
## RETIFIQUE em \_Success\_  
 Se a função tiver êxito quando o valor de retorno for diferente de zero, use `return != 0` como a condição com êxito em vez de `return == TRUE`.  Diferente de zero não significa necessariamente a equivalência ao valor real que o compilador fornece para `TRUE`.  O parâmetro a `_Success_` é uma expressão, além das seguintes expressões são avaliadas como equivalentes: `return != 0`, `return != false`, `return != FALSE`, e `return` sem parâmetros ou comparações.  
  
```cpp  
  
// Incorrect  
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
// Correct  
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
```  
  
## Variável de referência  
 Para uma variável de referência, a versão anterior de SAL usou o ponteiro indicado como o destino da anotação e solicitou a adição de `__deref` às anotações que anexaram a uma variável de referência.  Esta versão usa o próprio objeto e não requer `_Deref_`adicional.  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
```  
  
## Anotações em valores de retorno  
 O exemplo a seguir mostra anotações de um valor de problemas comuns de retorno.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 Neste exemplo, `_Out_opt_` informa que o ponteiro pode ser NULL como parte de pré\-requisitos.  No entanto, as condições anteriores não podem ser aplicadas ao valor de retorno.  Nesse caso, a anotação é `_Ret_maybenull_`correta.  
  
## Consulte também  
 [Usando anotações de SAL para reduzir defeitos de código do C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Noções básicas de SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)   
 [Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funções intrínsecas](../code-quality/intrinsic-functions.md)