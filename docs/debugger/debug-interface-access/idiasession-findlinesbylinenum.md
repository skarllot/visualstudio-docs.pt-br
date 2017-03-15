---
title: "IDiaSession::findLinesByLinenum | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Método IDiaSession::findLinesByLinenum"
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findLinesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Determina os números de linha do compiland que o número da linha especificada em um arquivo de origem se encontra dentro ou próximo.  
  
## Sintaxe  
  
```cpp#  
HRESULT findLinesByLinenum (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parâmetros  
 `compiland`  
 \[in\] Um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) o objeto que representa o compiland da pesquisa para os números de linha.  Este parâmetro não pode ser `NULL`.  
  
 `file`  
 \[in\] Um [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) o objeto que representa o arquivo de origem para pesquisar em.  Este parâmetro não pode ser `NULL`.  
  
 `linenum`  
 \[in\] Especifica um número de linha de base um.  
  
> [!NOTE]
>  Não é possível usar o zero para especificar todas as linhas \(use o [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md) método para localizar todas as linhas\).  
  
 `column`  
 \[in\] Especifica o número da coluna.  Use o zero para especificar todas as colunas.  Uma coluna é um deslocamento de byte em uma linha.  
  
 `ppResult`  
 \[out\] Retorna um [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objta que contém uma lista dos números de linha recuperado.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Exemplo  
 O exemplo a seguir mostra como abrir um arquivo de origem, enumerar os compilandos contribuiu por este arquivo e localize os números de linha no arquivo de origem onde começa a cada compiland.  
  
```cpp#  
void ShowLinesInCompilands(IDiaSession *pSession, LPCOLESTR filename)  
{  
    IDiaEnumSourceFiles* pEnum;  
    IDiaSourceFile*      pFile;  
    DWORD                celt;  
  
    pSession->findFile ( NULL, filename, nsFNameExt, &pEnum );  
    while ( pEnum->Next ( 1, &pFile, &celt ) == S_OK ) // for each file  
    {  
        IDiaEnumSymbols* pEnumCompilands;  
        IDiaSymbol* pCompiland;  
  
        pFile->get_compilands ( &pEnumCompilands );  
        // for each compiland  
        while ( pEnumCompilands->Next ( 1, &pCompiland, &celt ) == S_OK )  
        {  
            IDiaEnumLineNumbers* pEnum;  
            // Find first compiland closest to line 1 of the file.  
            if (pSession->findLinesByLinenum( pCompiland, pFile, 1, 0, &pEnum ) == S_OK)  
            {  
                IDiaLineNumber *pLineNumber;  
                DWORD lineCount;  
                while ( pEnum->Next(1,&pLineNumber,&lineCount) == S_OK)  
                {  
                     DWORD lineNum;  
                     if (pLineNumber->get_line(&lineNum) == S_OK)  
                     {  
                          printf("compiland starts in source at line number = %lu\n",lineNum);  
                     }  
                }  
            }  
        }  
    }  
}  
```  
  
## Consulte também  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)