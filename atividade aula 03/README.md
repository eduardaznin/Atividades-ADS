Análise dos estilos Monolito e Distribuido.

MONOLITO: Toda a aplicação é desenvolvida e mantida em uma única unidade. Todos os módulos do sistema rodam no mesmo processo e compartilham os memsos recursos, como banco de dados por exemplo. Elas se comunicam por chamadas de função diretas dentro do prórpio código. 
Um uso comum de monolito é em e-commerces de lojas pequenas e também sites acadêmicos, a vantagem do MONOLITO é que ele é "simplista" o que torna ele fácil de desenvolver, de testar e também é mais barato de se manter e criar.
Porém sua desvantagem vem com o tempo, conforme o sistema vai crescendo a necessidade de organizar melhor o código vira extrema para que você não precise dar deploy na aplicação inteira toda vez que quiser alterar algo específico.

DISTRIBUIDO: O sistema é dividido em múltiplos componentes independentes que rodam em máquinas diferentes e se comunicam em si pela rede, como data centers. 
Os usos comuns do estilo distribuido são aplicativos com computação em nuvem, como o Google Cloud e também serviços de streaming como a netflix. Bancos e sistemas de pagamento também utilizam esse estilo.
A vantagem é justamente poder distribuir o trabalho entre várias máquinas, podendo ser criados vários servidores e também caso alguma máquina falhe o sistema continua funcionando normalmente através das outras máquinas.
A maior desvantagem é que o estilo é extremamente dependente da rede para funcionar e isso pode causar lentidão e complicação de comunicação entre as máquinas dependendo de como está o sinal, e como é um sistema muito grande que envolve muitos servidores e máquinas, a manutenção dele também é mais complexo.
