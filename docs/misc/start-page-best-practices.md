---
title: "Iniciar p&#225;gina pr&#225;ticas recomendadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Iniciar as dicas de página"
  - "práticas recomendadas de página STAT"
  - "Iniciar o design da página"
ms.assetid: f6ce1ce0-746e-4004-a37f-6f176f6f5851
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Iniciar p&#225;gina pr&#225;ticas recomendadas
Como pode acessar a página inicial abre e comandos do Visual Studio sempre que o Visual Studio carrega, recomendamos que você verifique a estabilidade de qualquer página de início personalizado antes de usá\-lo ou distribuí\-lo. Este tópico sugere práticas recomendadas para design de página inicial robusto e inclui diretrizes sobre como criar uma interface do usuário útil \(UI\).  
  
## Diretrizes de estabilidade  
  
### Disponibilidade de recursos  
 O aspecto mais importante na criação de uma página de início personalizado robusto é garantir que todos os recursos estão disponíveis:  
  
-   Todos os necessários pacotes são instalados.  
  
-   Pacotes são pré\-carregados.  
  
-   Todos os necessários são assemblies na pasta \\PrivateAssemblies\\.  
  
-   Cada componente que usa uma conexão de rede ou Internet possui caminhos alternativos para cenários offline e as conexões interrompidas.  
  
### Desempenho  
 Se a página inicial tem requisitos de memória grande ou carrega muitos recursos, considere como o desempenho de inicialização pode ser afetado. Essas páginas de inicialização para carregar componentes sob demanda ou em segundo plano se for possível, para que o tempo de inicialização não é significativamente maior do programa.  
  
### Processo de desenvolvimento  
 Se você modificar diretamente a página de início ativo, você pode introduzir inadvertidamente erros que causam o Visual Studio falhe. Como a página inicial abre sempre que o Visual Studio abre, um travamento Start Page é difícil de corrigir. Portanto, é recomendável que você modifique cópias dos arquivos de página inicial e testá\-los em uma instância experimental do Visual Studio para a confiabilidade. Quando a nova página inicial é estável, você pode defini\-lo para ser executado na instância principal do Visual Studio.  
  
> [!NOTE]
>  Também recomendamos que você teste qualquer página de início de terceiros em uma instância experimental do Visual Studio antes de usá\-lo na instância primária.  
  
##### Para testar uma página de início em uma instância experimental do Visual Studio  
  
1.  Se você estiver usando o modelo de projeto de página inicial, pressione F5. Caso contrário:  
  
    1.  Copie o arquivo. XAML e qualquer texto de suporte ou marcação \\%USERPROFILE%\\My Documents\\Visual Studio *\< versão \>*\\StartPages\\.  
  
    2.  Copiar todos os assemblies necessários em *\< caminho de instalação do Visual Studio \>*\\Common7\\IDE\\PrivateAssemblies\\.  
  
    3.  Abra uma instância experimental do Visual Studio usando o seguinte comando em um prompt de comando do Visual Studio.  
  
         **Devenv \/rootsuffix exp**  
  
2.  No menu **Ferramentas**, clique em **Opções**. Selecione **ambiente** e, em seguida, selecione **inicialização**. No **Personalizar página inicial** lista, selecione o arquivo StartPage renomeado e, em seguida, clique em **OK**.  
  
3.  Do **exibição** menu, clique em **Start Page**.  
  
     Abre a página de início personalizados. Se a página de início que você está modificando falhar, reinicie a instância principal do Visual Studio, fazer as correções necessárias e, em seguida, abra outra instância experimental para que você possa continuar modificar sua página de início personalizados.  
  
 Se a página inicial falhar a instância primária do Visual Studio, você pode desativar temporariamente páginas personalizadas iniciar definindo o valor do registro de HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\CustomizationEnabled como 0. Como alternativa, você pode renomear temporariamente o arquivo. XAML para a sua página inicial do padrão atual. Qualquer medida permitem que você abra o Visual Studio tempo suficiente para corrigir o erro.  
  
### Depuração  
 A janela da ferramenta Start Page captura exceções quando uma página de início é carregado pela primeira vez, mas não capturar exceções depois disso. Você pode informar ao Visual Studio para exibir todas as exceções sem tratamento, definindo o valor do registro como "1".  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\General\\EnableUnhandledExceptionDisplay  
  
 As informações de exceção serão exibido em uma caixa de mensagem, permitindo que você depure controles em uma página de início ou em outros locais sem tratamento, mesmo na instância primária do Visual Studio. Se não for possível depurar depois que a exceção é acionada, reinicie o Visual Studio com o comando "devenv \/safemode", alternar de volta para sua página de início anterior e, em seguida, continuar a depuração na instância experimental.  
  
### Caminhos relativos  
 Ao fazer referência a caminhos de arquivo de uma página de início, sempre use um caminho relativo para permitir configurações de sistema diferentes. No entanto, a raiz de todos os caminhos relativos em uma página de início resolve não na pasta \\StartPages\\ mas para... \\*Pasta de instalação do visual Studio*\\Common7\\IDE, que é onde devenv.exe está localizado. Para definir um caminho relativo à pasta \\StartPages\\, use o VS iniciar página relativa conversor. Fazer isso definindo o `Source` propriedade do objeto para `vs:StartPageRelative`, conforme mostrado no exemplo a seguir.  
  
 XAML  
  
```  
<Image Source="{vs:StartPageRelative myImage.png}" .../>  
```  
  
 Use a sintaxe de caminho relativo padrão ao acessar recursos incluídos no Visual Studio, ou arquivos incluídos em outros pacotes.  
  
### Implantação  
 Recomendamos as seguintes práticas recomendadas ao implantar uma página de início personalizados para outros usuários.  
  
#### Configurações do usuário  
  
-   Respeita as configurações do usuário. Não substitua as preferências de página de início existentes.  
  
#### VSIX  
 Essas práticas se aplicam a implantação do VSIX:  
  
-   Use o [GettingStartedGuide](http://msdn.microsoft.com/pt-br/261bb1fd-abae-4ed6-80a8-90d5fc3bb8c6) elemento no manifesto VSIX para apontar para obter instruções sobre como definir a página inicial padrão.  
  
-   Use o [nome](http://msdn.microsoft.com/pt-br/d99d38d1-060b-401a-9b9f-ede2c6213a11) elemento e [Descrição](http://msdn.microsoft.com/pt-br/24ddc57e-e991-4a43-b0c9-0e76da293e99) elemento do manifesto VSIX claramente identificam a extensão como uma página inicial e descrever sua finalidade.  
  
-   Verificar se o manifesto VSIX não contêm caminhos absolutos.  
  
-   Quando você carregar o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web, inclua a marcação relevantes para que os usuários possam identificar a extensão como uma página inicial.  
  
#### MSI  
 Se você está produzindo uma página inicial como parte de uma extensão maior do que você estiver implantando em um pacote do Windows Installer \(MSI\), você pode definir a página inicial para ser instalado como a página inicial padrão no computador de destino. Para fazer isso, escreva o nome do arquivo Start Page. XAML para o valor do Uri dessa chave do registro: HKCU\\Software\\Microsoft\\VisualStudio\\14.0\\StartPage\\Default\\. Use as seguintes diretrizes ao definir esse valor do registro:  
  
-   O instalador, fornecem a interface do usuário para permitir que o usuário selecione se deseja tornar a nova página inicial padrão.  
  
-   Se o usuário desinstalar a extensão, restaure o valor do registro anterior.  
  
### Windows Presentation Framework \(WPF\)  
 Sua marcação XAML deve seguir as práticas recomendadas do WPF. Para obter informações sobre [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] e [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] práticas recomendadas para o desenvolvimento de aplicativos, consulte os tópicos a seguir, conforme apropriado.  
  
|Área|Tópico|  
|----------|------------|  
|Acessibilidade|[Accessibility Best Practices](../Topic/Accessibility%20Best%20Practices.md)|  
|Localização|[Visão geral de localização e globalização do WPF](../Topic/WPF%20Globalization%20and%20Localization%20Overview.md)|  
|Desempenho|[Otimizando o desempenho do aplicativo WPF](../Topic/Optimizing%20WPF%20Application%20Performance.md)|  
|Segurança|[Segurança \(WPF\)](../Topic/Security%20\(WPF\).md)|  
  
## Diretrizes de Interface do usuário  
 Para garantir uma experiência de usuário intuitiva e conveniente para a página inicial, use as seguintes diretrizes de interface do usuário, onde aplicável.  
  
### Linha superior  
  
#### Faixa  
  
-   Verifique a altura da faixa de imagem igual a altura da definição de linha da linha que o contém.  
  
-   Para acomodar diferentes tamanhos de janela e resoluções de tela, fazer a imagem do banner visualmente agradável a largura.  
  
-   Manter organizada a área do banner. O logotipo com botões adicionais ou elementos gráficos não se sobrepõem.  
  
### Coluna esquerda  
  
#### Área do botão  
  
-   Colocar somente as mais controles usados na área do botão para que haja espaço para os nomes dos projetos recentes a serem exibidos. É recomendável a menos de cinco botões.  
  
#### Projetos recentes  
  
-   Esse controle permite que os projetos recentes de acesso do usuário. Você pode definir o número de projetos para exibir de 0 a 24. Como esta é a seção usada com mais freqüência da página início, é recomendável que você não removê\-lo.  
  
#### Página Opções de inicialização  
  
-   Verifique se o **Fechar página após o carregamento do projeto** e **Mostrar página na inicialização** opções são exibidas na página inicial.  
  
-   Para controles adicionais nessa área, é recomendável que você use as caixas de seleção ou botões de opção e certifique\-se de que os controles se relacionam às preferências de página inicial.  
  
### Área de conteúdo  
  
#### Guias de nível superior  
  
-   Evite adicionar tantos guias que o controle de guia quebra em larguras de tela comum.  
  
-   Use nomes curtos e descritivos para guias.  
  
-   Certifique\-se de que o guias representam áreas de conteúdo agrupadas.  
  
#### Guias de níveis inferior  
  
-   Use apenas a navegação subnível se você tiver mais de dois subtópicos.  
  
-   Evite adicionar tantos guias que o controle de guia quebra em larguras de tela comum.  
  
-   Use nomes curtos e descritivos para guias.  
  
#### Conteúdo do guia de nível inferior  
  
-   Mostre mais do que cinco itens de conteúdo em uma guia de nível inferior.  
  
#### Conteúdo do item  
  
-   Mostra links de mais de quatro por item de conteúdo.  
  
-   Se você associar imagens a itens de conteúdo, certifique\-se de que cada imagem é 175 por 125 pixels.  
  
-   Use títulos de curtos e descritivos para itens de conteúdo.  
  
-   Limitar as descrições de itens de conteúdo para duas frases ou menos.  
  
### Geral  
  
#### Animações  
  
-   Se você usar animações, limitá\-los a 0,5 segundos ou menos para ajudar a evitar qualquer percepção do desempenho ruim.  
  
#### Cores de ambiente  
  
-   Respeitar as configurações do sistema de fontes e cores.  
  
-   Use planos de fundo claros.  
  
-   Use a detecção de área de trabalho remota para garantir degradação de cor normal em sessões remotas.  
  
## Consulte também  
 [Arquitetura de página de início](/visual-cpp/misc/start-page-architecture)   
 [Implantação de páginas de início personalizado](../extensibility/deploying-custom-start-pages.md)   
 [Adicionando comandos do Visual Studio para uma página inicial](../extensibility/adding-visual-studio-commands-to-a-start-page.md)