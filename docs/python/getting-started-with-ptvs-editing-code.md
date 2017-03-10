---
title: "Introdu&#231;&#227;o ao PTVS: editando c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 4
caps.handback.revision: 4
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
---
# Introdu&#231;&#227;o ao PTVS: editando c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O PTVS fornece a experiência de editor do Visual Studio produtiva para Python.  
  
 Assista a estas instruções em um curto [vídeo do youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Inicie com o modelo de projeto vazio aplicativo Python básico.  
  
 Comece a digitar um `from … import` linha no editor.  Você verá que a lista de preenchimento pop\-up tem uma lista completa dos módulos que estão disponíveis para importação.  Essa lista varia de acordo com sua versão do Python e o que você instalou de bibliotecas.  Use a biblioteca de matemática como exemplo.  Você notará que conforme você digita a lista de filtros de conclusões a esses itens, incluindo os caracteres que você digitou.  Conclua a instrução importando o `sin` identificador.  
  
```python  
from math import sin  
  
```  
  
 Durante a codificação, se você usar um identificador que é desvinculada, mas que podem ser encontrados nas bibliotecas do PTVS oferece uma correção rápida pop\-up para adicionar a instrução de importação apropriado que é necessário.  Por exemplo, se você digitou `cos`, em seguida, você veria **import from math** oferecidos.  
  
 Você pode usar um trecho de código para gerar código.  No menu Editar, escolha o IntelliSense e Insert Snippet.  Agora escolha Python e, em seguida, def  Chamar a função `make_dot_string` e adicione um parâmetro `x`.  Você pode adicionar asserções ao arquivo agora para desenvolvimento orientado por testes e consulte que PTVS já pode oferecer a nova função em listas de conclusão.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Agora, volte para a nova função e começar a escrever o seguinte corpo:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Você verá que o PTVS supõe que o parâmetro é um inteiro porque PTVS analisar os sites de chamada para essa função.  Você também precisará usar a correção rápida para importar `radians`.  
  
 Use outro trecho para criar um bloco principal digitando `main` no nível superior, invocando a marca inteligente da interface do usuário e usando uma guia para escolher "main de def..."  Escrever um loop básico para chamar `make_dot_string`.  Você verá que o PTVS sabe que a função retorna uma cadeia de caracteres, se você pressionar período e consulte as conclusões oferecidas.  Essas informações de tipo fluirá em todo o programa inteiro, para que onde quer que os valores de terminam, podemos fornecer dicas de ferramenta e conclusões que ajudarão você a melhor compreendam e escrever seu código.  
  
 Adicione uma chamada para imprimir e você deve ter um principal semelhante ao seguinte:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Se você pressionar F5, o código é executado em uma janela cmd.exe e você vir um ponto oscilatórios e para trás.  
  
 Assista a estas instruções em um curto [vídeo do youtube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## Consulte também  
 [Wiki documentação](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [PTVS Introdução e vídeos de mergulho profundo](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)