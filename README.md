# 1. Descrição

<p>Pode ser bem chato ter que digitar <b>ssh</b> toda vez que for conectar em uma máquina, ou até mesmo, criar um script para cada máquina separadamente.</p>
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
Com o passo <i>3.1</i> concluído com sucesso, agora é deixar o script acessível a ser executado de qualquer lugar da sua máquina. Para isso, é preciso modificar o lugar do script. É só executar os seguintes comandos

Dar permissão de execução para o <i>conn</i>:
   

    chmod +x conn

Mover para a pasta <i>/usr/local/bin</i>:

    cp conn /usr/local/bin/

## 4. Properties
50%  já foi feito, agora é a parte da configuração do properties. O properties é onde vai ser colocado as informações.