### Informações importantes Ruby
RVM - Ruby Version Manage
https://rvm.io

IRB - Interactive Ruby Shell é um REPL

PRY é uma alternativa ao irb padrão
gem install pry

Para ativar a coloração do pry no irb basta criar o arquivo .irbrc de configuração na home do usuário com as seguintes linhas:
```
require 'rubygems'
require 'pry'
Pry.start
exit
```
#### Saída padrão - STDOUT
puts

#### Entrada padrão - STDIN
gets

#### Coersão | Cast | Casting
Converte tipo de dados.
to_i -> para integer
to_f -> para float
to_s -> para string

## Estrutura condicional
if     -> testa se uma condição é verdadeira
else   -> caso contrãrio
unless -> testa se uma condição é falsa
```ruby
x = 2
if x > 1
  ....
else
  ...
end
# unless
unless x > 1
  ...
end

# case

case idade
when 0..18
  puts "De menor"
when 18..30
  puts "Boa idade"
else
  puts "Já é tio"
end

# Ternário
sexo = 'M'

sexo == 'M' ? (puts "Masculino") : (puts "Feminilo")
```

## Estrutura de repetição
#### While (enquanto)
```ruby
x = 5
while i <= x do
	puts i
end
```
#### each (cada)
```ruby
(0..5).each do |i|
  puts i
end
```

## Array / Vetor
```ruby
# criando uma array
v = [1,3,5,7,9]

# outra forma
v1 = Array.new

# add elementos
v1.push(4)
```

## Hashes
É uma lista de chave/valor
```ruby
# sintaxe
h = {"a": "15", "b": "Fulano"}
h = {"a" => "15", "b" => "Fulano"}
```
## String
A concatenação com o + gera uma nova instância na memória. Prefira utilizar a pá << para concaterar e outra opção é a interpolação utilizando #{}.
```ruby
# exemplos
# aqui gera uma nova instância na memória
# checando a referência da memória antes e depois da concatenação
a = "Nome"
b = "Sobrenome"

puts a.object_id
puts a + " " + b
puts a.object_id

# abaixo um exemplo de concatenação com a pá. Não gera uma nova instância na memória
c = "nome"
d = "sobrenome"

puts c.object_id
puts c << " " << b
puts c.object_id

# abaixo o exemplo de interpolação
e = 'nome'
f = 'sobrenome'

puts e.object_id
puts "#{e}  #{f}"
puts e.object_id
```

## Symbols
São comumente usados em Hashes e são muito usadas em situações que precisamos de um identificador imultável.
```ruby
# exemplo: Cria uma nova instâncias a cada impressão
puts "Nome".object_id
puts "Nome".object_id
puts "Nome".object_id

# exemplo: Com uso de Symbol a refência de memória não altera
puts :nome.object_id
puts :nome.object_id
puts :nome.object_id
```
## Classe
```ruby
# criar uma classe
class Pessoa
  # acoes aqui...
end

# cria um objeto
Pessoa.new

# construtor 
def initialize

end
```
### self
é o próprio objeto instânciado.
```ruby
self.object_id
```

### Variáveis de instância
As variáveis de instância podem ser identificadas pelo @ e estão disponíveis apenas para a instância
```ruby
@nome = "Nome sobrenome"
```

### Accessors
Accessors são atalhos para declaração de atributos em uma classe.

```ruby
# a delcaração abaixo nos fornece os métodos getter e setter
attr_accessor :nome

# exemplo
p1 = Pessoa.new
p1.nome = "Nome sobrenome" # setter
puts p1.nome # getter
```

### Método estático
No ruby é conhecido como método de classe e é precedido de self.
```ruby
#exemplo de método de classe
class Pessoa
  def self.nome(n)
    n
  end
end
# exemplo de como chamar o método, sem instânciar.
Pessoa.nome
```

## Módulos e Mixins
Rever a aula...

# Gems
http://rubygems.org

```ruby
gem list #gems instaladas
gem list nome_gem # pesquisa gems localmente
gem list nome_gem --remote # pesquisa gem remotamente

gem install nome_gem # instala um gem
gem install nome_gem -v xx.x.x # instala um gem de uma determinada versão
gem uninstall nome_gem # remove a gem
gem clenaup -d # remove versões anteriores de gems

# exemplos de gems
gem install cpf_utils
# importando a gem
require cpf_utils
# uso da gem cpf_utils
CpfUtils.cpf
```

Criando o arquivo Gemfile com as gems para o projeto
```ruby
source 'https://rubygems.org'
gem 'cpf_ultis'
```
#### Gems úteis
```ruby
gem 'cpf_utils' # recursos para cpf
gem 'faker' # 
gem 'lerolero' # gerador de texto tipo lorem
gem 'documentos_br'
gem 'tty-spinner' # TTY Toobox
```

# Bundler
Resolve problemas com dependência de gems. O bundler lê o arquivo Gemfile e instala todas as gems e sua dependências.
```ruby
# verifique se o bundler está instalado
gem list

# Se não tiver, instale
gem install bundler
```

# IRB
```ruby
# carregar arquivos
require_relative "nome_arquivo.rb"
# se carregado com sucesso o retorno é true
```

# Métodos úteis
.class -> verifica o tipo de dado
.inspect -> exibe mais informações
.chomp -> remove o \n da string para exibir o texto limpo.
.object_id

##### Documentação e apis Ruby
Documentação: www.ruby-lang.org/pt/documentation

Standard Library: / Core: http://ruby-doc.org

Api Dock: https://apidoc.com/ruby

# Rails
##### Documentação e apis Rails
Rails Guides: https://guides.rubyonrails.org

Api: http://api.rubyonrails.org

Api Dock: https://apidock.com/rails

no console execute rails para obter todas as opções do comando

### Criando a aplicação e opcionalmente configurando o banco de dados

```ruby
# criando a aplicação com a versão definida.
rails _5.2_ new cripto_wallet

# criando a aplicação
rails new cripto_wallet

#criando a aplicação com versão definida com bando de dados
rails _5.2_ new cripto_wallet --database=mysql

# criando a aplicação com banco de dados
rails new cripto_wallet --database=mysql
```
#### Banco de Dados
Arquivo de configuração fica localizado dentro de config/database.yml

Pesquisar na internet por database.yml mysql

#### Prototipagem
- wireframes (rascunho)
  - Adobe XD
  - Balsamiq
  - Mock Flow
  - Figma

#### Modelagem
Modelagem de banco de dados é a base para criação do banco de dados.

##### Convensão
De preferencia em escrever a estrutura MVC e nome de colunas das tabelas em English.
- Um Model deve ser escrito no singular
- 
#### Scaffold
No rails podemos gerar o CRUD através do generator scaffold.
```ruby
rails generate scaffold <modelName> <campo:tipo>

# Exemplo
rails generate scaffold Coin description:string

# ou 
rails g scaffold Coin description:string
```

#### Migrations
###### Rails dbconsole
Console de acesso ao banco  de dados

###### Rails Tasks
São tarefas pré definidas para geração de scripts.

Listar todas as Tasks disponíveis.
```ruby
rails -T
```

Algumas operações com banco de dados.
```ruby
# criar um banco de dados
rails db:create

# apaga um banco de dados
rails db:drop

# executar as migrations
rails db:migrate

# desfazer a execução das migrates
rails db:rollback
``` 
