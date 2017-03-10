---
title: "Emulador do Visual Studio para Android | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "crdun"
manager: "crdun"
---
# Emulador do Visual Studio para Android
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O Visual Studio emulador Android é um aplicativo de desktop que emula um dispositivo Android.  Ele fornece um ambiente virtualizado no qual você pode depurar e testar aplicativos Android sem um dispositivo físico.  Ele também fornece um ambiente isolado para protótipos de seu aplicativo.  
  
 O Visual Studio emulador Android foi projetado para fornecer desempenho comparável para um dispositivo real.  Antes de publicar seu aplicativo, no entanto, é recomendável que você teste seu aplicativo em um dispositivo físico.  
  
 Você pode testar seu aplicativo em um perfil de dispositivo exclusivo para cada uma das plataformas Android, resoluções de tela e outras propriedades de hardware com suporte pelo emulador do Visual Studio para o Android.  
  
 Este tópico contém as seções a seguir.  
  
-   [Instalando e desinstalando](#Installing)  
  
-   [Requisitos do sistema e compatibilidade com versões anteriores](#Requirements)  
  
-   [Rede no emulador do Visual Studio para Android](#Networking)  
  
-   [Configurar o emulador do Visual Studio para Android](#Configuring)  
  
-   [Recursos que você pode testar no emulador](#FeaturesTest)  
  
-   [Recursos que não é possível testar no emulador](#FeaturesNonTest)  
  
-   [Recursos de suporte](#Support)  
  
##  <a name="Installing"></a> Instalando e desinstalando  
 Instalando o  
  
 Visual Studio emulador Android é um componente das ferramentas de multiplataforma disponíveis no Visual Studio e será instalado durante uma instalação personalizada do Visual Studio quando você seleciona o desenvolvimento entre plataformas móveis, e ferramentas comuns e Kits de desenvolvimento de Software e, em seguida, emulador do Visual Studio para o Android.  
  
 Desinstalando  
  
 Você pode desinstalar o Visual Studio emulador para Android usando Adicionar ou remover programas no painel de controle.  
  
> [!NOTE]
>  Desinstalando o Visual Studio não desinstalará o emulador.  Você deve desinstalar o emulador separadamente.  
  
 Quando você desinstala o emulador do Visual Studio para o Android, Hyper\-V Ethernet adaptadores virtuais que foram criados para usar o emulador não são removidos automaticamente.  Você pode remover manualmente esses adaptadores virtuais \(se não estiver em uso\) por abrir o Gerenciador do Hyper\-V, selecionando uma das imagens VHD do emulador, escolhendo a guia rede e**Remover**para cada uma das opções que aparecem nesta guia.  
  
##  <a name="Requirements"></a> Requisitos do sistema e compatibilidade com versões anteriores  
 Para obter informações importantes sobre o hardware, software e requisitos de configuração para o emulador do Visual Studio para o Android, consulte o tópico a seguir.  
  
-   [Requisitos do sistema para o emulador do Visual Studio para Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
 Visual Studio emulador Android requer 2015 do Visual Studio; não é compatível com versões anteriores do Visual Studio.  
  
 Novas versões do emulador instaladas sobre versões antigas \(e podem, em alguns casos, substituir as imagens antigas, descartando as configurações, aplicativos e arquivos instalados nessas imagens\).  
  
##  <a name="Networking"></a> Rede no emulador do Visual Studio para Android  
 A conexão de rede do Visual Studio emulador para Android se comporta como a conexão de um computador desktop com as seguintes características:  
  
-   O emulador é exibido na rede como um dispositivo separado com seu próprio endereço IP.  
  
-   Ele não requer nenhum software de rede adicional que ainda não foi instalado com o emulador.  
  
-   Ele não está associado a um domínio do Windows.  
  
 Para compreender os recursos de conexão de rede do emulador, pense nisso como se fossem uma conexão Wi\-Fi do seu telefone Android à mesma rede.  Se um aplicativo em execução no seu telefone pode acessar um recurso de rede em sua conexão Wi\-Fi, um aplicativo em execução no emulador também pode acessar o mesmo recurso de rede.  
  
 Para obter mais informações sobre requisitos de rede, consulte[Requisitos do sistema para o emulador do Visual Studio para Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
 Para obter informações sobre solução de problemas de rede, consulte[Solução de problemas do emulador do Visual Studio para Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Configuring"></a> Configurar o emulador do Visual Studio para Android  
 Teste seu aplicativo Android para compatibilidade entre a incrível variedade de hardware Android pode ser um desafio.  Telefones Android e tablets no mercado abrangem uma ampla gama de versões e tamanhos de tela e vêm em muitas configurações de hardware diferentes \(RAM, CPUs, arquitetura, etc.\).  O Visual Studio emulador Android simplifica isso usando perfis de dispositivos.  Nosso conjunto de perfis de dispositivos representam o hardware mais popular no mercado, incluindo dispositivos da Samsung, Motorola, Sony, LG e muito mais.  
  
 No Visual Studio de 2015, instalar, desinstalar e iniciar os perfis de dispositivo usando o Gerenciador de emulador.  Acessar o Gerenciador de emulador escolhendo**ferramentas**em seguida,**Visual Studio emulador Android**.  
  
 ![The Visual Studio Emulator for Android Manager](../cross-platform/media/android_emu_manager.png "Android\_Emu\_Manager")  
  
 Por padrão, há quatro perfis de dispositivo previamente instalado \(KitKat e pirulito phone\/5 "e tablet\/7" configurações\), conforme indicado pelo texto em branco e ícones.  Outros perfis na lista aparecerão esmaecidos até que você escolha o**instalar perfil**botão e a instalação for concluída.  Você pode filtrar a lista por nível de API e clique na seta de detalhes no lado direito inferior de um perfil para exibir seus detalhes de configuração completa.  
  
 Depois de instalar o conjunto de perfis que você gostaria de destino, você pode iniciar esses novos perfis diretamente do Gerenciador de pressionando o verde**reproduzir**botão.  Além disso, eles aparecerão no menu suspenso do destino debug em qualquer tipo de projeto móvel multiplataforma do Visual Studio.  
  
##  <a name="FeaturesTest"></a> Recursos que você pode testar no emulador  
 Para obter informações detalhadas sobre os recursos que você pode testar no emulador, consulte[documentação](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx).  
  
##  <a name="FeaturesNonTest"></a> Recursos que não é possível testar no emulador  
 A lista a seguir descreve os recursos da plataforma Android que você**não é possível**testar no emulador.  Você deve testar esses recursos em um dispositivo físico.  
  
-   Bússola  
  
-   Giroscópio  
  
-   Controlador de vibração  
  
-   Brilho.  Alterar o nível de brilho do emulador não afetará visualmente a maneira como o dispositivo aparece na tela.  
  
##  <a name="Support"></a> Recursos de suporte  
 Se o computador host atende aos requisitos de sistema e encontrar um problema não abordados neste guia de solução de problemas:  
  
-   Faça uma pergunta sobre o uso de StackOverflow a[emulador android](http://stackoverflow.com/questions/tagged/android-emulator)e a marca do visual studio.  
  
-   Relate um problema usando o enviar um sorriso ferramenta no Visual Studio ou no Gerenciador de emulador.  
  
## Consulte também  
 [Requisitos do sistema para o emulador do Visual Studio para Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Solução de problemas do emulador do Visual Studio para Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)