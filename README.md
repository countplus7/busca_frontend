# Sistema Imobiliário Litoral

Um sistema completo para gerenciamento de imobiliárias, corretores e proprietários de imóveis, desenvolvido com React no front-end e Node.js/Express no back-end.

## Características

- Autenticação de usuários com diferentes níveis de acesso
- Cadastro e gerenciamento de imóveis
- Filtros de busca avançados
- Painel administrativo para gerenciar usuários, imóveis e notícias
- Formulários para cadastro de profissionais e particulares
- Banner rotativo com imóveis em destaque
- Área de notícias do mercado imobiliário

## Requisitos

- Node.js 18.x ou superior
- NPM ou Yarn

## Banco de Dados

O sistema utiliza um banco de dados MongoDB em memória (mongodb-memory-server), que é criado temporariamente quando o servidor é iniciado. Isso significa que:

- Não é necessário instalar MongoDB separadamente
- O banco de dados é recriado do zero cada vez que o servidor é reiniciado
- Dados são populados automaticamente no início através de scripts de seed
- Ideal para desenvolvimento e demonstração

## Instalação e Configuração

### Front-end

1. Clone o repositório:
```bash
git clone [url_do_repositório]
cd [nome_da_pasta]
```

2. Instale as dependências:
```bash
npm install
```

3. Inicie o servidor de desenvolvimento:
```bash
npm run dev
```

O front-end estará disponível em http://localhost:5173

### Back-end

1. Navegue até a pasta do servidor:
```bash
cd server
```

2. Instale as dependências:
```bash
npm install
```

3. Crie um arquivo `.env` na raiz da pasta server com as seguintes variáveis (opcional, valores padrão serão usados se não fornecido):
```
PORT=5000
JWT_SECRET=sua_chave_secreta_aqui
JWT_EXPIRES_IN=7d
```

4. Inicie o servidor:
```bash
npm run dev
```

O back-end estará disponível em http://localhost:5000

### Usuários pré-configurados

O banco de dados é populado automaticamente com os seguintes usuários:

1. Administrador:
   - Email: admin@litoral.com
   - Senha: senha123

2. Corretor:
   - Email: corretor@litoral.com
   - Senha: senha123

## Estrutura do Projeto

### Front-end
- `src/components`: Componentes React reutilizáveis
- `src/contexts`: Contextos React para gerenciamento de estado
- `src/hooks`: Hooks personalizados
- `src/types`: Definições de tipos TypeScript

### Back-end
- `src/models`: Modelos de dados MongoDB
- `src/controllers`: Controladores para lógica de negócio
- `src/routes`: Rotas da API
- `src/middlewares`: Middlewares para autenticação e validação
- `src/config`: Configurações do servidor
- `src/utils`: Funções utilitárias e scripts para popular o banco de dados

## API Endpoints

### Autenticação
- `POST /api/auth/login`: Autenticar usuário
- `POST /api/auth/register`: Registrar usuário
- `GET /api/auth/me`: Obter dados do usuário autenticado
- `POST /api/auth/register-professional`: Solicitar registro profissional
- `POST /api/auth/register-particular`: Solicitar registro particular

### Usuários
- `GET /api/users`: Obter todos os usuários (admin)
- `GET /api/users/:id`: Obter um usuário específico (admin)
- `PUT /api/users/:id`: Atualizar um usuário (admin)
- `DELETE /api/users/:id`: Deletar um usuário (admin)
- `GET /api/users/registration-requests`: Obter solicitações de cadastro (admin)
- `PUT /api/users/approve-request/:id`: Aprovar uma solicitação (admin)
- `PUT /api/users/reject-request/:id`: Rejeitar uma solicitação (admin)

### Propriedades
- `GET /api/properties`: Listar propriedades
- `GET /api/properties/featured`: Listar propriedades em destaque
- `GET /api/properties/:id`: Obter uma propriedade específica
- `POST /api/properties`: Criar uma propriedade (corretoria/admin)
- `PUT /api/properties/:id`: Atualizar uma propriedade (corretoria/admin)
- `DELETE /api/properties/:id`: Deletar uma propriedade (corretoria/admin)
- `PUT /api/properties/:id/feature`: Marcar/desmarcar propriedade como destaque (admin)

### Notícias
- `GET /api/news`: Listar notícias
- `GET /api/news/:id`: Obter uma notícia específica
- `POST /api/news`: Criar uma notícia (admin)
- `PUT /api/news/:id`: Atualizar uma notícia (admin)
- `DELETE /api/news/:id`: Deletar uma notícia (admin)

## Licença

Este projeto está licenciado sob a licença MIT - consulte o arquivo LICENSE para mais detalhes. 