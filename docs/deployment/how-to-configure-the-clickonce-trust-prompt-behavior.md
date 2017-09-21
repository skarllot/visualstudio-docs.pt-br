---
title: "Como configurar o comportamento do prompt confi&#225;vel do ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Aplicativos ClickOnce, instalar sem avisar"
  - "Aplicativos ClickOnce, prompt confiável"
  - "implantação ClickOnce, instalar sem avisar"
  - "implantação ClickOnce, prompt confiável"
  - "implantando aplicativos [ClickOnce], prompt confiável"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como configurar o comportamento do prompt confi&#225;vel do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode configurar o prompt de confiança de ClickOnce para o controle se os usuários finais recebem a opção de instalar aplicativos de ClickOnce, tais como Windows Forms applications, Windows Presentation Foundation de aplicativos, aplicativos de console, aplicativos de navegador do WPF e soluções do Office.  Você pode configurar o prompt de confiança, definindo as chaves do registro no computador de cada usuário final.  
  
 A tabela a seguir mostra as opções de configuração que podem ser aplicadas a cada uma das cinco zonas \(Internet, UntrustedSites, meu computador, LocalIntranet e TrustedSites\).  
  
|Opção|Valor de configuração do registro|Descrição|  
|-----------|---------------------------------------|---------------|  
|Ative o prompt de confiança.|`Enabled`|A solicitação de confiança de ClickOnce é a exibição para que os usuários finais possam conceder confiança aos aplicativos de ClickOnce.|  
|Restringir o prompt de confiança.|`AuthenticodeRequired`|O prompt de confiança ClickOnce só será exibido se ClickOnce aplicativos são assinados com um certificado que identifica o Editor.|  
|Desative o prompt de confiança.|`Disabled`|O prompt de confiança de ClickOnce não é exibido para quaisquer aplicativos de ClickOnce que não são assinados com um certificado explicitamente confiável.|  
  
 A tabela a seguir mostra o comportamento padrão para cada zona.  A coluna de aplicativos se refere a aplicativos Windows Forms, aplicativos de Windows Presentation Foundation, os aplicativos WPF de navegador e aplicativos de console.  
  
|Zona|Aplicativos|Soluções do Office|  
|----------|-----------------|------------------------|  
|`Meu computador`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Você pode substituir essas configurações, habilitando, restringindo ou desativando o prompt de confiança de ClickOnce.  
  
## Ativando o Prompt de confiança de ClickOnce  
 Habilite o prompt de confiança para uma zona quando desejar que os usuários finais devem ser apresentados com a opção de instalação e execução de qualquer aplicativo de ClickOnce que vem da zona.  
  
#### Para habilitar o prompt de confiança de ClickOnce, usando o editor do registro  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **Start**, e em seguida clique **Run**.  
  
    2.  No  **Abrir** , digite  `regedit32`e, em seguida, clique em  **OK**.  
  
2.  Localize a seguinte chave do registro:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Se a chave não existir, crie\-o.  
  
3.  Adicione as seguintes subchaves como  **O valor de seqüência de caracteres**, se eles ainda não existir, com os valores associados, mostrados na tabela a seguir.  
  
    |Subchave de valor de seqüência de caracteres|Valor|  
    |--------------------------------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`Meu computador`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Para soluções do Office,  `Internet` tem o valor padrão  `AuthenticodeRequired` e  `UntrustedSites` possui o valor  `desativado`.  Para todos os outros,  `Internet` tem o valor padrão  `Enabled`.  
  
#### Para habilitar o prompt de confiança ClickOnce programaticamente  
  
1.  Crie um aplicativo de console de Visual Basic ou C\# Visual em Visual Studio.  
  
2.  Abra o arquivo Program. vb ou Program. cs para edição e adicione o seguinte código.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Compile e execute o aplicativo.  
  
## Restringindo o Prompt de confiança de ClickOnce  
 Restringir o prompt de confiança para que as soluções devem ser assinadas com certificados Authenticode conhecidos identidade antes dos usuários são solicitados para uma decisão de confiança.  
  
#### Para restringir o prompt de confiança de ClickOnce usando o editor do registro  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **Start**, e em seguida clique **Run**.  
  
    2.  No  **Abrir** , digite  `regedit`e, em seguida, clique em  **OK**.  
  
2.  Localize a seguinte chave do registro:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Se a chave não existir, crie\-o.  
  
3.  Adicione as seguintes subchaves como  **O valor de seqüência de caracteres**, se eles ainda não existir, com os valores associados, mostrados na tabela a seguir.  
  
    |Subchave de valor de seqüência de caracteres|Valor|  
    |--------------------------------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`Meu computador`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### Para restringir o prompt de confiança ClickOnce programaticamente  
  
1.  Crie um aplicativo de console de Visual Basic ou C\# Visual em Visual Studio.  
  
2.  Abra o arquivo Program. vb ou Program. cs para edição e adicione o seguinte código.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Compile e execute o aplicativo.  
  
## Desativando o Prompt de confiança de ClickOnce  
 Você pode desativar o prompt de confiança para que os usuários finais não terá a opção para instalar soluções que já não são confiáveis em sua diretiva de segurança.  
  
#### Para desativar o prompt de confiança de ClickOnce usando o editor do registro  
  
1.  Abra o editor do registro:  
  
    1.  Clique em **Start**, e em seguida clique **Run**.  
  
    2.  No  **Abrir** , digite  `regedit`e, em seguida, clique em  **OK**.  
  
2.  Localize a seguinte chave do registro:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Se a chave não existir, crie\-o.  
  
3.  Adicione as seguintes subchaves como  **O valor de seqüência de caracteres**, se eles ainda não existir, com os valores associados, mostrados na tabela a seguir.  
  
    |Subchave de valor de seqüência de caracteres|Valor|  
    |--------------------------------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`Meu computador`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### Para desativar o prompt de confiança de ClickOnce programaticamente  
  
1.  Crie um aplicativo de console de Visual Basic ou C\# Visual em Visual Studio.  
  
2.  Abra o arquivo Program. vb ou Program. cs para edição e adicione o seguinte código.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Compile e execute o aplicativo.  
  
## Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Como depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Como adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Como assinar manifestos de aplicativo e implantação novamente](../deployment/how-to-re-sign-application-and-deployment-manifests.md)