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

## CGI x FastCGI

O CGI é um protocolo antigo que faz com que o servidor web (como o Nginx) execute um script (como um arquivo PHP) a cada requisição. Isso significa que o servidor web precisa iniciar o script, processá-lo e enviar a resposta para o cliente a cada vez. Esse processo é lento e consome muitos recursos.

O FastCGI é uma versão mais moderna do CGI que permite que o servidor web mantenha uma conexão persistente com o script. Isso significa que o script pode ser iniciado uma vez e ficar pronto para receber novas requisições. Quando uma requisição chega, o servidor web envia a requisição para o script, que processa a requisição e envia a resposta de volta para o servidor web. Esse processo é muito mais rápido e eficiente do que o CGI.

Em resumo, o FastCGI é uma versão aprimorada do CGI que oferece melhor performance e eficiência. Ele é uma ótima opção para sites que usam scripts como PHP, Python e Ruby.

## Cache
O cache é como um "cofrinho" que o Nginx usa para guardar cópias dos arquivos que já foram requisitados. Quando alguém pede um arquivo, o Nginx primeiro olha no "cofrinho". Se o arquivo estiver lá, ele entrega a cópia direto, sem precisar ir buscar na origem. Isso é muito rápido!

Imagine que você está em um restaurante e pede um prato. Se o restaurante tiver um "cofrinho" com pratos prontos, eles podem te servir muito rápido. Mas se eles precisarem preparar o prato do zero, vai demorar mais tempo.

O cache funciona da mesma forma: ele armazena cópias dos arquivos para que o Nginx possa entregá-los mais rápido. Isso é ótimo para a performance do seu site, pois as páginas carregam mais rápido e os usuários têm uma experiência melhor.

## Compressão de arquivos
O Nginx usa o algoritmo gzip para compactar arquivos. O gzip é um algoritmo de compressão de dados muito eficiente que pode reduzir o tamanho de um arquivo em até 90%.

Para ativar a compressão de arquivos no Nginx, você precisa adicionar algumas diretivas no arquivo de configuração do Nginx. Essas diretivas informam ao Nginx quais tipos de arquivos devem ser comprimidos e quais níveis de compressão devem ser usados.

Por exemplo, você pode adicionar a seguinte diretiva para ativar a compressão de arquivos HTML, CSS e JavaScript:

```bash
gzip on;
gzip_types text/plain text/css text/javascript application/javascript application/x-javascript text/xml application/xml application/xml+rss application/atom+xml image/svg+xml application/json application/x-font-ttf application/vnd.ms-fontobject application/x-font-otf;
```
Essa diretiva informa ao Nginx para compactar todos os arquivos com os tipos MIME especificados.

Você pode usar a diretiva gzip_min_length para definir o tamanho mínimo de um arquivo que deve ser comprimido. Por exemplo, você pode adicionar a seguinte diretiva para evitar que arquivos menores que 1000 bytes sejam comprimidos:

```bash
gzip_min_length 1000;
```

Você também pode usar a diretiva gzip_comp_level para definir o nível de compressão. O nível de compressão varia de 1 a 9, sendo 1 o nível mais baixo e 9 o nível mais alto. Um nível de compressão mais alto leva mais tempo para compactar o arquivo, mas reduz o tamanho do arquivo ainda mais.

## Conexão

Imagine que você está em uma loja e precisa comprar alguns itens. Você pode fazer isso de duas maneiras:

* Sem keep-alive: Você entra na loja, pega um item, sai da loja, volta para pegar outro item, sai da loja novamente, e assim por diante. Cada vez que você entra e sai da loja, você precisa passar pelo processo de abrir e fechar a porta, o que leva tempo.
* Com keep-alive: Você entra na loja, pega todos os itens que precisa e sai da loja apenas uma vez. Você mantém a porta aberta durante todo o tempo que você está dentro da loja, o que é mais rápido e eficiente.
  

No caso do keep-alive, o navegador (o cliente) mantém a conexão com o servidor (a loja) aberta por um tempo determinado. Isso significa que, se você precisar fazer várias requisições para o mesmo servidor, o navegador não precisa abrir e fechar a conexão a cada vez. Ele pode simplesmente enviar as requisições através da conexão já existente, o que é muito mais rápido.

O keep-alive é como um atalho que permite que o navegador faça várias requisições para o servidor sem precisar passar pelo processo de abrir e fechar a conexão a cada vez. Isso aumenta a performance do site, pois as requisições são processadas mais rapidamente.

Você pode configurar o tempo que a conexão deve permanecer aberta e o número máximo de requisições que podem ser feitas através dela.

## Servidor de Cache

O servidor de cache é como um "depósito" que guarda cópias de dados que são frequentemente acessados. Quando alguém pede um dado, o servidor de cache verifica se ele já está armazenado. Se estiver, ele entrega a cópia direto, sem precisar ir buscar no servidor original. Isso é muito útil para agilizar o acesso a informações que são usadas com frequência, como imagens, vídeos ou páginas web.

No Nginx, podemos configurar um servidor de cache para armazenar dados de diferentes tipos, como páginas HTML, arquivos estáticos (imagens, CSS, JavaScript) e até mesmo respostas de aplicações web.

Para configurar um servidor de cache no Nginx, você precisa definir um local para armazenar os dados em cache. Isso é feito usando a diretiva **fastcgi_cache_path** no arquivo de configuração do Nginx (nginx.conf). Essa diretiva define o caminho para o local de armazenamento, o tamanho do cache e o nome da "zona" de cache.

Por exemplo, você pode configurar um cache para armazenar dados de aplicações web usando o fastcgi_cache_path:

```bash
fastcgi_cache_path /var/cache/nginx levels=1:2 keys_zone=my_cache:10m inactive=60m;
```
Essa configuração define um cache chamado "my_cache" com um tamanho de 10MB, localizado em /var/cache/nginx. O cache é configurado com dois níveis para melhor organização e performance.

Depois de configurar o cache, você precisa definir quais requisições serão armazenadas em cache. Isso é feito usando a diretiva **fastcgi_cache** dentro de um bloco location no arquivo de configuração do Nginx.

Por exemplo, você pode configurar o cache para armazenar as respostas de uma aplicação web que está sendo executada em um servidor FastCGI:

```bash
location / {
    fastcgi_pass unix:/var/run/php-fpm.sock;
    fastcgi_index index.php;
    fastcgi_cache my_cache;
    fastcgi_cache_valid 200 302 1m;
    fastcgi_cache_key "$host$request_uri";
}
```
Essa configuração define que as respostas da aplicação web serão armazenadas em cache por 1 minuto. A chave do cache é gerada usando o nome do host e a URL da requisição.

Com essa configuração, quando uma requisição é feita para a aplicação web, o Nginx primeiro verifica se a resposta já está armazenada em cache. Se estiver, ele entrega a resposta diretamente do cache. Caso contrário, ele envia a requisição para a aplicação web, armazena a resposta em cache e a entrega para o cliente.