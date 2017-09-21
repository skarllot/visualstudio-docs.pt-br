---
title: Obtendo uma porta | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
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
ms.openlocfilehash: bb897eee4f95a1e96a8659c75850df3b62ab1a22
ms.lasthandoff: 02/22/2017

---
# <a name="getting-a-port"></a>Obtendo uma porta
Uma porta representa uma conexão a uma máquina que processos estão em execução. Essa máquina pode ser o computador local ou em um computador remoto (que possivelmente pode estar executando um sistema operacional não baseado em Windows, consulte [portas](../../extensibility/debugger/ports.md) para obter mais informações).  
  
 Uma porta é representada pelo [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface. Ele é usado para obter informações sobre processos em execução na máquina em que a porta está conectada ao.  
  
 Um mecanismo de depuração precisa acessar uma porta para registrar nós do programa com a porta e para atender a solicitações de informações do processo. Por exemplo, se o mecanismo de depuração implementa o [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) de interface, a implementação para o [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) método pode pedir que a porta para as informações de processo necessárias a serem retornados.  
  
 O Visual Studio fornece a porta necessária para o mecanismo de depuração e obtém essa porta de um fornecedor de porta. Se um programa estiver anexado a (ou no depurador devido a uma exceção foi lançada, que dispara a caixa de diálogo Just-in-Time [JIT]), o usuário terá a opção de transporte (outro nome para um fornecedor de porta) usar. Caso contrário, se o usuário inicia o programa a partir do depurador, o sistema do projeto Especifica o fornecedor de porta para usar. Em ambos os casos, o Visual Studio cria uma instância do fornecedor de porta, representado por um [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) de interface e solicita uma nova porta chamando [adicionar porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) com um [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interface. Em seguida, essa porta é passada para o mecanismo de depuração de uma forma ou de outra.  
  
## <a name="example"></a>Exemplo  
 Este fragmento de código mostra como usar a porta fornecida ao [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para registrar um nó de programa em [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parâmetros não diretamente relacionados a esse conceito foram omitidos por motivos de clareza.  
  
> [!NOTE]
>  Este exemplo usa a porta para iniciar e retomar o processo e supõe que o [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interface é implementada na porta. Isso não é a única maneira de realizar essas tarefas, e é possível que a porta não pode até mesmo ser envolvida diferente do que o programa [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) atribuído a ele.  
  
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
 [Registrando o programa](../../extensibility/debugger/registering-the-program.md)   
 [Habilitar um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Fornecedores de porta](../../extensibility/debugger/port-suppliers.md)   
 [Portas](../../extensibility/debugger/ports.md)
