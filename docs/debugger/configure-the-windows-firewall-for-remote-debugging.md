---
title: "Configurar o Firewall do Windows para a depura&#231;&#227;o remota | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configurar o Firewall do Windows para a depura&#231;&#227;o remota
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como configurar o firewall para permitir a depuração remota em computadores que executam os seguintes sistemas operacionais:  
  
-   Windows 7  
  
-   Windows 8\/8.1  
  
-   Windows 10  
  
-   Windows Server 2008 \(R2\)  
  
-   Windows Server 2012  
  
-   Windows Server 2012 R2  
  
 Se a rede na qual você está depurando não estiver protegida por um firewall, essa configuração é desnecessária. Caso contrário, o computador que hospeda o Visual Studio e o computador remoto a ser depurado requerem alterações à configuração do firewall.  
  
 **IPSec** se sua rede requer que a comunicação seja executada usando o IPSec, você deve abrir portas adicionais no computador host do Visual Studio e o computador remoto.  
  
 **Servidor web** se você estiver depurando um servidor remoto, você deve abrir uma porta adicional no computador remoto.  
  
 Observe que os dois computadores não precisa executar o mesmo sistema operacional. Por exemplo, o computador do Visual Studio pode executar Windows 10 e o computador remoto pode executar o Windows Server 2012 R2.  
  
## Para configurar o Firewall do Windows no computador do Visual Studio  
 As instruções para configurar o firewall do Windows ser ligeiramente diferem em diferentes sistemas operacionais. No Windows 7 ou Windows Server 2008, a palavra **programa** é usado; no Windows 8\/8.1, Windows 10 e o Windows Server 2012, a palavra **aplicativo** é usado.  Nas etapas a seguir, usaremos a palavra **aplicativo**.  
  
1.  Abra a página de Firewall do Windows. \(No **Iniciar** caixa Pesquisar do menu, digite **Firewall do Windows**\).  
  
2.  Clique em **permitem que um aplicativo ou recurso pelo Firewall do Windows**.  
  
3.  No **permitido aplicativos e recursos** lista, procure **Visual Studio Remote Debugger descoberta**. Se estiver listado, certifique\-se de que ela está selecionada e que um ou mais tipos de rede também são selecionados.  
  
4.  Se **Visual Studio Remote Debugger descoberta** não é listado, clique em **Permitir que outro aplicativo**. Se você ainda não estiver visível no **Adicionar um aplicativo** janela, clique em **Procurar** e navegue até **\\Common7\\IDE\\Remote \< diretório de instalação do Visual Studio \> depurador**. Localize a pasta apropriada para o aplicativo \(x86, x64, Appx\) e, em seguida, selecione **msvsmon.exe**. Em seguida, clique em **Add**.  
  
5.  No **permitido aplicativos e recursos** lista, selecione **Visual Studio Monitor de depuração remota**. Verificar um ou mais tipos de rede \(**domínio, Home\/Work \(privada\), público**\) que você deseja que o monitor de depuração remota para se comunicarem. Os tipos devem incluir a rede à qual o computador do Visual Studio está conectado.  
  
## Para abrir uma porta no computador do Visual Studio para habilitar a descoberta  
 Você deve permitir que a porta UDP 3702 entrada permitir a descoberta de computador \(es\) executando o depurador remoto. Para adicioná\-lo, consulte como configurar portas no Firewall.  
  
## Para configurar o firewall do Windows do computador remoto para depuração remota  
 Os componentes de depuração remotos podem ser instalados no computador remoto ou executar a partir de um diretório compartilhado. O firewall do computador remoto deve ser configurado em ambos os casos. Os componentes de depuração remotos estão localizados em:  
  
 **\< diretório de instalação do visual Studio \> \\Common7\\IDE\\Remote depurador**  
  
 As instruções para configurar o firewall do Windows ser ligeiramente diferem em diferentes sistemas operacionais. No Windows 7 ou Windows Server 2008, a palavra **programa** é usado; no Windows 8\/8.1, Windows 10 e o Windows Server 2012, a palavra **aplicativo** é usado.  Nas etapas a seguir, usaremos a palavra **aplicativo**.  
  
1.  Abra a página de Firewall do Windows. \(No **Iniciar** caixa Pesquisar do menu, digite **Firewall do Windows**.\)  
  
2.  Clique em **permitem que um aplicativo ou recurso pelo Firewall do Windows**.  
  
3.  No **permitido aplicativos e recursos** lista, procure **Visual Studio Monitor de depuração remota**. Se estiver listado, certifique\-se de que ela está selecionada e que um ou mais tipos de rede também são selecionados.  
  
4.  Se **Visual Studio Monitor de depuração remota** não é listado, clique em **Permitir que outro aplicativo**. Se você ainda não estiver visível no **Adicionar uma janela de aplicativo**, clique em **Procurar** e navegue até **\\Common7\\IDE\\Remote \< diretório de instalação do Visual Studio \> depurador**. Localize a pasta apropriada para o aplicativo \(x86, x64, Appx\) e, em seguida, selecione **msvsmon.exe**. Em seguida, clique em **Add**.  
  
5.  No **permitido aplicativos** lista, selecione **Visual Studio Monitor de depuração remota**. Verificar um ou mais tipos de rede \(**domínio, Home\/Work \(privada\), público**\) que você deseja que o monitor de depuração remota para se comunicarem. Os tipos devem incluir a rede à qual o computador do Visual Studio está conectado.  
  
## Portas que habilitar a depuração remota no computador remoto  
  
|||||  
|-|-|-|-|  
|**Portas**|**Entrada\/saída**|**Protocol**|**Descrição**|  
|3702|Saída|UDP|Necessário para a detecção do depurador remoto.|  
|4020||TCP|Para VS 2015. O número da porta é incrementado por 2 para cada versão do Visual Studio. Para obter mais informações, consulte Visual Studio Remote Debugger atribuições de porta.|  
|4021||TCP|Para VS 2015. O número da porta é incrementado por 2 para cada versão do Visual Studio. Para obter mais informações, consulte Visual Studio Remote Debugger atribuições de porta.|  
  
## Portas no computador remoto que habilitar a depuração remota com o modo de compatibilidade gerenciado ou nativo  
  
|||||  
|-|-|-|-|  
|**Portas**|**Entrada\/saída**|**Protocol**|**Descrição**|  
|135, 139, 445|Saída|TCP|Obrigatório.|  
|137, 138|Saída|UDP|Obrigatório.|  
|500, 4500|Saída|UDP|Necessário se a diretiva de domínio requer comunicação de rede a ser executada por meio de IPSec.|  
|80|Saída|TCP|Necessário para depuração de servidor Web.|  
  
## Como configurar portas no Firewall do Windows  
  
1.  Sobre o **Iniciar** menu, procure **Firewall do Windows com segurança avançada**.  
  
2.  Clique em **regras de entrada** ou **as regras de saída** e, em seguida, clique em **nova regra** no **ações** lista.  
  
3.  Sobre o **tipo de regra** página, selecione **porta** e, em seguida, clique em **próximo**.  
  
4.  Sobre o **protocolo e portas** selecione a protocolo de porta \(TCP ou UDP\). Selecione **portas locais específicas** e digite um ou mais números de porta que você deseja habilitar para o protocolo. Números separados por vírgulas. Em seguida, clique em **próximo**.  
  
5.  Sobre o **ação** página, selecione **Permitir a conexão** e, em seguida, clique em **próximo**.  
  
6.  Sobre o **perfil** selecione um ou mais tipos de rede para habilitar para a porta. O tipo que você selecionar deve incluir a rede à qual o computador remoto está conectado. Em seguida, clique em **próximo**.  
  
7.  Sobre o **nome** página, digite um nome para a regra e, em seguida, clique em **Concluir**.  
  
8.  Você deve ver a nova regra no **regras de entrada** ou **as regras de saída** lista.  
  
## Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)