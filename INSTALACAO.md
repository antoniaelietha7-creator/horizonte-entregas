# Instalação — Horizonte Entregas

## 1. Configurar Authentication
No Firebase Console:
1. Abra **Authentication** > **Sign-in method**.
2. Confirme que **E-mail/senha** está habilitado.

## 2. Configurar as regras do Firestore
1. Abra **Firestore Database** > **Regras**.
2. Substitua o conteúdo pelas regras do arquivo `firestore.rules`.
3. Clique em **Publicar**.

Essas regras permitem que cada pessoa crie e leia somente seu próprio perfil. A pessoa não pode aprovar a própria conta nem alterar o próprio tipo de usuário. A coleção de corridas permanece bloqueada nesta versão.

## 3. Publicar no GitHub Pages
1. Crie o repositório público `horizonte-entregas`.
2. Envie `index.html`, `firestore.rules`, `README.md` e este guia para a raiz do repositório.
3. No GitHub, abra **Settings** > **Pages**.
4. Em **Build and deployment**, escolha **Deploy from a branch**.
5. Selecione `main` e `/ (root)`, depois salve.
6. Aguarde o GitHub publicar e abra a URL apresentada na tela de Pages.

## 4. Autorizar o domínio no Firebase
No Firebase Console:
1. Abra **Authentication** > **Settings** > **Authorized domains**.
2. Adicione o domínio do GitHub Pages (por exemplo, `SEU-USUARIO.github.io`).
3. Salve.

## 5. Testar
- Abra o site publicado.
- Crie uma conta de teste como loja.
- Saia e crie outra conta como entregador, usando outro e-mail.
- Confirme no Firebase Authentication que os usuários foram criados.
- Confirme no Firestore que existem documentos em `users`, com IDs iguais aos UIDs.

## Observações de segurança e produto
- A chave `apiKey` do Firebase Web identifica o projeto; ela não substitui regras de segurança. Não coloque chaves privadas ou credenciais de serviço no site.
- Não desative as regras do Firestore para “fazer funcionar”.
- Não habilite corridas, pagamentos, localização ou acesso público aos perfis até implementar regras específicas e testar abuso, concorrência e privacidade.
- O status inicial dos cadastros é `pending`. A aprovação administrativa ainda será implementada.
- A primeira versão não inclui chamadas de entrega, distribuição de corridas, chat, mapas, rastreamento, notificações push ou pagamentos.
- Antes de abrir ao público, prepare termos de uso, política de privacidade, canal de suporte e análise jurídica do modelo de operação.
