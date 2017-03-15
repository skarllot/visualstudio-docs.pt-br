---
title: "Seguran&#231;a de acesso do c&#243;digo para aplicativos ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XBAPProjectPropertiesSecurity.HowTo"
  - "vb.XBAProjectPropertiesSecurity.HowTo"
  - "vb.ProjectPropertiesSecurity.HowTo"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Implantando aplicativos [ClickOnce], segurança"
  - "Aplicativos ClickOnce, caspol"
  - "segurança ClickOnce, aplicativos hospedados pelo navegador WPF"
  - "segurança ClickOnce, aplicativos ClickOnce"
  - "Aplicativos ClickOnce, políticas de segurança de acesso do código"
  - "segurança, ClickOnce"
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
caps.latest.revision: 31
caps.handback.revision: 31
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Seguran&#231;a de acesso do c&#243;digo para aplicativos ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aplicativos ClickOnce são baseados no .NET Framework e estão sujeitos a restrições de segurança de acesso do código. Por esse motivo, é importante entender as implicações de código de segurança de acesso e escrever aplicativos ClickOnce adequadamente.  
  
 Segurança de acesso ao código é um mecanismo no .NET Framework que ajuda a limitar o acesso código tem a recursos e operações protegidos. Você deve configurar as permissões de segurança de acesso do código para seu aplicativo ClickOnce usar a zona apropriada para o local do instalador do aplicativo. Na maioria dos casos, você pode escolher o **Internet** zona para um conjunto limitado de permissões ou a **Intranet Local** zona para um conjunto maior de permissões.  
  
## Segurança de acesso ao código do ClickOnce padrão  
 Por padrão, um aplicativo ClickOnce recebe permissões de confiança total, quando ele é instalado ou executado em um computador cliente.  
  
-   Um aplicativo que tenha permissões de confiança total tem acesso irrestrito aos recursos, como o sistema de arquivos e registro. Isso potencialmente permite que seu aplicativo \(e sistema do usuário final\) ser explorado por códigos mal\-intencionados.  
  
-   Quando um aplicativo requer permissões de confiança total, o usuário final pode ser solicitado para conceder permissões para o aplicativo. Isso significa que o aplicativo não fornecer realmente uma experiência de ClickOnce e o prompt pode ser confuso para usuários menos experientes.  
  
    > [!NOTE]
    >  Ao instalar um aplicativo de uma mídia removível, como um CD\-ROM, o usuário não é solicitado. Além disso, um administrador de rede pode configurar a diretiva de rede para que os usuários não são solicitados ao instalar um aplicativo de uma fonte confiável. Para obter mais informações, consulte [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
 Para restringir as permissões para um aplicativo ClickOnce, você pode modificar as permissões de segurança de acesso do código para seu aplicativo solicitar a zona que melhor atenda as permissões que seu aplicativo requer. Na maioria dos casos, você pode selecionar a zona da qual o aplicativo está sendo implantado. Por exemplo, se seu aplicativo for um aplicativo empresarial, você pode usar o **Intranet Local** zona. Se seu aplicativo for um aplicativo da internet, você pode usar o **Internet** zona.  
  
## Configurar permissões de segurança  
 Você sempre deve configurar seu aplicativo ClickOnce para solicitar a zona apropriada para limitar as permissões de segurança de acesso do código. Você pode configurar permissões de segurança no **segurança** página do **Project Designer**.  
  
 O **segurança** página o **Project Designer** contém um **Ativar configurações de segurança do ClickOnce** caixa de seleção. Quando esta caixa de seleção estiver marcada, as solicitações de permissão de segurança são adicionadas ao manifesto de implantação para seu aplicativo. No momento da instalação, o usuário precisará conceder permissões se as permissões solicitadas excederem as permissões padrão para a zona da qual o aplicativo é implantado. Para obter mais informações, consulte [Como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 Os aplicativos implantados em locais diferentes são concedidos níveis diferentes de permissões sem avisar. Por exemplo, quando um aplicativo é implantado pela Internet, ele recebe um conjunto altamente restritivo de permissões. Quando instalado de uma Intranet local, ele recebe permissões mais e, quando instalado de um CD\-ROM, ele recebe permissões de confiança total.  
  
 Como um ponto de partida para configurar permissões, você pode selecionar uma zona de segurança do **zona** lista o **segurança** página. Se seu aplicativo será implantado potencialmente de mais de uma zona, selecione a zona com o mínimo de permissões. Para obter mais informações, consulte [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 As propriedades que podem ser definidas variam de acordo com o conjunto de permissões; nem todos os conjuntos de permissão têm propriedades configuráveis. Para obter mais informações sobre a lista completa de permissões que seu aplicativo possa solicitar, consulte <xref:System.Security.Permissions>. Para obter mais informações sobre como definir permissões para uma zona personalizada, consulte [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## Depurando um aplicativo que possui permissões restritas  
 Como desenvolvedor, você provavelmente deve executar seu computador de desenvolvimento com permissões de confiança total. Portanto, você não verá as mesmas exceções de segurança quando você depura o aplicativo que os usuários podem ver quando eles o executam com permissões restritas.  
  
 Para capturar essas exceções, você precisa depurar o aplicativo com as mesmas permissões que o usuário final. Depuração com permissões restritas pode ser habilitada no **segurança** página do **Project Designer**.  
  
 Quando você depurar um aplicativo com permissões restritas, exceções podem ser geradas para quaisquer demandas de segurança de código não tem sido habilitadas no **segurança** página. Um exceção auxiliar será exibida, fornecendo sugestões sobre como modificar seu código para evitar a exceção.  
  
 Além disso, quando você escreve um código, o recurso IntelliSense no Editor de códigos desabilitará todos os membros que não estão incluídos nas permissões de segurança que você configurou.  
  
 Para obter mais informações, consulte [Como depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## Permissões de segurança para aplicativos hospedados em navegador  
 Visual Studio fornece os seguintes tipos de projeto para aplicativos Windows Presentation Foundation \(WPF\):  
  
-   Aplicativo do Windows WPF  
  
-   Aplicativos WPF de navegador da Web  
  
-   Biblioteca de controle personalizado WPF  
  
-   Biblioteca de serviço do WPF  
  
 Esses tipos de projeto, apenas o WPF Web Browser Applications são hospedados em um navegador da Web e, portanto, requerem implantação especial e configurações de segurança. As configurações de segurança padrão para esses aplicativos são os seguintes:  
  
-   **Habilitar configurações de segurança do ClickOnce**  
  
-   **Este é um aplicativo de confiança parcial**  
  
-   **Zona da Internet** \(com a permissão padrão definido para aplicativos de navegador WPF Web selecionada\)  
  
 No **configurações de segurança avançadas** caixa de diálogo, o **depurar esse aplicativo com o conjunto de permissões selecionado** caixa de seleção é marcada e desabilitada. Isso ocorre porque a depurar na zona não pode ser desativada para aplicativos hospedados pelo navegador.  
  
## Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Como depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Página Segurança, Designer de Projeto](../ide/reference/security-page-project-designer.md)