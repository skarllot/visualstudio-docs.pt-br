---
title: "Depurar XAML no Blend | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar XAML no Blend
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar as ferramentas no [!INCLUDE[blend_first](../debugger/includes/blend_first_md.md)] para depurar o XAML em seu aplicativo.  Ao compilar um projeto, qualquer erro é exibido no painel **Resultados**.  Clique duas vezes em um erro para localizar a marcação relacionada ao erro.  Se você precisar de mais espaço para trabalhar, oculte o painel **Resultados** pressionando F12.  
  
## Erros de sintaxe  
 Erros de sintaxe ocorrem quando o XAML ou os arquivos code\-behind não seguem as regras de formatação do idioma.  A descrição do erro pode ajudar você a entender como corrigi\-lo.  A lista também especifica o nome do arquivo e o número da linha em que se encontra o erro.  Os erros de XAML são listados na guia **Marcação** do painel **Resultados**.  
  
> [!TIP]
>  XAML é uma linguagem de marcação baseada em XML e segue as regras de sintaxe XML.  
  
 Algumas causas comuns de erros de sintaxe XAML são:  
  
-   Uma palavra\-chave com erro de ortografia ou de capitalização.  
  
-   Aspas faltando ao redor de atributos ou cadeias de caracteres de texto.  
  
-   Está faltando um elemento XAML em uma marca de fechamento.  
  
-   Um elemento XAML existe em um local onde não é permitido.  
  
 Para mais informações sobre a sintaxe XAML comum, veja [Guia de sintaxe básica XAML](http://go.microsoft.com/fwlink/?LinkId=329942).  
  
 Você também pode identificar e resolver erros de sintaxe code\-behind simples, erros de compilação e de tempo de execução no [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  No entanto, os erros de code\-behind podem ser mais fáceis de identificar e resolver no Visual Studio.  
  
### Depurando código XAML de exemplo  
 O exemplo a seguir detalhará a uma sessão de depuração XAML simples no [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  
  
##### Para criar um projeto  
  
1.  No [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)], abra o menu **Arquivo** e clique em **Novo Projeto**.  
  
     Na caixa de diálogo **New Project**, é exibida uma lista de tipos de projetos no lado esquerdo.  Quando você clica em um tipo de projeto, os modelos de projeto associados a ele aparecem do lado direito.  
  
2.  Na lista de tipos de projetos, clique em **XAML \(Windows Store\)**.  
  
3.  Na lista de modelos de projetos, clique em **Blank App**.  
  
4.  Na caixa de texto **Nome**, digite `DebuggingSample`.  
  
5.  Na caixa de texto **Location**, verifique a localização do projeto.  
  
6.  Na lista **Linguagem**, clique em **Visual C\#** e em **OK** para criar o projeto.  
  
7.  Clique com o botão direito do mouse na superfície de design e clique em **Exibir Código\-Fonte** para alternar para o modo de exibição **Divisão**.  
  
8.  Copie o código a seguir clicando no link **Copiar** no canto superior direito do código.  
  
    ```  
    <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
         <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
         <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
    </Grid>  
  
    ```  
  
9. Localize o elemento **Grid** padrão e coloque o código entre as marcas **Grid** inicial e final.  Quando você terminar, seu código deverá parecer como este:  
  
    ```  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
         </Grid>  
    </Grid>  
  
    ```  
  
10. Pressione Ctrl\+Shift\+B para compilar o projeto.  
  
 Uma mensagem de erro aparece alertando você que o projeto não pode ser criado, e o painel **Resultados**, listando os erros, aparece na parte inferior do aplicativo.  
  
 ![Debug XAML in Blend for Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend\_debugXAML\_XAML")  
  
### Resolvendo erros de XAML  
 Quando são detectados erros de XAML, a superfície de design exibe um alerta informando que seu projeto contém marcação inválida.  À medida que você resolve os erros, a lista de erros no painel **Resultados** é atualizada.  Quando você tiver resolvido todos os erros, a superfície de design é habilitada e seu aplicativo é exibido na superfície de design.  
  
##### Para resolver os erros de XAML  
  
1.  Clique duas vezes no primeiro erro da lista.  A descrição é "O valor '\<' não é um válido em um atributo". Quando você clica duas vezes no erro, o ponteiro encontra o local correspondente no código.  O `<` que precede `Button` é válido e não um atributo, conforme sugerido na mensagem de erro.  Se você observar a linha de código precedente, notará que as marcas de aspas de fechamento para o atributo `Top` estão faltando.  Digite as marcas de aspas de fechamento.  Observe que a lista de erros no painel **Resultados** é atualizada de acordo com suas alterações.  
  
2.  Clique duas vezes na descrição "'0' não é válido no início de um nome". `Margin="0,149,0,0"` aparecerá bem formada.  No entanto, observe que a codificação de cor da `Margin` não corresponde a outras instâncias de `Margin` no código.  Como as marcas de cotação de fechamento estão faltando do par de nome\/valor precedente \(`VerticalAlignment="Top`\), `Margin="` que é lido como parte do valor do atributo precedente, e 0 é lido como o início de um par de nome\/valor.  Digite as marcas de aspas de fechamento para `Top`.  Observe que a lista de erros no painel **Resultados** é atualizada de acordo com suas alterações.  
  
3.  Clique duas vezes no erro restante, "A marca XML de fechamento 'Button' é discrepante." O ponteiro está localizado na marca **Grid** de fechamento \(`</Grid>`\), sugerindo que o erro está dentro do objeto `Grid`.  Observe que o segundo objeto `Button` está sem a marca de fechamento.  Depois de adicionar a `/` de fechamento, a lista de painéis dos **Resultados** é atualizada.  Agora que esses erros iniciais foram resolvidos, dois erros adicionais foram identificados.  
  
4.  Clique duas vezes em "O membro 'content' não é reconhecido nem acessível." O `c` em `content` deve estar em maiúsculas.  Substitua o "c" minúsculo pelo "c" maiúsculo.  
  
5.  Clique duas vezes em "A propriedade 'Mame' não existe no namespace 'http:\/\/schemas.microsoft.com\/winfx\/2006\/xaml'." O "M", em "Mame" deve ser um "N". Substitua o "M" por um "N". Agora que o XAML pode ser analisado, o aplicativo aparece na superfície de design.  
  
     ![Debugging XAML in Blend for Visual Studio](~/debugger/media/blend_debugartboard_xaml.png "blend\_debugArtboard\_XAML")  
  
     Pressione Ctrl\+Shift\+B para compilar um projeto e confirmar que não há restam erros.  
  
## Depurando no Visual Studio  
 Você pode abrir projetos do [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] no Visual Studio para depurar o código de maneira mais fácil em seu aplicativo.  Para abrir um projeto do [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] no Visual Studio, clique com o botão direito do mouse no painel **Projetos** e clique em **Editar no Visual Studio**.  Quando você encerrar sua sessão de depuração no Visual Studio, pressione Ctrl\+Shift\+S para salvar todas as mudanças e voltar para o [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  Você será solicitado a recarregar o projeto.  Clique em **Sim para Todos** para continuar trabalhando no [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].  
  
 Para obter mais informações sobre como depurar seu aplicativo, veja [Depurar aplicativos da Windows Store no Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).  
  
## Obtendo ajuda  
 Se você precisar de mais ajuda para depurar seu aplicativo [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)], pesquise nos [fóruns da comunidade de aplicativos da Windows Store](http://go.microsoft.com/fwlink/?LinkId=280308) as postagens relacionadas ao seu problema ou para postar uma pergunta.