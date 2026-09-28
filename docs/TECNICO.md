# Documentação técnica — Site CIAL

> Arquivo sugerido para `docs/TECNICO.md`. Descreve a estrutura observada no repositório; não substitui uma auditoria do código nem um guia de implantação validado.

## Organização

```text
site-cial1/
├── pagina/               # Páginas da loja, estilos, scripts e imagens
├── cadastro/             # Cadastro, login, recuperação de senha e área do cliente
└── cial-backend/
    ├── server.js          # Entrada do servidor
    ├── CadastroRoute.js   # Arquivo de rota relacionado a cadastro
    ├── RecuperacaoRoute.js # Arquivo de rota relacionado a recuperação
    ├── supabaseCliente.js # Arquivo de integração com banco
    ├── emailConfig.js     # Configuração relacionada a e-mail
    └── package.json       # Dependências e scripts do backend
```

As páginas incluem `pagina/index.html`, `pagina/Produtos.html`, `pagina/bombas.html`, `pagina/carrinho.html`, `pagina/admin.html`, `cadastro/cadastro.html`, `cadastro/login.html`, `cadastro/recuperar-senha.html` e `cadastro/area-cliente.html`. A existência desses arquivos não confirma que todos os fluxos estejam concluídos.

## Desenvolvimento local

O backend possui `package.json` em `cial-backend/`. Instale as dependências nessa pasta e confira os scripts declarados no arquivo antes de iniciar o servidor. Para testar o frontend, use um servidor HTTP local se a abertura direta do HTML não permitir as requisições à API. As portas, URLs e variáveis necessárias devem ser confirmadas na configuração atual do projeto; não estão documentadas aqui como valores definitivos.

## Segurança e publicação

Foi observado `cial-backend/.env` no repositório. **Não copie seus valores para esta documentação.** Se houver credenciais reais, trate-as como potencialmente expostas: revogue ou rotacione as credenciais, remova o arquivo do versionamento, adicione-o ao `.gitignore` e disponibilize somente um `.env.example` com valores fictícios. A remoção da versão atual não apaga automaticamente entradas antigas do histórico Git.

Antes de apresentar o sistema como pronto para clientes ou colocá-lo em produção, verifique:

- Autenticação e autorização de cada rota sensível, inclusive operações administrativas e recuperação de senha.
- Permissões e políticas de acesso às tabelas e aos dados dos usuários.
- Validação de entradas e tratamento de erros sem vazamento de informações sensíveis.
- Presença de `node_modules/` e arquivos em `uploads/` no controle de versão.
- Configuração de ambiente, URLs, integrações, armazenamento e testes dos fluxos reais.

Esta documentação **não certifica que as rotas estão seguras**. A afirmação exige revisão do código e testes no ambiente em que o projeto será executado.
