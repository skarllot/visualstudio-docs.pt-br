---
title: Avaliar locais | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f4c8b7d2e35f9e593e52c3a4cf704f9d0d1892a2
ms.lasthandoff: 02/22/2017

---
# <a name="evaluating-locals"></a>Avaliar locais
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) é chamado para obter o valor de um local, bem como o nome do local e o tipo. Como o valor do local é dependente do estado atual do programa, o valor do local deve ser obtido da memória. O [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) objeto é usado para ligar o [IDebugField](../../extensibility/debugger/reference/idebugfield.md) que representa o local para o local apropriado na memória que contém o valor do objeto. Este local na memória é representado por um [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto.  
  
 Essa funcionalidade de recuperar o valor do local é encapsulada em uma função auxiliar que realiza as seguintes tarefas:  
  
1.  Associa o `IDebugField` objeto na memória para obter um `IDebugObject` objeto.  
  
2.  Obtém o valor da memória. Esse valor é representado como uma série de bytes.  
  
3.  Formata o valor com base no tipo do local.  
  
4.  Retorna um objeto genérico que contém o valor do local. No c#, isso é uma `object`, e em C++, isso é um `VARIANT`.  
  
## <a name="managed-code"></a>Código gerenciado  
 Esta é uma implementação de uma função que recupera o valor de um local em código gerenciado.  
  
```c#  
namespace EEMC  
{  
    internal class Field  
    {  
        internal static object GetValue(  
            IDebugBinder binder,  
            IDebugField field,  
            Type t,  
            uint size)  
        {  
            if (t == null || size == 0)  return null;  
  
            IDebugObject debugObject = null;  
            binder.Bind(null, field, out debugObject);  
  
            byte[] buffer = new byte[size];  
            for (int i = 0; i < size; i++)  buffer[i] = 0;  
  
            debugObject.GetValue(buffer, size);   
  
            if (t == typeof(sbyte)) return (sbyte) buffer[0];  
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);  
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);  
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);  
            if (t == typeof(byte))  return buffer[0];  
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);  
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);  
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);  
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);  
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);  
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);  
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);  
            return null;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Código não gerenciado  
 Esta é uma implementação de uma função que recupera o valor de um local em código não gerenciado. `FieldGetType`é mostrado na [Obtendo valores locais](../../extensibility/debugger/getting-local-values.md).  
  
```cpp#  
HRESULT FieldGetPrimitiveValue(  
    in  IDebugBinder* pbinder,  
    in  IDebugField*  pfield,  
    out VARIANT*      pvarValue  
    )  
{  
    if (pvarValue == NULL)  
        return E_INVALIDARG;  
    else  
        *pvarValue = 0;  
  
    if (pfield == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    UINT          valueSize = 0;  
    BYTE*         pvalueBits = NULL;  
    IDebugObject* pobject    = NULL;  
  
    //get the value as bits  
    hr = pbinder->Bind( NULL, pfield, &pobject );  
    if (FAILED(hr))  
        return hr;  
  
    hr = pobject->GetSize( &valueSize );  
    if (FAILED(hr))  
    {  
        pobject->Release();  
        return hr;  
    }  
  
    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));  
    if (!pvalueBits)  
    {  
        pobject->Release();  
        return E_OUTOFMEMORY;  
    }  
  
    hr = pobject->GetValue( pvalueBits, valueSize );  
    pobject->Release();  
    if (FAILED(hr))  
    {  
        free(pvalueBits);  
        return hr;  
    }  
  
    //get the type  
    VARIANT     valueType;  
  
    hr = FieldGetType( pfield, &valueType );  
    if (FAILED(hr))  
    {  
        free(pvalueBits);  
        return hr;  
    }  
  
    //copy a primitive value  
    switch (valueType.vt)  
    {  
    case VT_BSTR:  
        {  
            pvarValue->vt = VT_BSTR;  
            if (valueSize == 0)  
                pvarValue->bstrVal = SysAllocString( OLE("") );  
            else  
                pvarValue->bstrVal =  
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),  
                                           valueSize );  
        }  
  
    case VT_BOOL:  
    case VT_I1:  
    case VT_I2:  
    case VT_I4:  
    case VT_I8:  
    case VT_UI1:  
    case VT_UI2:  
    case VT_UI4:  
    case VT_UI8:  
    case VT_R4:  
    case VT_R8:  
        pvarValue->vt = valueType.vt;  
  
        if (valueSize > 8)  
            valueSize = 8;  
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );  
        break;  
  
    case VT_VOID:  
    case VT_EMPTY:  
        pvarValue->vt = valueType.vt;  
        break;  
  
    default:  
        //not a primitive type  
        VariantClear(&valueType);  
        free(pvalueBits);  
        return E_FAIL;  
    }  
  
    free(pvalueBits);  
    VariantClear(&valueType);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Implementação de exemplo de locais](../../extensibility/debugger/sample-implementation-of-locals.md)   
 [Obtendo valores de Local](../../extensibility/debugger/getting-local-values.md)   
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md)
