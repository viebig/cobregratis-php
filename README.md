# PHP Wrapper para a API do Cobre Grátis (adicionado suporte a composer)

Essa biblioteca é um conjunto de classes em PHP para acessar as informações do [Cobre Grátis](http://cobregratis.com.br) através da [API](https://github.com/CobreGratis/cobregratis-api).

Todas as classes são herdadas do PHP ActiveResouce. Veja a documentação do [PHP ActiveResouce](https://github.com/lux/phpactiveresource) para mais informações.

## Instalando

### Via composer

    composer require "viebig/cobregratis": "dev-master"

### Via git

    git clone https://github.com/CobreGratis/cobregratis-php.git

### Configurando seu token

```php
require 'lib/CobreGratis.php';

$bank_billet = new BankBillet();
$bank_billet->user = "seu_token";
$bank_billet->password = "X";
```

## Uso

```php
# criar um boleto
$bank_billet = new BankBillet(array(
  'amount' => 230.50,
  'expire_at' => '2015-07-22',
  'name' => 'Rafael Lima'
));
$bank_billet->user = "seu_token";
$bank_billet->password = "X";
$bank_billet->save();

# listar todos os boletos
$bank_billet->extra_params = "?page=1";
$bank_billets = $bank_billet->find('all');
if($bank_billets->errno) {
  print "$bank_billets->error\n";
} else {
  foreach($bank_billets as $bank_billet) {
    print "Nosso Número: $bank_billet->our_number\n";
    print "Vencimento: $bank_billet->expire_at\n";
    print "Valor: $bank_billet->amount\n";
    print "Sacado: $bank_billet->name\n";
    print "URL: $bank_billet->external_link\n";
    print "=================================\n";
  }
}
```

Veja os exemplos:
[bank_billet.php](https://github.com/CobreGratis/cobregratis-php/blob/master/examples/bank_billet.php)
[customer.php](https://github.com/CobreGratis/cobregratis-php/blob/master/examples/customer.php)
[bank_billet_subscription.php](https://github.com/CobreGratis/cobregratis-php/blob/master/examples/bank_billet_subscription.php)

## Licença

Esse código é livre para ser usado dentro dos termos da licença [MIT license](http://www.opensource.org/licenses/mit-license.php).

## Bugs, Issues, Agradecimentos, etc

Comentários são bem-vindos. Envie seu feedback através do [issue tracker do GitHub](http://github.com/CobreGratis/cobregratis-php/issues)

## Autor

[**Rafael Lima**](http://github.com/rafaelp) trabalhando na [CobreGratis](http://bielsystems.com.br)

Blog: [http://rafael.adm.br](http://rafael.adm.br)

Twitter: [http://twitter.com/rafaelp](http://twitter.com/rafaelp)

## Composer

[**Guilherme Viebig**](http://github.com/viebig) - [BitLoom](http://www.bitloom.net) - [Ponki](http://www.ponki.com.br)