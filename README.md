# Requisitos - Projeto: Sistema Web de Concessionária de Veículos

## Grupo

Bruno Vinicius Carvalho de Alencar\
Felipe de Arena Abreu Ramos Figueiredo\
João Victor Mesquita de Moraes Toledo\
Lucas da Silva Lima\
Rafael de Araujo Moreira

Divisão de tarefas:

- Bruno Vinicius Carvalho de Alencar 
(Responsável pelo formatação dos requisitos para markdown)

- Felipe de Arena Abreu Ramos Figueiredo
(Responsável pelo formatação dos requisitos para markdown)

- João Victor Mesquita de Moraes Toledo
(Responsável pelo levantamento dos critérios de qualidade e priorização)

- Lucas da Silva Lima
(Responsável pelo levantamento dos requisitos funcionais e não funcionais)

- Rafael de Araujo Moreira
(Responsável pelo levantamento dos demais requisitos, casos de teste e aceitabilidade)

## Descrição Breve do Projeto
O sistema será desenvolvido para uma concessionária online de veículos, que busca digitalizar o processo de venda, cadastro e gerenciamento de seu estoque. O objetivo é facilitar o acesso dos clientes às informações detalhadas dos carros disponíveis, além de oferecer ferramentas para que administradores e vendedores possam gerenciar os itens (cadastro, edição e exclusão) de forma simples, segura e eficiente.

## Principais Atores

Usuários Cadastrados: clientes que possuem conta no sistema, podendo cadastrar e gerenciar os veículos que anunciaram.

Administradores/Gerentes: responsáveis pelo controle do sistema, podendo cadastrar, editar e excluir qualquer veículo, além de monitorar atividades e manter a organização do estoque.

Funcionários da Concessionária: equipe que auxilia na manutenção dos anúncios e no atendimento aos clientes.

Fornecedores/Parceiros: empresas ou pessoas que fornecem veículos para a concessionária anunciar e vender.

# Requisitos Funcionais

## RF-001: Visualização e listagem de itens

Descrição:
O sistema deve permitir que o usuário tenha acesso à todo o estoque de veículos disponíveis para venda pela concessionária na página inicial (home) do sistema.

### Critério de aceitação:
O sistema deve redirecionar o usuário à página home assim que o usuário acessar a URL do sistema, onde irá visualizar toda a listagem de carros e itens cadastrados pela loja.

### Critério de aceitabilidade:

- A listagem deve exibir somente veículos cadastrados e disponíveis para venda.
- Cada item da listagem deve mostrar pelo menos: foto, modelo, marca e preço.
- A listagem deve ser atualizada automaticamente quando novos itens forem cadastrados.

### Critérios de qualidade (Não-funcionais):

- Performance: A listagem inicial deve ser carregada em até 2 segundos após acessar a URL.
- Usabilidade: A página inicial deve ser responsiva, adaptando-se a diferentes tamanhos de tela.
- Confiabilidade: O sistema deve garantir que os itens exibidos sejam atualizados em tempo real.

### Rastreabilidade:
- Origem: Solicitação do cliente (HU-01). 
- Dependência: RF-003 (Cadastro de novos itens). 
- Casos de Teste: CT-001 (Carregar listagem).

### Priorização: Must Have
Justificativa: Sem a listagem de itens na página inicial, o usuário não terá acesso ao estoque, tornando o sistema inviável.

### Testabilidade:
Teste funcional automatizado verificando se a listagem carrega itens cadastrados em até 2 segundos.

## RF-002: Acesso à página de detalhes de cada item

Descrição:
O sistema deve permitir que o usuário possa ver todas as informações disponíveis sobre um determinado veículo em uma página de detalhes, para cada veículo.

### Critério de aceitação:
Ao clicar sobre o card com imagem dos itens na listagem, o usuário é redirecionado a uma outra página onde serão listadas todas as demais informações referentes ao produto.**

### Critério de aceitabilidade:

- A página de detalhes deve exibir obrigatoriamente: foto, modelo, marca, ano, quilometragem, preço e descrição.
- O usuário não deve conseguir editar ou excluir informações a partir da página de detalhes.
- Informações sensíveis ou restritas (como dados internos da concessionária) não devem ser exibidas ao público.

### Critérios de qualidade (Não-funcionais):

- Performance: A transição da listagem para a página de detalhes deve ocorrer em até 2 segundos.
- Usabilidade: A página de detalhes deve ser clara e organizada, exibindo informações completas do veículo.
- Disponibilidade: O sistema deve estar acessível 99,5% do tempo em horário comercial.

### Rastreabilidade:
- Origem: Solicitação do cliente (HU-02).
- Dependência: RF-001 (Listagem).
- Casos de Teste: CT-002 (Acessar detalhes).

### Priorização: Must Have
Justificativa: Essencial para que o cliente visualize informações detalhadas antes de decidir pela compra.

### Testabilidade:
Testes de interface validando se todos os campos obrigatórios do veículo são exibidos corretamente.

## RF-003: Cadastro de novos itens

Descrição:
O sistema deve permitir que o usuário com cadastro e o usuário com permissão administrativa possa cadastrar um item no estoque disponível para venda da concessionária.

### Critério de aceitação:

- O usuário poderá cadastrar novos itens apenas se estiver logado no sistema ou for um usuário administrador.
- Ao clicar no botão “Cadastrar veículo”, o usuário é redirecionado para uma página com um formulário com os dados do cadastro.
- Ao clicar no botão “Salvar”, é exibido uma mensagem de “Cadastrado com sucesso” e o usuário é redirecionado de volta à página home com a listagem de veículos.

### Critério de aceitabilidade:

- Todos os campos obrigatórios (modelo, marca, ano, preço, quilometragem) devem ser preenchidos.
- O preço e a quilometragem não podem ser valores negativos.
- O ano do veículo não pode ser maior que o ano atual.
- Fotos do veículo devem estar em formato JPG ou PNG, com tamanho máximo de 5MB.

### Critérios de qualidade (Não-funcionais):

- Segurança: Apenas usuários logados ou administradores poderão cadastrar itens.
- Performance: O cadastro deve ser processado em até 3 segundos.
- Usabilidade: O formulário deve validar os dados obrigatórios antes do envio.

### Rastreabilidade:

- Origem: Solicitação do administrador (HU-03).
- Dependência: RF-008 (Login e Senha).
- Casos de Teste: CT-003 (Cadastro válido), CT-004 (Cadastro inválido).

### Priorização:
Justificativa: Fundamental para manter o estoque atualizado e disponível para visualização.

### Testabilidade:
Testes automatizados com dados válidos/inválidos e validação de mensagens de erro.

## RF-004: Edição de itens cadastrados

Descrição:
O sistema deve permitir que o usuário com cadastro possa editar os itens cadastrados por ele. Ao passo que o usuário com permissão administrativa poderá  editar as informações de qualquer item, cadastrados por ele ou terceiros.

### Critérios de aceitação:

- O usuário poderá editar itens apenas se estiver logado no sistema ou for um usuário administrador.
- Ao clicar no botão “Editar veículo”, o usuário é redirecionado para uma página com um formulário com os dados já existentes do produto.
- Ao clicar no botão “Salvar”, é exibido uma mensagem de “Editado com sucesso” e o usuário é redirecionado de volta à página home com a listagem de veículos

### Critério de aceitabilidade:

- Somente usuários logados podem editar os itens.
- O sistema deve validar novamente os dados editados (ex.: não permitir ano inválido ou preço negativo).
- As alterações devem ser registradas em log, incluindo usuário responsável e data/hora da edição.

### Critérios de qualidade (Não-funcionais):

- Segurança: Somente usuários logados ou administradores poderão editar itens.
- Performance: A edição deve ser concluída em até 3 segundos.
- Usabilidade: O formulário de edição deve carregar os dados já cadastrados corretamente.

### Rastreabilidade:

- Origem: Solicitação do usuário (HU-04).
- Dependência: RF-003 (Cadastro de itens).
- Casos de Teste: CT-005 (Edição válida), CT-006 (Edição inválida).

### Priorização: Should Have
Justificativa: Importante para manter informações atualizadas, mas o sistema pode funcionar inicialmente apenas com cadastro e listagem.

### Testabilidade: 
Testes funcionais garantindo que apenas usuários autorizados consigam editar e que os dados sejam atualizados corretamente.

## RF-005: Exclusão de itens

Descrição:
O sistema deve permitir que o usuário com cadastro possa excluir os itens que foram cadastrados por ele. Ao passo que o usuário com permissão administrativa poderá excluir qualquer item, cadastrado por ele ou terceiros.

### Critérios de aceitação:

- O usuário poderá excluir itens apenas se estiver logado no sistema ou for um usuário administrador.
- Ao clicar no botão “Excluir veículo”, o usuário é redirecionado para uma página com a confirmação.
- Ao clicar no botão “Sim, tenho certeza”, é exibido uma mensagem de “Excluído com sucesso” e o usuário é redirecionado de volta à página home com a listagem de veículos.

### Critério de aceitabilidade:

- Somente usuários logados podem excluir itens.
- Antes da exclusão, deve haver uma confirmação explícita do usuário.
- O sistema deve registrar em log os itens excluídos, incluindo usuário responsável e data/hora.
Um item excluído não deve mais aparecer na listagem pública.

### Critérios de qualidade (Não-funcionais):

- Segurança: Apenas usuários logados ou administradores poderão excluir itens.
- Usabilidade: A confirmação de exclusão deve ser clara e evitar exclusões acidentais.
- Confiabilidade: O sistema deve registrar o histórico de exclusões para auditoria.

### Rastreabilidade:

- Origem: Solicitação do usuário (HU-05).
- Dependência: RF-003 (Cadastro de itens).
- Casos de Teste: CT-007 (Exclusão confirmada), CT-008 (Exclusão cancelada).

### Priorização: Should Have
Justificativa: Necessário para controle do estoque, mas pode ser implementado após cadastro e listagem.

### Testabilidade:
Testes de confirmação para exclusão e verificação de remoção do item da listagem.

## RF-006: Campo de busca

Descrição:
O sistema deve exibir um campo de busca que permitirá ao usuário buscar, dentre os itens disponíveis no estoque, por palavras-chaves como modelo do veículo, ano, marca, quilometragem e outros.

### Critério de aceitação:
Ao clicar no campo de busca no topo da página home , deverá ser selecionado, e , ao inserir a palavra-chave e clicar no ícone de lupa, sua página será recarregada com os itens correspondentes.

### Critério de aceitabilidade:

-A busca deve aceitar pelo menos: modelo, marca, ano e quilometragem como parâmetros.
-Resultados irrelevantes ou fora dos critérios não devem ser exibidos.
-Caso não haja resultados, o sistema deve exibir a mensagem “Nenhum veículo encontrado”.

### Critérios de qualidade (Não-funcionais):

- Performance: A busca deve retornar os resultados em até 2 segundos.
- Usabilidade: Deve permitir filtros como modelo, ano, marca e quilometragem.
- Confiabilidade: Os resultados exibidos devem corresponder exatamente à palavra-chave digitada.

### Rastreabilidade:

- Origem: Solicitação do cliente (HU-06).
- Dependência: RF-001 (Listagem).
- Casos de Teste: CT-009 (Busca com resultados), CT-010 (Busca sem resultados).

**Priorização:** Must Have
Justificativa: A busca melhora a experiência do usuário e facilita encontrar veículos específicos no estoque.

### Testabilidade:
 Testes de busca com diferentes palavras-chave, validando tempo de resposta e precisão dos resultados.

## RF-007: Acesso à serviços

Descrição:
Qualquer usuário poderá ter acesso à página de listagem dos itens e demais serviços, exceto cadastro, edição e exclusão dos produtos disponíveis em estoque.

### Critério de aceitação:
O usuário que não estiver no grupo com as permissões de administrador do sistema, só poderá cadastrar novos itens, além de editar e excluir itens cadastrados por ele.

### Critério de aceitabilidade:

- Usuários não logados devem ter acesso apenas à listagem de itens e serviços informativos.
- Apenas usuários cadastrados podem incluir, editar ou excluir itens.
- Usuários comuns só podem gerenciar itens cadastrados por eles mesmos.
- Administradores podem gerenciar qualquer item do sistema.

### Critérios de qualidade (Não-funcionais):

- Segurança: Usuários sem permissão não podem acessar cadastro, edição ou exclusão.
- Usabilidade: A interface deve indicar claramente quais funcionalidades estão disponíveis para cada tipo de usuário.
- Disponibilidade: O acesso aos serviços deve estar disponível 99,5% do tempo em horário comercial.

### Rastreabilidade:

Origem: Regras de negócio (HU-07).
Dependência: RF-008 (Login e permissões).
Casos de Teste: CT-011 (Acesso de usuário comum), CT-012 (Acesso de administrador).

### Priorização:
Justificativa: Facilita a navegação de usuários comuns, mas não é essencial para a primeira versão.

### Testabilidade:
Testes de permissão para validar restrições de acesso entre usuários comuns e administradores.

## RF-008: Página de acesso com login e senha

Descrição:
O usuário poderá ter acesso ao sistema com login e senha caso seja cadastrado ou fazer o cadastro caso seja seu primeiro acesso.

### Critérios de aceitação:

- O usuário conseguirá acessar a listagem de produtos sem possuir um login e senha.
- Caso deseje cadastrar uma conta, deve clicar no ícone de “Registre-se” ao lado do campo de busca, onde será redirecionado para uma página de cadastro com formulário para informações cadastrais.
- Ao clicar no botão “Concluir” no canto inferior do formulário, será redirecionado para a página de login.

### Critério de aceitabilidade:

- O login deve ser feito com e-mail e senha válidos previamente cadastrados.
- Senhas devem ter no mínimo 8 caracteres, incluindo letras e números.
- O sistema deve bloquear a conta após 5 tentativas de login inválidas consecutivas.
- O cadastro deve exigir dados mínimos: nome completo, e-mail válido e senha forte.

### Critérios de qualidade (Não-funcionais):

- Segurança: O sistema deve criptografar senhas e proteger dados sensíveis conforme a LGPD.
- Usabilidade: O formulário de login/cadastro deve ser simples e intuitivo.
- Performance: O login deve ser processado em até 3 segundos.

### Rastreabilidade:

- Origem: Solicitação de segurança (HU-08).
- Dependência: Nenhuma.
- Casos de Teste: CT-013 (Login válido), CT-014 (Login inválido).

### Priorização: Must Have
Justificativa: Essencial para controle de permissões e segurança no sistema.

### Testabilidade:
Testes de autenticação (credenciais corretas e incorretas), validação de senhas e mensagens de erro.

# Requisitos Não Funcionais

## RNF-001: Performance e Tempo de Resposta

Descrição:
O sistema deve garantir tempos de resposta adequados para manter a fluidez da navegação.

### Critérios de Qualidade:

- A página inicial (listagem de itens) deve carregar em até 2 segundos.
- O cadastro/edição/exclusão deve ser concluído em até 3 segundos.
- O campo de busca deve retornar resultados em até 2 segundos.Tempo de login não deve ultrapassar 3 segundos.

### Rastreabilidade:
- Origem: Expectativa do cliente (NFR-01). 
- Afeta: RF-001, RF-002, RF-003, RF-006 e RF-008. 
- Casos de Teste: CT-015 (Testes de carga)

### Priorização: Must Have
Must Have (fundamental para boa experiência do usuário).

### Testabilidade:
Testes de desempenho medindo tempos de resposta com ferramentas de “stress test”.

## RNF-002: Usabilidade e Experiência do Usuário

Descrição:
O sistema deve ser simples e intuitivo para todos os tipos de usuários (clientes, vendedores e administradores).
 
### Critérios de Qualidade:

- Interface em português brasileiro com terminologia acessível.
- Operações principais (listagem e busca) acessíveis em até 2 cliques.
- Formulários de cadastro com validação e mensagens claras de erro.
- Design responsivo, compatível com desktop, tablet e celular.

### Rastreabilidade:
- Origem: Expectativa do cliente (NFR-02). 
- Afeta: Todos os RFs. 
- Casos de Teste: CT-016 (Testes de interface).

### Priorização: Must Have
Essencial para adoção do sistema.

### Testabilidade:
Avaliação com usuários reais (testes de usabilidade) e validação de acessibilidade/responsividade.

## RNF-003: Segurança e Controle de Acesso

Descrição:
O sistema deve proteger os dados dos usuários e controlar permissões de acordo com perfis de acesso.
 
### Critérios de Qualidade:

- Senhas armazenadas com criptografia segura (ex.: bcrypt).
- Autenticação obrigatória para cadastro, edição e exclusão de itens.
- A sessão expira automaticamente após 30 minutos de inatividade.
- Conformidade com a LGPD no tratamento de dados pessoais.

### Rastreabilidade:
- Origem: Regras de negócio (NFR-03). 
- Afeta: RF-003, RF-004, RF-005, RF-007, RF-008. 
- Casos de Teste: CT-017 (Login seguro), CT-018 (Permissões incorretas).

### Priorização: Must Have
Indispensável para confiabilidade e proteção.

### Testabilidade:
Testes de autenticação, criptografia de senha e simulação de acessos não autorizados.

## RNF-004: Confiabilidade e Disponibilidade

Descrição:
O sistema deve estar disponível de forma contínua, evitando falhas e indisponibilidades.
 
### Critérios de Qualidade:

- Disponibilidade mínima de 99,5% em horário comercial.
- Em caso de falha, o sistema deve se recuperar em até 5 minutos.
- Backups automáticos do banco de dados realizados diariamente.
- Logs de erros e atividades críticas registrados para auditoria.

### Rastreabilidade:
- Origem: Expectativa da gerência (NFR-04). 
- Afeta: Todos os RFs. 
- Casos de Teste: CT-019 (Disponibilidade em carga).

### Priorização: Should Have
Importante para a confiança do cliente.

### Testabilidade:
Testes de falha simulada e recuperação, verificação de logs e tempo de uptime.

## RNF-005: Manutenibilidade e Escalabilidade

Descrição:
O sistema deve permitir manutenção fácil e suportar crescimento de dados e usuários.

### Critérios de Qualidade:

- Código documentado seguindo boas práticas (ex.: Clean Code).
- Banco de dados deve suportar até 100.000 registros de veículos sem degradação de desempenho.
- Arquitetura modular para facilitar a adição de novas funcionalidades.
- Logs de manutenção disponíveis para equipe técnica.

### Rastreabilidade:
- Origem: Expectativa da equipe técnica (NFR-05). 
- Afeta: Estrutura geral do sistema. 
- Casos de Teste: CT-021 (Carga de dados), CT-022 (Expansão do sistema).

### Priorização: Could Have
Não é crítico no início, mas importante a médio prazo.

### Testabilidade:
Revisão de código, testes de crescimento de banco de dados e inclusão de novas funcionalidades em ambiente de homologação.


## Tabela de Priorização MoSCoW (Requisitos Funcionais)
|Priorização| Código do requisito|
|-----------|--------------------|
|Must Have  | RF-001            |
|Must Have  | RF-002            |
|Must Have  | RF-003            |
|Must Have  | RF-006            |
|Must Have  | RF-008            |
|Could Have | RF-007            |
|Should Have| RF-004            |
|Should Have| RF-005            |

## Tabela de Priorização MoSCoW (Requisitos Não Funcionais)
|Priorização| Código do requisito|
|-----------|--------------------|
|Must Have  | RNF-001            |
|Must Have  | RNF-002            |
|Must Have  | RNF-003            |
|Could Have | RNF-005            |
|Should Have| RNF-004            |
