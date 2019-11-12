# 1. Descrição

<p>Pode ser bem chato ter que digitar <b>ssh user@host</b> toda vez que for conectar em uma máquina, ou até mesmo, criar um script para cada máquina.</p>
Então, a ideia desse projeto é <i>centralizar</i> e <i>automatizar</i> a conexão nessas máquinas remotas, afim de melhorar a produtividade do seu dia a dia.


# 2. Requisitos

<ul>
<li> Linux Distros 
<li> sshpass
</ul>


# 3. SETUP
<p>O projeto se baseia em 2 arquivos o <b><i>conn</i></b> e <b><i>properties</i></b>.</p>
<p>O conn é o script que faz toda a mágica e o properties é onde vocês vão colocar as informações das máquinas para conexão.</p>

## 3.1. SETUP CONN

<p>A única configuração que precisa fazer no <i>script</i> é o caminho de onde está o <i>properties</i>.
A configuração é alterar o valor da variável <b><i>propertiesPATH</i></b>. Ela é o caminho do properties, essa variável é o core do script é importante não errar esse passo.</p>
<p>Segue um exemplo de de/para:</p>
<ul>
<li> [De] Valor Default:
</ul>

    propertiesPATH="/example/path/properties"

 <ul>
 <li> [Para] Valor Modificado:
 </ul>

    propertiesPATH="/l/disk0/scripts/ambientes/properties"

## 3.2. Modificar o caminho do script
<p>Com o passo <i>3.1</i> concluído com sucesso, agora é deixar o script acessível a ser executado de qualquer lugar da sua máquina. Para isso, é preciso modificar o lugar do script. É só executar os seguintes comandos</p>

<p>Dar permissão de execução para o <i>conn</i>:</p>
   

    chmod +x conn

<p>Mover para a pasta <i>/usr/local/bin</i>:</p>

    cp conn /usr/local/bin/



# 4. Properties
<p>50%  já foi feito, agora é a parte da configuração do properties. O properties é onde vai ser colocado as informações.
Quando você abrir o properties a primeira vez, ele vai ter esse valor:</p>

    ID = ${ID}
    HOST = ${HOST}
    USER = ${USER}
    PASS = ${PASS}
    PORT = ${PORT}
    SERVICES = ${SERVICES}
## 4.1. ID
>   OBRIGATÓRIO

<p>O ID nada mais que o identificador da máquina. Esse cara é livre da sua escolha.
O ID vai ser passado na hora de executar o script. Então, a conexão a máquina depende desse ID</p>
<p>Segue um exemplo:</p>
Suponhamos que você queira acessar a máquina de produção, então um ID lógico pra essa máquina é <b>prod</b>. Assim, quando você for se conectar nessa máquina você usará esse ID.</p>
<center><b><p>OBS: Na seção 5, é explicado com mais detalhes como é executado o script.</b></p></center>

## 4.1. HOST
>   OBRIGATÓRIO

O <i>HOST</i> pode ser preechido tanto pelo IP (127.0.0.1) quanto o HOSTNAME (localhost)da máquina que você deseja acessar. 

## 4.2. USER
>   OBRIGATÓRIO

O <i>USER</i> é o usuário da máquina que você deseja acessar. Exemplo: nicolas

## 4.3. PASS
>   OBRIGATÓRIO

O <i>PASS</i> é a senha do usuário que você deseja usar para acessar a máquina. Exemplo: usuario

## 4.4. PORT 
>   OBRIGATÓRIO

<p>A <i>PORT</i> é a porta da máquina que você deseja acessar.</p>
<p>Se a máquina não tem uma porta especifica, então pode preencher com 22 que é sucesso</p>

## 4.5. SERVICES
>   OPCIONAL
<p>Essa chave é pra você descrever o que tem nessa máquina que é útil pra você. Por exemplo: Eu logo todos os dias em uma máquina que é o banco de dados da minha aplicação. Então nessa chave <i>SERVICES</i> eu coloco DATABASE, assim quando eu logar, é mostrado o serviço que essa máquina me disponibiliza.</p>
<p>Esse campo é de livre escrita, então pode salvar ai tudo que for útil para o seu caso</p>
<center><b><p>OBS: Esse é o único ponto que é opcional para a conexão.</b></p></center>

## 4.6. PROPERTIES DE UMA MÁQUINA PRONTO

<p>Usando os exemplo dado em cada tópico, é possivel montar o properties de uma máquina completo, segue abaixo: </p>

    ID = prod
    HOST = localhost
    USER = nicolas
    PASS = usuario
    PORT = 22
    SERVICES = DATABASE
<br>

>  <b>CONFIGURAR MULTIPLAS MÁQUINAS:</b> Para ver como ficar um properties mais completo, com várias máquinas configuradas, veja na pasta <b>"demonstração"</b> o arquivo <i>properties_example</i>