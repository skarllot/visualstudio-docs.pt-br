---
title: Registrando o programa | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
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
ms.openlocfilehash: 1bc19623ac675252587b714de504022020b44ce2
ms.lasthandoff: 02/22/2017

---
# <a name="registering-the-program"></a>Registrando o programa
Depois que o mecanismo de depuração adquiriu uma porta, representado por um [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface, a próxima etapa para habilitar o programa a ser depurado é registrá-lo com a porta. Depois de registrado, o programa está disponível para depuração por um dos seguintes meios:  
  
-   O processo de anexação, que permite que o depurador obtivesse o controle de depuração completo de um aplicativo em execução.  
  
-   Just-in-time (JIT) depuração, que permite a depuração após o fato de um programa executado independentemente de um depurador. Quando a arquitetura de tempo de execução detecta uma falha, o depurador é notificado antes do sistema operacional ou do ambiente de execução libera a memória e os recursos do programa com falha.  
  
## <a name="registering-procedure"></a>Procedimento de registro  
  
#### <a name="to-register-your-program"></a>Para registrar o seu programa  
  
1.  Chamar o [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) método implementado pela porta.  
  
     `IDebugPortNotify2::AddProgramNode`requer um ponteiro para um [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface.  
  
     Normalmente, quando o sistema operacional ou o ambiente de tempo de execução carrega um programa, ele cria o nó do programa. Se o mecanismo de depuração (DE) é solicitado a carregar o programa o DE cria e registra o nó do programa.  
  
     O exemplo a seguir mostra o mecanismo de depuração, ative o programa e registrá-lo com uma porta.  
  
    > [!NOTE]
    >  Isso não é a única maneira de iniciar e reiniciar um processo; Isso é principalmente um exemplo de registro de um programa com uma porta.  
  
    ```cpp#  
    // This is an IDebugEngineLaunch2 method.  
    HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                          IDebugPort2 *pPort,  
                                          /* omitted parameters */,  
                                          IDebugProcess2**ppDebugProcess)  
    {  
        // do stuff here to set up for a launch (such as handling the other parameters)  
        ...  
  
        // Now get the IPortNotify2 interface so we can register a program node  
        // in CDebugEngine::ResumeProcess.  
        CComPtr<IDebugDefaultPort2> spDefaultPort;  
        HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
        if (SUCCEEDED(hr))  
        {  
            CComPtr<IDebugPortNotify2> spPortNotify;  
            hr = spDefaultPort->GetPortNotify(&spPortNotify);  
            if (SUCCEEDED(hr))  
            {  
                // Remember the port notify so we can use it in ResumeProcess.  
                m_spPortNotify = spPortNotify;  
  
                // Now launch the process in a suspended state and return the  
                // IDebugProcess2 interface  
                CComPtr<IDebugPortEx2> spPortEx;  
                hr = pPort->QueryInterface(&spPortEx);  
                if (SUCCEEDED(hr))  
                {  
                    // pass on the parameters we were given (omitted here)  
                    hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
                }  
            }  
        }  
        return(hr);  
    }  
  
    HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
    {  
        // Make a program node for this process  
        HRESULT hr;  
        CComPtr<IDebugProgramNode2> spProgramNode;  
        hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            hr = m_spPortNotify->AddProgramNode(spProgramNode);  
            if (SUCCEEDED(hr))  
            {  
                // resume execution of the process using the port given to us earlier.  
               // (Querying for the IDebugPortEx2 interface is valid here since  
               // that's how we got the IDebugPortNotify2 interface in the first place.)  
                CComPtr<IDebugPortEx2> spPortEx;  
                hr = m_spPortNotify->QueryInterface(&spPortEx);  
                if (SUCCEEDED(hr))  
                {  
                    hr  = spPortEx->ResumeProcess(pDebugProcess);  
                }  
            }  
        }  
        return(hr);  
    }  
  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Obtendo uma porta](../../extensibility/debugger/getting-a-port.md)   
 [Habilitar um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
