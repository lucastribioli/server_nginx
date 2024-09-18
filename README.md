# Estudo Servidor Web

## Servidor Web X Servidor de aplicação
O servidor web é como um atendente de um restaurante. Ele recebe o pedido do cliente (seu navegador), que é a URL da página que você quer acessar. Ele então verifica se a página existe e, se existir, ele a entrega para você.

Já o servidor de aplicação é como o cozinheiro do restaurante. Ele é responsável por preparar a página, ou seja, ele processa as informações que a página precisa para funcionar, como dados do banco de dados, lógica de negócio e outras informações.

Em resumo:

Servidor web: Responsável por receber e enviar arquivos, como HTML, CSS e JavaScript.
Servidor de aplicação: Responsável por processar as informações e gerar a página final que o servidor web irá enviar para o seu navegador.

## Proxy Reverso

O Proxy Reverso é como um intermediário entre o seu navegador (cliente) e o servidor web. Ele recebe a sua requisição, a encaminha para o servidor web e, em seguida, retorna a resposta para você.

Mas, além de apenas encaminhar a requisição, o Proxy Reverso pode fazer algumas coisas interessantes:

* Balancear a carga: Se você tem vários servidores web, o Proxy Reverso pode distribuir as requisições entre eles, garantindo que nenhum servidor fique sobrecarregado.
* Criptografar o tráfego: O Proxy Reverso pode criptografar o tráfego entre o seu navegador e o servidor web, protegendo suas informações.
* Adicionar cabeçalhos: O Proxy Reverso pode adicionar cabeçalhos HTTP à requisição, como o X-Real-IP, que informa o IP real do cliente.
* Cachear conteúdo: O Proxy Reverso pode armazenar em cache o conteúdo do servidor web, diminuindo o tempo de resposta para o cliente.

## API Gateway
API Gateway é como um "garçom" que facilita a comunicação entre os clientes e os serviços da sua aplicação, além de oferecer alguns serviços extras para melhorar a performance, a segurança e a gestão da sua API.

## Load Balancer
O Load Balancer é como um "gerente" que distribui as requisições dos clientes (navegadores, aplicativos, etc.) para os servidores web que estão disponíveis. Ele garante que nenhum servidor fique sobrecarregado e que todos os clientes sejam atendidos de forma rápida e eficiente.

O Load Balancer pode usar diferentes estratégias para distribuir as requisições, como:

* Round Robin: As requisições são distribuídas para os servidores web em ordem circular.
* Least Connections: As requisições são direcionadas para o servidor web que tem menos conexões ativas.
* Weighted Round Robin: As requisições são distribuídas para os servidores web de acordo com um peso definido, por exemplo, um servidor web mais potente pode receber mais requisições.
