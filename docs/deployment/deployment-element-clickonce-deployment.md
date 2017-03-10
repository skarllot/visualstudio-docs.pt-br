---
title: "Elemento &lt;deployment&gt; (implanta&#231;&#227;o do ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#subscription"
  - "urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup"
  - "urn:schemas-microsoft-com:asm.v2#deploymentProvider"
  - "urn:schemas-microsoft-com:asm.v2#update"
  - "urn:schemas-microsoft-com:asm.v2#deployment"
  - "urn:schemas-microsoft-com:asm.v2#expiration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <deployment> (manifesto da implantação do ClickOnce)"
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;deployment&gt; (implanta&#231;&#227;o do ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifica os atributos usados para a implantação de atualizações e exposição ao sistema.  
  
## Sintaxe  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## Elementos e atributos  
 O `deployment` elemento é obrigatório e está sendo o `urn:schemas-microsoft-com:asm.v1` espaço para nome.  O elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`install`|Obrigatório.  Especifica se este aplicativo define uma presença no Windows  **Iniciar** menu e, no painel de controle  **Adicionar ou remover programas** aplicativo.  Os valores válidos são  `true` e  `false`.  Se  `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sempre será executado a versão mais recente deste aplicativo da rede e não reconhecerá a `subscription` elemento.|  
|`minimumRequiredVersion`|Opcional.  Especifica a versão mínima deste aplicativo que pode ser executado no cliente.  Se o número da versão do aplicativo for menor que o número de versão fornecido no manifesto de implantação, o aplicativo não será executado.  Números de versão devem ser especificados no formato  `n.n.n. n`, onde  `n` é um inteiro não assinado.  Se a `install` atributo é  `false`, `minimumRequiredVersion` não deve ser definido.|  
|`mapFileExtensions`|Opcional.  O padrão  `false`.  Se  `true`, todos os arquivos na implantação devem ter uma extensão. Deploy.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]irá remover esta extensão esses arquivos, assim que ele baixa essas atualizações do servidor Web.  Se você publicar seu aplicativo usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], adiciona automaticamente essa extensão a todos os arquivos.  Este parâmetro permite que todos os arquivos dentro de um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a implantação seja baixado de um servidor Web que bloqueia a transmissão de arquivos que terminam em "não seguras" extensões como. exe.|  
|`disallowUrlActivation`|Opcional.  O padrão  `false`.  Se  `true`, impede que um aplicativo instalado que está sendo iniciado clicando no URL ou digitando a URL no Internet Explorer.  Se a `install` atributo não estiver presente, esse atributo é ignorado.|  
|`trustURLParameters`|Opcional.  O padrão  `false`.  Se  `true`, permite que a URL conter os parâmetros de seqüência de caracteres de consulta que são passados para o aplicativo, bem como argumentos de linha de comando são passados para um aplicativo de linha de comando.  Para obter mais informações, consulte [Como recuperar informações de cadeia de caracteres de consulta em um aplicativo ClickOnce online](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md).<br /><br /> Se a `disallowUrlActivation` atributo é  `true`, `trustUrlParameters` deve ser excluído do manifesto, ou explicitamente definido como  `false`.|  
  
 O `deployment` elemento também contém os seguintes elementos filho.  
  
## assinatura  
 Opcional.  Contém o `update` elemento.  O `subscription` elemento não tem nenhum atributo.  Se a `subscription` elemento não existir, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo nunca irá procurar por atualizações disponíveis.  Se a `install` atributo da `deployment` elemento é  `false`, o `subscription` elemento é ignorado, pois um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é iniciado a partir da rede sempre usa a versão mais recente.  
  
## atualizar  
 Obrigatório.  Este elemento é filho da `subscription` elemento e contenha o `beforeApplicationStartup` ou o `expiration` elemento.  `beforeApplicationStartup`e `expiration` não pode ser especificados no manifesto de implantação do mesmo.  
  
 O `update` elemento não tem nenhum atributo.  
  
## beforeApplicationStartup  
 Opcional.  Este elemento é filho de `update` elemento e sem atributos.  Quando o `beforeApplicationStartup` elemento existe, o aplicativo será bloqueado quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verifica se há atualizações, se o cliente estiver on\-line.  Se esse elemento não existir, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] primeiro fará uma busca de atualizações de acordo com os valores especificados para o `expiration` elemento.  `beforeApplicationStartup`e `expiration` não pode ser especificados no manifesto de implantação do mesmo.  
  
## expiração  
 Opcional.  Este elemento é filho de `update` elemento, e não tem filhos.  `beforeApplicationStartup`e `expiration` não pode ser especificados no manifesto de implantação do mesmo.  Quando a verificação de atualização ocorre e uma versão atualizada é detectada, a nova versão armazena em cache enquanto a versão existente é executado.  A nova versão, em seguida, instala no lançamento da próximo a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
 O `expiration` elemento suporta os seguintes atributos.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`maximumAge`|Obrigatório.  Identifica a antiga como a atualização atual deve se tornar antes que o aplicativo executa uma verificação de atualização.  A unidade de tempo é determinada pelo `unit` atributo.|  
|`unit`|Obrigatório.  Identifica a unidade de tempo para `maximumAge`.  Unidades válidas são  `horas`,  `dias`, e  `semanas`.|  
  
## deploymentProvider  
 Para o.NET Framework 2.0, esse elemento é necessário se o manifesto de implantação contém um `subscription` seção.  Para o.NET Framework 3.5 e posterior, esse elemento é opcional e o padrão será o servidor e caminho do arquivo no qual o manifesto de implantação foi descoberto.  
  
 Este elemento é filho de `deployment` elemento e tem o atributo a seguir.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`codebase`|Obrigatório.  Identifica o local, como um identificador de URI \(Uniform Resource\), de que o manifesto de implantação é usado para atualizar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  Esse elemento também permite o encaminhamento de locais de atualização para instalações baseadas em CD.  Deve ser um URI válido.|  
  
## Comentários  
 Você pode configurar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] procurar atualizações após a inicialização do aplicativo para verificar se há atualizações na inicialização, ou nunca verificar atualizações.  Para verificar se há atualizações na inicialização, certifique\-se que o `beforeApplicationStartup` elemento existe sob o `update` elemento.  Para verificar se há atualizações após a inicialização, certifique\-se que o `expiration` elemento existe sob o `update` elemento e que os intervalos de atualização são fornecidos.  
  
 Para desabilitar a verificação de atualizações, remova o `subscription` elemento.  Quando você especifica no manifesto de implantação para nunca verificar se há atualizações, você pode ainda verificar as atualizações manualmente, usando o <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> método.  
  
 Para obter mais informações sobre como o deploymentProvider está relacionado a atualizações, consulte [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## Exemplos  
 O exemplo de código a seguir ilustra uma `deployment` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação.  O exemplo usa um `deploymentProvider` elemento para indicar o local preferido de atualização.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)