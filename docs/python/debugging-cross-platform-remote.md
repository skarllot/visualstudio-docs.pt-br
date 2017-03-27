---
title: "Depuração remota de plataforma cruzada com as Ferramentas Python para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 7634da4bdc2b0186f410acb4eaf57a70ddea3e91
ms.lasthandoff: 03/10/2017

---

# <a name="remotely-debugging-python-code"></a>Depurando o código do Python remotamente

A PTVS (Ferramentas Python para Visual Studio) pode iniciar e depurar aplicativos do Python local e remotamente em um computador Windows (consulte [Depuração remota](../debugger/remote-debugging.md)). Ela também pode depurar remotamente em um dispositivo ou sistema operacional diferente ou em uma implementação Python que não seja o CPython usando a [biblioteca ptvsd](https://pypi.python.org/pypi/ptvsd).

Ao usar a ptvsd, o código do Python que está sendo depurado hospeda o servidor de depuração ao qual o Visual Studio pode se anexar. Isso exige uma pequena modificação no código para importar e habilitar o servidor e pode exigir configurações de rede ou de firewall no computador remoto para permitir conexões TCP.

Para obter uma introdução à depuração remota, assista a [Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc) (Aprofundamento: Depuração remota de plataforma cruzada) (youtube.com, 6min22s).

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="preparing-the-script-for-debugging"></a>Preparando o script para depuração

1. Crie um arquivo do Python com o seguinte código no computador remoto:

  ```python
  import random

  guesses_made = 0
  name = raw_input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print 'Well, {0}, I am thinking of a number between 1 and 20.'.format(name)

  while guesses_made < 6:
      guess = int(raw_input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print 'Your guess is too low.'
      if guess > number:
          print 'Your guess is too high.'
      if guess == number:
          break
  if guess == number:
      print 'Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made)
  else:
      print 'Nope. The number I was thinking of was {0}'.format(number)
  ```
 
1. Instale o pacote `ptvsd` no ambiente usando `pip install ptvsd`.

1. Habilite a depuração remota adicionando o código abaixo no primeiro ponto possível no script, antes de outros códigos. (Embora esse não seja um requisito estrito, é impossível depurar os threads em segundo plano gerados antes que a função `enable_attach` seja chamada.)

   ```python
   import ptvsd
   ptvsd.enable_attach(secret='my_secret')
   ```

   O parâmetro `secret` passado para `enable_attach` é usado para restringir o acesso ao script em execução. Ao se anexar, você precisará especificá-lo no Visual Studio ou a conexão será negada. Para desabilitá-lo e permitir que qualquer pessoa se conecte, use `enable_attach(secret=None)`.

1. Salve o arquivo e inicie o script no computador remoto. Observe que a chamada a `enable_attach` é executada em segundo plano e aguarda as conexões de entrada. Se desejado, a função `wait_for_attach` pode ser chamada após `enable_attach` para bloquear o programa até que o depurador seja anexado.

Além de `enable_attach` e `wait_for_attach`, o ptvsd também fornece uma função auxiliar `break_into_debugger`, que serve como um ponto de interrupção programático, caso o depurador seja anexado. Também há uma função `is_attached` que retorna `True` se o depurador é anexado (observe que não há necessidade de verificar esse resultado antes de chamar outras funções `ptvsd`).

## <a name="attaching-remotely-from-python-tools"></a>Anexando remotamente por meio das Ferramentas Python

Nestas etapas, definiremos um ponto de interrupção simples para interromper o processo remoto.

1. Crie uma cópia do arquivo remoto no computador local e abra-a no Visual Studio. Não importa a localização do arquivo, mas o nome deve corresponder ao nome do script no computador remoto ao qual ele será anexado.

1. Selecione **Depurar > Anexar ao Processo** para abrir a caixa de diálogo “Anexar ao Processo”.

1. Defina **Transporte** como **Depuração remota do Python**.

1. Insira o endereço do computador remoto no campo **Qualificador** e pressione Enter. Isso deverá listar os processos disponíveis nesse computador:

![Inserindo o qualificador e listando os processos](media/remote-debugging-qualifier.png)

1. Normalmente, um erro neste estágio indica que o segredo não teve uma correspondência, que a versão `ptvsd` não corresponde àquela usada pela PTVS ou que não foi possível estabelecer uma conexão. Uma das causas comuns de falha de conexão é que o computador remoto tem um firewall que está bloqueando a porta do servidor de depuração (o padrão é 5678) aberta. É possível reconfigurar o firewall ou usar outra porta; a última opção pode ser feita especificando-a explicitamente na chamada a `enable_attach` no parâmetro `address`, como:

  ```python
  ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))
  ```

  O formato do endereço é o mesmo que foi usado pelo soquete do módulo padrão do Python para soquetes do tipo `AF_INET`; consulte sua [documentação](http://docs.python.org/3/library/socket.html#socket-families) para obter detalhes. 

1. Depois que o processo for exibido na lista, clique duas vezes nele para anexá-lo. O Visual Studio exibe suas ferramentas de depuração enquanto o script continua sendo executado. Para o script de exemplo mostrado acima, a inserção de um número fará com que o ponto de interrupção seja atingido:

    ![O ponto de interrupção é atingido](media/remote-debugging-breakpoint-hit.png)

1. Neste ponto, é possível usar todos os recursos de depuração comuns da PTVS. 

1. Ao interromper a depuração, o Visual Studio se desanexa do script, mas o script continuará sendo executado no computador remoto. O servidor de depuração também continua sendo executado em seu thread em segundo plano, para que seja possível se reanexar ao processo posteriormente usando o mesmo procedimento.


## <a name="securing-the-debugger-connection-with-ssl"></a>Protegendo a conexão do depurador com o SSL

Por padrão, a conexão com o servidor de depuração remota da PTVS não é protegida de nenhuma forma; qualquer pessoa com o segredo pode se conectar e todos os dados são passados em texto sem formatação. Consequentemente, outras pessoas na rede podem rastrear os dados ou até mesmo executar um ataque MITM (man-in-the-middle). Para evitar isso, ao fazer a depuração em redes desprotegidas ou na Internet, o servidor de depuração dá suporte ao SSL. 

Para proteger o canal com o SSL, você precisará de um certificado SSL. É possível gerar um certificado autoassinado por conta própria, conforme descrito na [documentação do módulo padrão do Python `ssl`](http://docs.python.org/3/library/ssl.html#self-signed-certificates). Para evitar ataques MITM, esse certificado gerado também precisará ser adicionado ao repositório raiz da AC no computador Windows que executa a PTVS. Isso pode ser feito usando o Gerenciador de Certificados (certmgr.msc), conforme descrito em [Como fazer para exportar certificados e/ou chaves privadas?](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/how-do-i-export-certificates-andor-private-keys/7722900a-e848-4076-bc50-9e2f5e3c66ac). Observe que você precisará ter um arquivo de certificado separado (não combinado com a chave privada em um único arquivo) para importação. 

Depois gerar e registrar o certificado e os arquivos de chave privada, você precisará atualizar a chamada a `enable_attach` no script para usá-los. Isso é feito por meio dos parâmetros `certfile` e `keyfile`, que têm o mesmo significado que a função padrão `ssl.wrap_socket` do Python. Por exemplo, se o arquivo de certificado é chamado `my_cert.cer` e o arquivo de chave é chamado `my_cert.key`, use: 

```python
ptvsd.enable_attach(secret='my_secret', certfile='my_cert.cer', keyfile='my_cert.key')
```

O processo de anexação é exatamente o mesmo, conforme descrito anteriormente, com exceção de que, em vez de usar o esquema `tcp://` no Qualificador, use `tcps://`: 

![Escolhendo o transporte de depuração remota com SSL](media/remote-debugging-qualifier-ssl.png)

Se você não adicionou o certificado ao repositório raiz da AC, obterá uma mensagem de aviso: 

![Aviso do certificado SSL](media/remote-debugging-ssl-warning.png)

É possível optar por ignorar isso e continuar com a depuração; o canal ainda será criptografado contra a interceptação, mas se você ignorar o aviso, será aberta uma possibilidade de um ataque MITM.

