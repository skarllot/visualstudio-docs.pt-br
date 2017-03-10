---
title: "Problemas de configura&#231;&#227;o de servidor e cliente em implanta&#231;&#245;es do ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "implantação ClickOnce, solucionando problemas"
  - "implantando aplicativos, ClickOnce"
  - "solucionando problemas de implantações ClickOnce"
  - "Aplicativos do Windows, implantações ClickOnce"
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Problemas de configura&#231;&#227;o de servidor e cliente em implanta&#231;&#245;es do ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você usar o Internet Information Services \(IIS\) no Windows Server e sua implantação contém um tipo de arquivo que o Windows não reconhece, como, por exemplo, um arquivo do Microsoft Word, o IIS recusará transmitir o arquivo e sua implantação não terá êxito.  
  
 Além disso, alguns servidores Web e Web, como o software de aplicativo, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contém uma lista de arquivos e tipos de arquivos que você não pode fazer o download.  Por exemplo, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] impede o download de todos os arquivos Web. config.  Esses arquivos podem conter informações confidenciais, como nomes de usuário e senhas.  
  
 Embora essa restrição não deve causar problemas para fazer o download de núcleo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos como, por exemplo, manifestos e assemblies, essa restrição pode impedi\-lo de fazer o download de arquivos de dados incluídos como parte da sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  Na [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], você pode resolver esse erro, removendo o manipulador que proíbe o download desses arquivos do Gerenciador de configuração do IIS.  Consulte a documentação do servidor IIS para obter detalhes adicionais.  
  
 Alguns servidores Web podem bloquear arquivos com extensões como. dll,. config e. mdf.  Normalmente, aplicativos baseados em Windows incluem arquivos com algumas dessas extensões.  Se um usuário tenta executar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o aplicativo que acessa um arquivo bloqueado em um servidor Web, ocorrerá um erro.  Em vez de desbloquear todas as extensões de arquivo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publica cada arquivo de aplicativo com uma extensão de arquivo ". Deploy" por padrão.  Portanto, o administrador só precisa configurar o servidor Web para desbloquear as seguintes extensões de arquivo de três:  
  
-   .application  
  
-   .manifest  
  
-   .deploy  
  
 No entanto, você pode desativar essa opção desmarcando a  **extensão de arquivo ". Deploy" uso** de opção na [Publish Options Dialog Box](http://msdn.microsoft.com/pt-br/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), caso em que você deve configurar o servidor Web para desbloquear todas as extensões de arquivo usadas no aplicativo.  
  
 Você terá que configurar. manifest e. Application. Deploy, por exemplo, se você estiver usando o IIS em que você não tiver instalado o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ou se você estiver usando outro servidor Web \(por exemplo, Apache\).  
  
## Secure Sockets Layer \(SSL\) e ClickOnce  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo funcionará bem com SSL, exceto quando o Internet Explorer gera uma solicitação sobre o certificado SSL.  O prompt pode ser elevado quando há algo errado com o certificado, como, por exemplo, quando os nomes dos sites não coincidem ou o certificado expirou.  Para fazer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] trabalhar em uma conexão SSL, certifique\-se de que o certificado está atualizado e se os dados do certificado coincide com os dados do site.  
  
## Autenticação de Proxy e ClickOnce  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Fornece suporte para autenticação integrada do Windows de proxy a partir de.NET Framework 3.5.  Sem diretivas específicas de Machine. config são necessárias.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]não oferece suporte para outros protocolos de autenticação como, por exemplo, básica ou Digest.  
  
 Você também pode aplicar um hotfix para.NET Framework 2.0 para ativar esse recurso.  Para obter mais informações, consulte http:\/\/go.microsoft.com\/fwlink\/?LinkId\=158730  
  
 Para obter mais informações, consulte [Elemento \<defaultProxy\> \(configurações de rede\)](../Topic/%3CdefaultProxy%3E%20Element%20\(Network%20Settings\).md).  
  
## ClickOnce e a compatibilidade do navegador da Web  
 Atualmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] as instalações serão iniciada apenas se a URL para o manifesto de implantação é aberta usando o Internet Explorer.  Uma implantação cuja URL é iniciado a partir de outro aplicativo, como, por exemplo, de Microsoft Office Outlook, será iniciado com êxito somente se o Internet Explorer está definido como o navegador da Web padrão.  
  
> [!NOTE]
>  Mozilla Firefox é suportado se o provedor de implantação não estiver em branco ou o Microsoft.Extensão de Assistente do NET Framework é instalado.  Esta extensão é empacotada com.NET Framework 3.5 SP1.  Para obter suporte XBAP, o plug\-in do NPWPF é ativado quando necessário.  
  
## Ativar aplicativos de ClickOnce por meio de scripts do navegador  
 Se você tiver desenvolvido uma página da Web personalizada que inicia uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo usando os scripts ativos, você pode achar que o aplicativo não será iniciado em algumas máquinas.  Internet Explorer contém uma configuração chamada  **Aviso automático para o arquivo downloads**, que afeta esse comportamento.  Esta configuração está disponível no  **Security** guia no seu  **Opções** menu afeta esse comportamento.  Ele é chamado de  **Aviso automático para o arquivo downloads**, e ele é listado sob o  **Downloads** categoria.  A propriedade é definida como  **Habilitar** por padrão para páginas da Web de intranet e  **Desativar** por padrão para páginas da Web da Internet.  Quando essa configuração está definida como  **Desativar**, qualquer tentativa de ativar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo programaticamente \(por exemplo, atribuindo sua URL para o `document.location` propriedade\) serão bloqueados.  Nestas circunstâncias, os usuários podem iniciar aplicativos somente por meio de um download iniciado pelo usuário, por exemplo, clicando em um hiperlink, definido a URL do aplicativo.  
  
## Problemas de configuração de servidor adicionais  
  
##### Permissões de administrador necessárias  
 Você deve ter permissões de administrador no servidor de destino, se você estiver publicando com HTTP.  O IIS exige esse nível de permissões.  Se você não estiver publicando usando HTTP, você só precisa de permissão de gravação no caminho de destino.  
  
##### Problemas de autenticação de servidor  
 Quando você publica um servidor remoto que possui o "Acesso anônimo" desativado, você receberá o seguinte aviso:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  Você pode fazer com que a autenticação NTLM \(NT desafio\-resposta\) funcionam se o site solicita credenciais diferente de suas credenciais padrão e, na caixa de diálogo segurança, clique em  **OK** quando for solicitado se deseja salvar as credenciais fornecidas em sessões futuras.  No entanto, essa solução alternativa não funcionará para autenticação básica.  
  
## Usando servidores de Web de terceiros  
 Se você estiver implantando um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo de um servidor Web diferente do IIS, você pode enfrentar um problema se o servidor estiver retornando o tipo de conteúdo incorreto para a chave [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos, como, por exemplo, o manifesto de implantação e o manifesto do aplicativo.  Para resolver esse problema, consulte a Ajuda do seu servidor Web documentação sobre como adicionar novos tipos de conteúdo para o servidor e certifique\-se de que todos os arquivo extensão mapeamentos de nomes listados na tabela a seguir estão em vigor.  
  
|Extensão de nome de arquivo|Tipo de conteúdo|  
|---------------------------------|----------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## ClickOnce e unidades mapeadas  
 Se você usar Visual Studio para publicar um aplicativo de ClickOnce, você não pode especificar uma unidade mapeada como o local de instalação.  No entanto, você pode modificar o aplicativo ClickOnce para instalar a partir de uma unidade mapeada usando o gerador de manifesto e o Editor \(Mage e MageUI.exe\).  Para obter mais informações, consulte [Mage.exe \(Ferramenta de Geração e Edição de Manifesto\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) e [MageUI.exe \(Ferramenta de Geração e Edição de Manifesto, cliente gráfico\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  
  
## Protocolo FTP não tem suporte para a instalação de aplicativos  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]oferece suporte à instalação de aplicativos em qualquer servidor da Web HTTP 1.1 ou o servidor de arquivos.  Não há suporte para FTP, File Transfer Protocol, para instalar aplicativos.  Você pode usar o FTP para publicar apenas os aplicativos.  A tabela a seguir resume essas diferenças:  
  
|Tipo de URL|Descrição|  
|-----------------|---------------|  
|FTP: \/ \/|Você pode publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo usando esse protocolo.|  
|http:\/\/|Você pode instalar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo usando esse protocolo.|  
|https:\/\/|Você pode instalar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo usando esse protocolo.|  
|File:\/\/|Você pode instalar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo usando esse protocolo.|  
  
## XP SP2 do Windows: O Firewall do Windows  
 Por padrão, o Windows XP SP2 permite que o Firewall do Windows.  Se você estiver desenvolvendo sua aplicação em um computador com Windows XP instalado, são ainda poderão publicar e executar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos do servidor local que está executando o IIS.  No entanto, é possível acessar o servidor que está executando o IIS em outro computador, a menos que você abre o Firewall do Windows.  Consulte a Ajuda do Windows para obter instruções sobre como gerenciar o Firewall do Windows.  
  
## Windows Server: Ativar extensões de servidor do FrontPage  
 Extensões de servidor do FrontPage da Microsoft é necessária para publicação de aplicativos em um servidor de Web do Windows que usa o HTTP.  
  
 Por padrão, o Windows Server não tem as extensões de servidor do FrontPage instaladas.  Se você quiser usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para publicar em um servidor Web do Windows Server que usa HTTP com extensões de servidor do FrontPage, você deve instalar primeiro as extensões de servidor do FrontPage.  Você pode executar a instalação usando a ferramenta de administração de gerenciar o servidor no Windows Server.  
  
## Windows Server: Tipos de conteúdo bloqueada  
 IIS no [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] bloqueios para baixo de todos os tipos de arquivo, exceto para determinados tipos de conteúdo conhecidos \(por exemplo,. htm,. HTML,. txt e assim por diante\).  Para permitir a implantação de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usando este servidor de aplicativos, você precisa alterar as configurações do IIS para permitir o download de arquivos do tipo Application. manifest e outros tipos de arquivo personalizado usados pelo seu aplicativo.  
  
 Se você implantar usando um servidor IIS, execute o inetmgr. exe e adicionar novos tipos de arquivo da página da Web padrão:  
  
-   Para as extensões de Application e. manifest, o tipo MIME deve ser "application\/x\-ms\-application." Para outros tipos de arquivo, o tipo MIME deve ser "application\/octet\-stream".  
  
-   Se você criar um tipo de MIME com extensão "\*" e o tipo MIME "application\/octet\-stream", ele permitirá que arquivos do tipo de arquivo desbloqueado para serem baixadas.  \(No entanto, bloqueados arquivo não podem ser baixados tipos como. aspx e. asmx\).  
  
 Para obter instruções específicas sobre como configurar os tipos de MIME no Windows Server, consulte artigo do Microsoft Knowledge Base KB326965, "IIS 6.0 oferece não servir desconhecido tipos MIME" em [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;326965](http://support.microsoft.com/default.aspx?scid=kb;en-us;326965).  
  
## Mapeamentos de tipo de conteúdo  
 Ao publicar via HTTP, o tipo de conteúdo \(também conhecido como o tipo MIME\) para o arquivo. Application deve ser "application\/x\-ms\-application." Se você tiver [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] instalado no servidor, ele será definido para você automaticamente.  Se isso não estiver instalado, você precisará criar uma associação de tipo MIME para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vroot do aplicativo \(ou todo o servidor\).  
  
 Se você implantar usando um servidor IIS, execute o inetmgr. exe e adicionar um novo tipo de conteúdo de "application\/x\-ms\-application" para a extensão. Application.  
  
## Problemas de compactação HTTP  
 Com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], você pode realizar downloads que usam a compactação HTTP, uma tecnologia de servidor Web que usa o algoritmo GZIP para compactar um fluxo de dados antes de enviar o fluxo para o cliente.  O cliente — nesse caso, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]— descompacta o fluxo antes de ler os arquivos.  
  
 Se você estiver usando o IIS, você pode facilmente ativar a compactação HTTP.  No entanto, quando você ativa a compactação HTTP, ele só é habilitado para determinados tipos de arquivo — isto é, os arquivos HTML e texto.  Para ativar a compactação para assemblies \(. dll\), XML \(. xml\), \(. Application\), de manifestos de implantação e manifestos de aplicativo \(. manifest\), você deve adicionar esses tipos de arquivo à lista de tipos para o IIS para compactar.  Até que você adicione os tipos de arquivo para sua implantação, apenas o texto e arquivos HTML serão compactados.  
  
 Para obter instruções detalhadas para o IIS, consulte [como especificar tipos de documentos adicionais para a compactação HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## Consulte também  
 [Solução de problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Pré\-requisitos de implantação de aplicativos](../deployment/application-deployment-prerequisites.md)