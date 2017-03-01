---
title: Registrando um personalizado Debug Engine | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
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
ms.openlocfilehash: acb2f05283814228ec9b0e6439e9989b06aba196
ms.lasthandoff: 02/22/2017

---
# <a name="registering-a-custom-debug-engine"></a>Registrando um mecanismo de depuração personalizado
O mecanismo de depuração deve se registrar como uma fábrica de classes a seguir as convenções de COM, bem como registrar com o Visual Studio por meio da subchave do registro do Visual Studio.  
  
> [!NOTE]
>  Um exemplo de como registrar um mecanismo de depuração pode ser encontrado no exemplo TextInterpreter, que é criado como parte do [Tutorial: Criando um Debug Engine usando COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processo do servidor de DLL  
 Normalmente, um mecanismo de depuração é implementado em sua própria DLL como um servidor COM. Isso significa que o mecanismo de depuração deve registrar o CLSID de sua fábrica de classes com para que Visual Studio pode acessá-lo. Em seguida, o mecanismo de depuração deve ser registrado com o próprio Visual Studio para estabelecer as propriedades (conhecido também como métricas) a depuração mecanismo oferece suporte. A opção de métricas que são gravadas para a subchave de registro do Visual Studio para o mecanismo de depuração depende dos recursos que suporta o mecanismo de depuração.  
  
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descreve não apenas os locais de registro necessários para registrar um mecanismo de depuração; ele também descreve a biblioteca dbgmetric.lib, que contém um número de funções úteis e declarações para os desenvolvedores de C++ que tornam manipulando o registro mais fácil.  
  
### <a name="example"></a>Exemplo  
 A seguir está um exemplo típico (do exemplo TextInterpreter) mostrando como usar o `SetMetric` de função (de dbgmetric.lib), para registrar um mecanismo de depuração com o Visual Studio. As métricas que está sendo passadas também são definidas no dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter é um mecanismo de depuração básica; ele não implementa — e, portanto, não registrar — todos os outros recursos. Um mecanismo de depuração mais completo teria uma lista completa de `SetMetric` chamadas ou seus equivalentes, uma para cada recurso, o mecanismo de depuração oferece suporte.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Auxiliares do SDK para depuração](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Criando um mecanismo de depuração usando COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)
