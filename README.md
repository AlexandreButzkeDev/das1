# das1
trabalho das1
aula 06/03
 Regiões: As "Cidades" da Nuvem
O que é? São grandes áreas geográficas (como São Paulo, Tóquio ou Paris) onde a AWS tem vários prédios cheios de computadores (data centers).

Para que serve? Se você mora no Brasil, seus dados ficam na "cidade" de São Paulo para chegar mais rápido até você.

Exemplo: O jogo Fortnite tem servidores em Buenos Aires (uma "cidade" da AWS na Argentina) para os jogadores de lá terem menos lag.

2. Zonas de Disponibilidade (AZs): Os Bairros Seguros
O que é? Dentro de cada "cidade" (região), existem vários bairros isolados (AZs) com computadores.

Para que serve? Se um bairro pega fogo (falha), os outros continuam funcionando. Assim, seu jogo não para!

Exemplo: A AWS do Brasil tem 3 AZs em São Paulo – se uma falhar, as outras duas mantêm tudo online.

3. Local Zones: As Lojas de Bairro
O que é? São pequenas extensões de uma "cidade" principal, colocadas perto de lugares com muita gente.

Para que serve? Para coisas que precisam ser super-rápidas, como jogos ou vídeos ao vivo.

Exemplo: Se você mora no Chile, uma Local Zone em Santiago deixa o Netflix mais rápido para você, sem precisar buscar os dados em São Paulo.

4. Edge Locations: Os Entregadores Mais Rápidos
O que é? São mini-estações espalhadas pelo mundo, como pontos de entrega.

Para que serve? Guardar cópias de coisas populares (como um vídeo do TikTok) perto de você, para carregar em um piscar de olhos.

Exemplo: Com o 5G, seu celular se conecta a uma Edge Location perto da antena, e o vídeo chega quase instantaneamente.

Por que isso é legal?
Escalabilidade: A AWS pode aumentar ou diminuir o número de computadores conforme precisa. É como ter um exército de robôs que aparece só quando você precisa!

Economia: Você só paga pelo que usa. Se seu jogo fica vazio à noite, a AWS desliga alguns computadores e você gasta menos.

Curiosidade Maluca!
Quando a AWS quer criar uma nova "cidade" (região), ela usa computadores de outra cidade já pronta para montar tudo. É como usar peças de Lego de uma nave espacial para construir um castelo! 🚀🏰

Conclusão: A AWS é como um quebra-cabeça gigante de computadores, organizado para que tudo funcione rápido, seguro e sem gastar dinheiro à toa. E o melhor: você nem percebe, mas está usando isso tudo quando joga Fortnite ou assiste Netflix




aula 13/03 
1. Responsabilidade Compartilhada: Quem Protege o Quê?
AWS (Amazon): Cuida do castelo físico (paredes, portões, servidores).

Exemplo: Garante que os computadores (hardware) não quebrem e a eletricidade nunca falte.

Você (Usuário): Cuida do interior do castelo (sistemas, senhas, aplicativos).

Exemplo: Se você instala um sistema operacional (como Linux) em um servidor da AWS, você é responsável por atualizá-lo e protegê-lo.

👉 Dica: Se o servidor for invadido, a culpa não é da AWS, mas sim de quem esqueceu de trancar a porta digital!

2. EC2: O Servidor Mágico na Nuvem
O que é? Um computador virtual (EC2) na AWS onde você pode instalar programas, como um servidor web (Apache).

Problema: Como acessar esse computador sem usar senhas ou chaves?

Solução Mágica (SSM Agent): A AWS coloca um "ajudante invisível" (SSM Agent) dentro do servidor. Ele cria um túnel seguro para você entrar sem expor portas perigosas (como a porta 22 do SSH).

Exemplo Prático:

Walter instalou o Apache (servidor web) em um EC2.

Usou o AWS Systems Manager para conectar ao servidor sem senha, como um passe de mágica!

Digitou o IP do servidor no navegador e... funcionou! (Apareceu "It works!").

⚠ Atenção: Expor portas como 22 (SSH) ou 80 (HTTP) diretamente na internet é perigoso! Use o Systems Manager para entrar sem riscos.

3. Roles (Funções): Os Poderes Temporários
O que é? Uma permissão temporária que você dá a um serviço (como o EC2) para fazer algo específico.

Como funciona?

Você cria uma Role (ex.: "RoleDoSystemsManager") com permissões limitadas.

Associa essa Role ao servidor EC2.

O "ajudante invisível" (SSM Agent) usa essa Role para se conectar ao Systems Manager sem precisar de senhas.

Exemplo:

Se um programador precisa de acesso total por 1 hora, ele recebe uma Role temporária. Após 1 hora, o poder some automaticamente!

🔑 Vantagem: Ninguém precisa guardar senhas ou chaves secretas. É mais seguro!

4. Princípio do Privilégio Mínimo
Regra de Ouro: Nunca dê mais permissões do que o necessário.

Exemplo: Um servidor que só exibe um site não precisa de acesso ao banco de dados.

Na AWS: Use Roles para controlar exatamente o que cada serviço pode fazer.

Curiosidade Maluca!
O SSM Agent é como um teleporte seguro. Ele conecta o seu computador ao servidor EC2 por um caminho secreto dentro da própria AWS, sem usar a internet aberta. Assim, os piratas digitais nunca descobrem a entrada! 🚪✨

Conclusão:

AWS Systems Manager + Roles = Segurança sem Complicação

Nunca exponha portas desnecessárias (22, 80) diretamente na internet.

Use Roles para dar permissões temporárias e sempre siga o privilégio mínimo.

Assim, seu castelo na nuvem fica protegido, e você pode jogar Minecraft ou hospedar sites sem medo de invasores! 🏰🛡




aula 17/03
1. S3 Buckets: Os "Baús" Secretos da Nuvem
O que é? Um bucket é como um baú único com um nome que ninguém mais no mundo pode ter (ex.: meu-bau-secreto-2024).

Para que serve? Guardar arquivos (fotos, vídeos, documentos) ou até hospedar sites estáticos (HTML, CSS).

Exemplo: Se você criar um bucket chamado fotos-da-viagem, ninguém mais poderá usar esse nome, nem em outra conta AWS!

⚠ Cuidado! Se o bucket for público, qualquer pessoa pode ver seu conteúdo. Por isso, nunca deixe um bucket público sem necessidade!

2. Hospedagem de Sites Estáticos: Sua Página na Nuvem
Como funciona?

Crie um bucket e ative a opção "Hospedagem de site estático".

Faça upload dos arquivos do site (ex.: index.html).

Acesse o site pelo link único do S3 (ex.: http://meu-bucket.s3-website-regiao.amazonaws.com).

👉 Exemplo do Walter:

Ele criou um bucket, subiu um arquivo index.html e digitou o link no navegador. Apareceu "It works!" 🎉

Dica: Para usar um domínio personalizado (ex.: www.meusite.com), basta apontá-lo para o link do S3.

3. Pastas no S3: Uma Ilusão Organizada
O que são? As "pastas" no S3 são prefixos (ex.: fotos/verao/) para organizar arquivos, mas não existem de verdade.

Como assim? O S3 é um sistema flat (plano): todos os arquivos ficam "soltos", mas a AWS mostra pastas para facilitar sua vida.

Exemplo: O arquivo fotos/verao/praia.jpg é apenas uma chave única, não uma pasta real!

4. Segurança: Cuidado com os "Baús" Públicos!
Risco: Se um bucket estiver público, hackers podem procurar buckets com nomes óbvios (ex.: dados-clientes-2024) e roubar informações.

Solução:

Use permissões mínimas (só libere acesso a quem precisa).

Nunca exponha portas como 80 (HTTP) ou 22 (SSH) diretamente para a internet.

⚠ Ataque comum: Hackers usam scripts para "adivinhar" nomes de buckets públicos e explorá-los.

5. Como o S3 Guarda Seus Tesouros?
Mágica da AWS: Quando você sobe um arquivo, o S3 o divide em pedacinhos e espalha em vários discos pelo mundo.

Vantagem: Se um disco quebra, seus arquivos ainda estão seguros!

Para baixar: O S3 reconstrói tudo automaticamente, como um quebra-cabeça perfeito.

Curiosidade Maluca!
O S3 é tão poderoso que armazena trilhões de objetos (arquivos) e aguenta milhões de requisições por segundo! É como ter um exército de robôs trabalhando 24/7 para proteger seus dados. 🤖🔒

Conclusão:

Buckets são únicos: Escolha nomes criativos para evitar exposição.

Sites estáticos: Use o S3 para hospedar páginas simples sem servidores.

Pastas são "fingidas": Organize com prefixos, mas lembre-se: é tudo plano!

Segurança em primeiro lugar: Nunca deixe buckets públicos sem motivo!

Assim, seu "baú" na nuvem fica cheio de tesouros, mas longe de piratas! 🏴☠💎




aula 20/03
1. AWS Outposts: O "Castelo Portátil"
O que é? Um servidor mágico da AWS que você pode colocar dentro da sua empresa (como um mini-castelo).

Para que serve? Rodar serviços da nuvem (como S3, EC2) localmente, mas conectado à nuvem da AWS.

Exemplo: É como ter um teleporte que traz parte da nuvem para perto de você!

⚠ Diferença:

Na nuvem, o S3 é infinito (você guarda quantos tesouros quiser!).

No Outposts, o S3 tem limite de espaço (como um baú físico que enche). Se acabar, precisa comprar mais baús (discos)!

2. Por que Usar o Outposts?
Vantagem: Mesmo dentro da sua empresa, você usa serviços da AWS (EC2, S3) e ganha:

Gerenciamento fácil: Se o servidor quebrar, a AWS troca como mágica! ✨

Integração com a nuvem: Dá para replicar dados para a nuvem automaticamente.

Desvantagem: Custa mais caro que um servidor comum (ex.: Dell), mas vem com superpoderes da AWS!

3. S3 no Outposts: O Baú que Não Cresce Sozinho
Na nuvem: O S3 é elástico (expande automaticamente, como um baú sem fundo).

No Outposts: O S3 é limitado pelo hardware físico. Se encher, você precisa comprar mais discos! 💾

Exemplo: Se você pedir 1TB de S3 no Outposts, a AWS entrega um HD de 1TB. Na nuvem, ela "inventa" espaço infinito!

4. Tipos de "Baús" (Storage Classes)
S3 Standard: Para tesouros acessados frequentemente (mais caro).

S3 Glacier: Para tesouros esquecidos (mais barato, mas demora para recuperar).

Curiosidade: Alguns clientes não conseguem pagar para mover dados entre classes (é muito caro!).

5. Hardware: Processadores Mágicos
Graviton: Processador da AWS (como um robô eficiente que gasta menos energia).

Intel: Processador tradicional (como um cavalo veloz e conhecido).

Escolha: Depende do que você precisa (velocidade, custo, compatibilidade)!

Curiosidade Maluca!
O AWS Outposts é tão poderoso que pode ser instalado até em um banheiro virando data center! 🚽🔧 (Brincadeira... mas a AWS realmente entrega o servidor onde você quiser!)

Conclusão:

Outposts é a ponte entre a nuvem e sua empresa (ideal para quem precisa de controle local + serviços AWS).

S3 na nuvem é infinito, mas no Outposts tem limite físico.

Escolha storage classes com sabedoria para não gastar rios de dinheiro!



aula 23/03
1. GitHub: Sua Prateleira de Brinquedos
O problema: Alguns alunos tinham "prateleiras" (repositórios) vazias ou com brinquedos velhos (sem commits recentes).

Dica do Walter: Coloque pelo menos um "Hello World" (um brinquedo simples) para mostrar que a prateleira está sendo usada!

"Bicho Preguiça" 🦥: Seu repositório está desatualizado? Atualize! Senão, vira um "bicho preguiça" digital.

2. S3 Bucket: O Baú que Pode Ser Público ou Secreto
Padrão: Todo bucket S3 começa trancado (privado). Só o dono tem a chave!

Como abrir o baú?

Opção arriscada: Tornar o bucket público (qualquer um vê seus tesouros!).

Opção segura: Usar URLs pré-assinadas (chaves temporárias) para dar acesso por minutos ou horas.

Exemplo do Walter:

Ele gerou uma URL temporária para a "foto da mãe" (um arquivo privado).

Quem recebeu a URL conseguiu ver a foto só por 10 minutos! Depois, a chave "expirou".

⚠️ Cuidado com CORS: É como construir uma ponte entre castelos (domínios). Se a ponte estiver mal configurada, ninguém compartilha recursos!

3. Escolhendo o Melhor Lugar para o Baú (Regiões)
Onde guardar? A região do S3 afeta:

Custo 💰: Alguns lugares são mais caros que outros.

Velocidade ⚡: Escolha uma região perto dos usuários (ex.: Brasil para brasileiros).

Leis 🏛️: Países têm regras diferentes para dados (ex.: GDPR na Europa).

👉 Dica: O S3 é regional (seu baú fica em um lugar específico do mundo). Escolha com sabedoria!

Curiosidade Maluca!
O S3 pode guardar até 5 TB em um único arquivo – é como enfiar um elefante inteiro dentro do baú! 🐘📦 E as URLs pré-assinadas são tão seguras que nem o melhor hacker do mundo consegue quebrá-las... se você configurar direitinho!

Conclusão:

GitHub: Mantenha seus repositórios atualizados (não seja um "bicho preguiça"!).

S3 Bucket: Nunca deixe público sem necessidade. Use URLs pré-assinadas para acesso controlado!

Regiões: Escolha com base em custo, velocidade e leis.
