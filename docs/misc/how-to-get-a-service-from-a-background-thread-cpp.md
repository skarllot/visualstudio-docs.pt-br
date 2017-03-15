---
title: "Como: obter um servi&#231;o de um Thread em segundo plano (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Multithreading, serviços"
ms.assetid: 97a56709-66d4-431a-ae63-392ee5898511
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Como: obter um servi&#231;o de um Thread em segundo plano (C++)
Serviços não podem ser obtidos por meio de `IServiceProvider.QueryService` de um segmento de plano de fundo.  Se você usar `QueryService` para obter um serviço no thread principal e, em seguida, tente usar o serviço em um segmento de plano de fundo, ele também irá falhar.  
  
 Para obter um serviço a partir de um thread de plano de fundo, use `CoMarshalInterThreadInterfaceInStream` na `IVsPackage.SetSite` método para empacotar o provedor de serviços em um fluxo no thread principal.  Em seguida, você pode desempacotar o provedor de serviços em um segmento de plano de fundo e usá\-lo para obter o serviço.  Você pode desempacotar apenas uma vez, portanto, a interface que você recebe de volta em cache.  
  
> [!NOTE]
>  Código gerenciado automaticamente empacota interfaces entre threads, portanto, obtendo um serviço de um segmento de plano de fundo não requer código especial.  
  
## Exemplo  
 O seguinte código empacota um provedor de serviços no thread principal e fornece um `QueryServiceFromBackgroundThread` método para desempacotar o provedor de serviços para obter um serviço de um thread de segundo plano.  
  
```  
class CMyPackage : public IVsPackage  
{  
private:  
    // Used to marshal IServiceProvider between threads  
    CComPtr< IStream > m_pSPStream;  
    // IServiceProvider proxy for the background thread  
    CComPtr< IServiceProvider > m_pBackgroundSP;  
  
public:  
    HRESULT SetSite( IServiceProvider* pSP )  
    {  
        // Marshal the service provider into a stream so that  
        // the background thread can retrieve it later  
        CoMarshalInterThreadInterfaceInStream(  
            IID_IServiceProvider, pSP, &m_pSPStream);  
  
        //... do the rest of your initialization  
    }  
  
    // Call this when your background thread needs to call QueryService  
    // The first time through, it unmarshals the interface stored   
    HRESULT QueryServiceFromBackgroundThread(  
        REFGUID rsid,        // [in] Service ID  
        REFIID riid,         // [in] Interface ID  
        // [out] Interface pointer of requested service (NULL on error)  
        void **ppvObj  
    {  
        if( !m_pBackgroundSP )  
        {  
            if( !m_pSPStream )  
            {  
                return E_UNEXPECTED;  
            }  
  
            HRESULT hr = CoGetInterfaceAndReleaseStream(   
                m_pSPStream, IID_IServiceProvider,   
                (void **)&m_pBackgroundSP );  
            if( FAILED(hr) )  
            {  
                return hr;  
            }  
  
            // The CoGetInterfaceAndReleaseStream has already   
            // destroyed the stream.  To avoid double-freeing,   
            // the smart wrapper needs to be detached.  
            m_pSPStream.Detach();  
        }  
  
        return m_pBackgroundSP->QueryService( rsid, riid, ppvObj );  
    }  
};  
```  
  
## Consulte também  
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)