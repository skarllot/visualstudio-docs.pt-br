---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
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
  - "Método IDiaSymbol::get_undecoratedNameEx"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera parte ou todo um nome não decorado para um C\+\+ decorados nome \(ligação\).  
  
## Sintaxe  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### Parâmetros  
 `undecoratedOptions`  
 \[in\] Especifica uma combinação de sinalizadores que controlam o que é retornado.  Consulte a seção de comentários para os valores específicos e o que fazer.  
  
 `pRetVal`  
 \[out\] Retorna que o nome não decorado para um C\+\+ decorada nome.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
 O `undecorateOptions` pode ser uma combinação dos sinalizadores a seguir.  
  
> [!NOTE]
>  Os nomes de sinalizador não estão definidos no SDK do DIA, portanto, você precisa adicionar as declarações ao seu código ou usar os valores brutos.  
  
|Sinalizador|Valor|Descrição|  
|-----------------|-----------|---------------|  
|UNDNAME\_COMPLETE|0x0000|Permite total undecoration.|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|Remove sublinhados provenientes da Microsoft estendido palavras\-chave.|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|Desativa a expansão da Microsoft extended palavras\-chave.|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|Desativa a expansão de tipo de retorno para a declaração principal.|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|Desativa a expansão do modelo de declaração.|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|Desativa a expansão do especificador de linguagem de declaração.|  
|UNDNAME\_RESERVED1|0x0020|RESERVADO.|  
|UNDNAME\_RESERVED2|0x0040|RESERVADO.|  
|UNDNAME\_NO\_THISTYPE|0x0060|Desabilita todos os modificadores na `this` tipo.|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|Desativa a expansão dos especificadores de acesso para os membros.|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|Desativa a expansão da "throw\-assinaturas" para funções e ponteiros para funções.|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|Desativa a expansão da `static` ou `virtual` membros.|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|Desativa a expansão do modelo Microsoft para UDT retorna.|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|Undecorates nomes decorados de 32 bits.|  
|UNDNAME\_NAME\_ONLY|0x1000|Obtém somente o nome para a declaração principal; Retorna apenas \[escopo::\] nome.  Expande o modelo params.|  
|UNDNAME\_TYPE\_ONLY|0x2000|A entrada é apenas um tipo de codificação; compõe um Declarador abstrata.|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|Os parâmetros do modelo real estão disponíveis.|  
|UNDNAME\_NO\_ECSU|0x8000|Suprime o enum\/classe\/struct\/união.|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|Suprime a verificação de caracteres de identificador válido.|  
|UNDNAME\_NO\_PTR64|0x20000|Não inclui ptr64 na saída.|  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)