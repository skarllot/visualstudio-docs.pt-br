---
title: "Criando aplicativos ClickOnce para a implanta&#231;&#227;o por terceiros | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Elemento <useManifestForTrust>"
  - "manifestos de aplicativos [ClickOnce]"
  - "Aplicativos ClickOnce, implantados por outros"
  - "Aplicativos ClickOnce, .NET Framework anterior"
  - "Aplicativos ClickOnce, versões anteriores do .NET Framework"
  - "implantações de cliente [ClickOnce]"
  - "manifestos [ClickOnce]"
  - "identidade visual e implantação múltipla de ClickOnce"
  - "informações de identidade visual preservadas"
  - "aplicativos confiáveis, ClickOnce"
  - "Elemento useManifestForTrust"
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Criando aplicativos ClickOnce para a implanta&#231;&#227;o por terceiros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nem todos os desenvolvedores que estão criando ClickOnce implantações planejam implantar os próprios aplicativos.  Muitas delas basta empacotar seus aplicativos usando o ClickOnce e, em seguida, entregar os arquivos para um cliente, como, por exemplo, uma grande corporação.  O cliente torna\-se responsável por que hospeda o aplicativo em sua rede.  Este tópico discute alguns dos problemas inerentes a tais deployments em versões do.NET Framework anterior à versão 3.5.  Além disso, descreve uma nova solução fornecida usando o recurso de novo "usar manifesto para relação de confiança" na.NET Framework 3.5.  Finalmente, ele conclui com as estratégias recomendadas para a criação de implantações de ClickOnce para os clientes que ainda estão usando versões antigas do.NET Framework.  
  
## Problemas envolvidos na criação de implantações para clientes  
 Vários problemas ocorrem quando você planeja fornecer uma implantação para um cliente.  A primeira questão está relacionada à assinatura de código.  Para ser implantado em uma rede, o manifesto de implantação e o manifesto de aplicativo de uma implantação de ClickOnce devem ambos ser assinados com um certificado digital.  Isso suscita a pergunta de se usar o certificado do desenvolvedor ou do cliente ao assinar os manifestos.  
  
 A questão de certificado a ser usado é essencial, como a identidade do aplicativo de um ClickOnce se baseia a assinatura digital do manifesto de implantação.  Se o desenvolvedor assina o manifesto de implantação, ele pode levar a conflitos, se o cliente é uma grande empresa, e mais de uma divisão da empresa implanta uma versão personalizada do aplicativo.  
  
 Por exemplo, digamos que a Adventure Works tem um departamento de finanças e um departamento de recursos humanos.  Ambos os departamentos de licença do Microsoft Corporation que gera relatórios dos dados armazenados em um banco de dados SQL de um aplicativo de ClickOnce.  A Microsoft fornece a cada departamento com uma versão do aplicativo que é personalizado para seus dados.  Se os aplicativos são assinados com o mesmo certificado Authenticode, um usuário que tenta usar ambos os aplicativos encontraria um erro, como o segundo aplicativo como sendo idênticas ao primeiro considere ClickOnce.  Nesse caso, o cliente poderia enfrentar efeitos colaterais imprevisíveis e indesejados que incluem a perda de quaisquer dados armazenados localmente pelo aplicativo.  
  
 Um problema adicional relacionado à assinatura de código é o `deploymentProvider` elemento no manifesto de implantação, que informa ao ClickOnce onde procurar por atualizações de aplicativos.  Este elemento deve ser adicionado para o manifesto de implantação antes para assiná\-lo.  Se este elemento for adicionado posteriormente, o manifesto de implantação deve ser assinado novamente.  
  
### Exigir que o cliente assinar o manifesto de implantação  
 Uma solução para esse problema de implantações de não\-exclusivos é ter o sinal do desenvolvedor o manifesto do aplicativo e o cliente assinar o manifesto de implantação.  Embora essa abordagem funcione, ele apresenta outros problemas.  Uma vez que um certificado Authenticode deve permanecer um ativo protegido, o cliente não pode dar apenas o certificado ao desenvolvedor para assinar a implantação.  Enquanto o cliente pode assinar a implantação se manifestam usando ferramentas disponíveis gratuitamente com o.NET Framework SDK, isso pode exigir conhecimento técnico mais que o cliente está disposto ou capaz de fornecer.  Em tais casos, o desenvolvedor geralmente cria um aplicativo, site ou outro mecanismo através do qual o cliente pode enviar a sua versão do aplicativo para assinatura.  
  
### O impacto do cliente, assinatura de segurança de aplicativos de ClickOnce  
 Mesmo que o desenvolvedor e o cliente concordam que o cliente deve assinar o manifesto de aplicativo, isso gera outros problemas que cercam a identidade do aplicativo, especialmente à medida que ele se aplica à implantação de aplicativos confiáveis.  \(Para obter mais informações sobre esse recurso, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).\) Digamos que a Adventure Works deseja configurar seus computadores clientes para que qualquer aplicativo fornecido a ele pela Microsoft Corporation seja executado com confiança total.  Se a Adventure Works assina o manifesto de implantação, ClickOnce usará assinatura de segurança do trabalho de aventura para determinar o nível de confiança do aplicativo.  
  
## Criação de implantações de clientes usando o manifesto do aplicativo para confiança  
 ClickOnce na.NET Framework 3.5 contém um novo recurso que oferece uma nova solução de desenvolvedores e clientes para o cenário de como os manifestos devem ser assinados.  O manifesto do aplicativo ClickOnce oferece suporte a um novo elemento chamado `<useManifestForTrust>` que permite que um desenvolvedor significar que a assinatura digital do manifesto do aplicativo é o que deve ser usado para tomar decisões de confiança.  O desenvolvedor usa ferramentas de empacotamento de ClickOnce — como, por exemplo, Visual Studio, MageUI.exe e Mage — para incluir este elemento no manifesto do aplicativo, bem como para incorporar tanto o nome do editor como o nome do aplicativo no manifesto.  
  
 Ao usar o `<useManifestForTrust>`, o manifesto de implantação não precisa ser assinado com um certificado Authenticode emitido por uma autoridade de certificação.  Em vez disso, ele pode ser assinado com o que é conhecido como um certificado auto\-assinado.  Um certificado auto\-assinado é gerado pelo cliente ou o desenvolvedor usando padrão.Ferramentas do NET Framework SDK e, em seguida, aplicada para o manifesto de implantação usando as ferramentas de implantação de ClickOnce padrão.  Para obter mais informações, consulte [Makecert.exe \(Ferramenta de Criação de Certificado\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md).  
  
 Usando um certificado auto\-assinado para obter o manifesto de implantação apresenta diversas vantagens.  Eliminando a necessidade do cliente obter ou criar seus próprios certificados Authenticode, `<useManifestForTrust>` simplifica a implantação para o cliente, permitindo que o desenvolvedor manter sua própria identidade de marca no aplicativo.  O resultado é um conjunto de implantações assinados que são mais seguros e têm identidades de aplicativos exclusivo.  Isso elimina o conflito potencial que pode ocorrer com a implantação do mesmo aplicativo para vários clientes.  
  
 Para obter informações passo a passo sobre como criar uma implantação de ClickOnce com `<useManifestForTrust>` habilitado, consulte [Instruções passo a passo: implantando manualmente um aplicativo ClickOnce que não requer nova assinatura e que preserva informações de identidade visual](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### Manifesto de aplicativo como para confiança funciona em tempo de execução  
 Para obter uma melhor compreensão de como funciona o usar o manifesto do aplicativo para confiança em tempo de execução, considere o exemplo a seguir.  Um aplicativo de ClickOnce que tem como alvo o.NET Framework 3.5 é criado pela Microsoft.  O manifesto do aplicativo usa a `<useManifestForTrust>` elemento e é assinado pela Microsoft.  A Adventure Works assina o manifesto de implantação usando um certificado auto\-assinado.  Adventure Works, os clientes são configurados para confiar em qualquer aplicativo assinado pela Microsoft.  
  
 Quando um usuário clica em um link para o manifesto de implantação, o ClickOnce instala o aplicativo no computador do usuário.  As informações do certificado e a implantação de identificar o aplicativo exclusivamente para ClickOnce no computador cliente.  Se o usuário tentar instalar novamente o mesmo aplicativo de um local diferente, o ClickOnce pode usar esta identidade para determinar se o aplicativo já existe no cliente.  
  
 Em seguida, ClickOnce examina o certificado Authenticode que é usado para assinar o manifesto de aplicativo, que determina o nível de confiança que darão a ClickOnce.  Desde que a Adventure Works configurou seus clientes para confiar em qualquer aplicativo assinado pela Microsoft, este aplicativo de ClickOnce seja concedido confiança total.  Para obter mais informações, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
## Criação de implantações de cliente para versões anteriores  
 E se um desenvolvedor está implantando aplicativos de ClickOnce para clientes que estiverem usando versões antigas do.NET Framework?  As seções a seguir resumem as várias soluções recomendadas, juntamente com os benefícios e desvantagens de cada.  
  
### Implantações de sinal no nome do cliente  
 Uma estratégia de implantação possíveis é para o desenvolvedor criar um mecanismo para assinar as implantações em nome dos seus clientes, usando a chave particular do cliente.  Isso impede que o desenvolvedor ter que gerenciar chaves particulares ou vários pacotes de implantação.  O desenvolvedor apenas fornece a mesma implantação para cada cliente.  Ele é o cliente para personalizá\-lo para seu ambiente usando o serviço de autenticação.  
  
 Uma desvantagem desse método é o tempo e as despesas necessárias para implementá\-lo.  Enquanto um serviço pode ser construído usando as ferramentas fornecidas na.NET Framework SDK, ele irá adicionar mais tempo de desenvolvimento para o ciclo de vida do produto.  
  
 Como indicado anteriormente neste tópico, outra desvantagem é que a versão de cada cliente do aplicativo terá a mesma identidade de aplicativo, o que poderia levar a conflitos.  Se esta for uma preocupação, o desenvolvedor pode alterar o campo de nome usado ao gerar o manifesto de implantação para dar um nome exclusivo de cada aplicativo.  Isso irá criar uma identidade separada para cada versão do aplicativo e eliminar quaisquer possíveis conflitos de identidade.  Este campo corresponde do `-Name` argumento Mage e até o  **nome** campo o  **nome** guia em MageUI.exe.  
  
 Por exemplo, digamos que o desenvolvedor criou um aplicativo chamado Application1.  Em vez de criar uma única implantação com o campo de nome definido para Application1, o desenvolvedor pode criar várias implantações com esse nome, como, por exemplo, Application1\-CustomerA, CustomerB\-Application1, uma variação específicos do cliente e assim por diante.  
  
### Implantação usando um pacote de instalação  
 Uma estratégia de implantação possíveis a segunda é gerar um projeto de instalação do Microsoft para executar a implantação inicial do aplicativo ClickOnce.  Isso pode ser fornecida em um dos vários formatos diferentes: como uma implantação MSI, como um executável de instalação \(.EXE\), ou como um arquivo de gabinete \(. cab\) em conjunto com um script em lotes.  
  
 Usando esta técnica, o desenvolvedor poderia fornecer ao cliente uma implantação que inclui os arquivos do aplicativo, o manifesto do aplicativo e um manifesto de implantação que serve como um modelo.  O cliente executaria o programa de instalação, que solicitaria\-los para uma URL de implantação \(servidor ou local do qual os usuários instalarão o aplicativo de ClickOnce do compartilhamento de arquivo\), bem como um certificado digital.  O aplicativo de instalação também pode escolher pedir opções adicionais de configuração ClickOnce, como, por exemplo, o intervalo de verificação de atualização.  Depois que essas informações são reunidas, o programa de instalação seria gere o manifesto de implantação real, assiná\-lo e publicar o aplicativo ClickOnce para o local de servidor designado.  
  
 Existem três maneiras para que o cliente pode assinar o manifesto de implantação nesta situação:  
  
1.  O cliente pode usar um certificado válido emitido por uma autoridade de certificação \(CA\).  
  
2.  Como uma variação nessa abordagem, o cliente pode escolher assinar seu manifesto de implantação com um certificado auto\-assinado.  A desvantagem é que ele fará com que o aplicativo para exibir as palavras "Editor desconhecido" quando o usuário é perguntado se deseja instalá\-lo.  No entanto, a vantagem é que ele impede que os clientes menores não precisarão gastar tempo e dinheiro necessário para um certificado emitido por uma autoridade de certificação.  
  
3.  Finalmente, o desenvolvedor pode incluir seu próprio certificado auto\-assinado no pacote de instalação.  Isso introduz os problemas potenciais com a identidade do aplicativo discutidas anteriormente neste tópico.  
  
 A desvantagem do método de projeto de implantação do programa de instalação é o tempo e as despesas necessárias para construir um aplicativo de implantação personalizada.  
  
### Ter o cliente gere o manifesto de implantação  
 Uma estratégia de implantação possíveis a terceira é para entregar apenas os arquivos de aplicativo e o manifesto de aplicativo logoff para o cliente.  Nesse cenário, o cliente é responsável por usar o.NET Framework SDK para gerar e assinar o manifesto de implantação.  
  
 A desvantagem desse método é que ele requer que o cliente instalar o.Ferramentas do NET Framework SDK e fazer com que um desenvolvedor ou administrador do sistema que é qualificada para usá\-los.  Alguns clientes talvez demandam uma solução que requer pouco ou nenhum esforço técnico na sua parte.  
  
## Consulte também  
 [Implantando aplicativos ClickOnce para servidores de teste e produção sem assinar novamente](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Instruções passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Instruções passo a passo: implantando manualmente um aplicativo ClickOnce que não requer nova assinatura e que preserva informações de identidade visual](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)