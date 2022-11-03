# Padr-o-de-projeto
Padrão criacional - Singleton

Criacional – o padrão de projeto Singleton
O padrão de projeto Singleton é um padrão criacional, cujo objetivo é criar apenas uma instância de uma classe e fornecer apenas um ponto global de acesso àquele objeto. Um exemplo comumente usado dessa classe em Java é o calendário, onde você não pode fazer uma instância daquela classe. Ele também usa seu próprio método getInstance()para obter o objeto a ser usado.
Uma classe usando o padrão de projeto Singleton incluirá:
1.	Uma variável estática privada, que contém a única instância da classe.
2.	Um construtor privado, de modo a não ser possível instanciá-la de qualquer outro lugar.
3.	Um método estático público, para retornar a instância única da classe.
Há muitas implementações diferentes do padrão Singleton. Hoje, examinarei as implementações:
1. Instanciação ávida
2. Instanciação preguiçosa
3. Instanciação thread-safe
A ávida (Eager)
Esse tipo de instanciação acontece durante o carregamento da classe, já que a instância da variável acontece fora de qualquer método. Isso impõe uma desvantagem substancial se essa classe não for usada pela aplicação do client. O plano de contingência, se essa classe não for usada, é a instanciação preguiçosa.
A preguiçosa (Lazy)
Não há muita diferença com relação à implementação acima. As principais diferenças estão na variável estática, que inicialmente é declarada como null (nula), e no fato de que ela é instanciada apenas dentro do método getInstance() se e somente se a variável de instância permanecer null (nula) no momento da verificação.
Isso conserta um problema, mas ainda existe outro. E se dois clients diferentes acessarem a classe Singleton ao mesmo tempo? Bem, elas verificarão se a instância está null ao mesmo tempo, verão que isso é verdade e criarão duas instâncias da classe para cada solicitação feita pelos dois clients. Para resolver isso, a instanciação Thread Safe deve ser implementada.
A segurança (da thread) é fundamental
Em Java, a palavra-chave synchronized é usada nos métodos ou nos objetos para implementar a segurança das threads, de modo que apenas uma thread acesse um recurso específico em determinado momento. A instanciação da classe é colocada dentro de um bloco synchronized para que o método somente possa ser acessado por um client de cada vez.
	
A sobrecarga de um método synchronized é alta, reduzindo o desempenho de toda a operação.
Por exemplo, se a variável de instância já tiver sido instanciada, cada vez que algum client acessar o método getInstance(), o método synchronized é executado e há uma queda de desempenho. Isso acontece apenas para verificar se o valor da variável instance é null. Se descobrir que é, ele sai do método.
Para reduzir essa sobrecarga, é usado o double locking. A verificação é usada antes do método synchronized também. Somente se o valor for null o método synchronized é executado.

