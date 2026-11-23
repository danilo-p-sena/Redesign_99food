# Como publicar no GitHub e compartilhar para testes

O projeto está organizado para publicação como site estático no GitHub Pages. Há duas formas de publicar.

## Opção A — deixar que eu envie os arquivos pelo GitHub conectado

1. Acesse https://github.com/new.
2. Nome do repositório: `99food-delivery-redesign`.
3. Marque **Public** para gerar um link que você possa compartilhar com participantes.
4. Marque **Add a README file** para inicializar a branch `main`.
5. Não precisa adicionar `.gitignore` nem licença: esses arquivos já estão neste projeto.
6. Clique em **Create repository** e envie o link do repositório nesta conversa.

Com a branch inicial criada, consigo enviar os arquivos do projeto para esse repositório usando a conexão GitHub disponível.

## Opção B — publicar você mesmo usando o Git bundle

Coloque `99food-delivery-redesign.bundle` em uma pasta local e crie um repositório público vazio no GitHub (sem README, licença ou `.gitignore`). No PowerShell, execute:

```powershell
git clone .\99food-delivery-redesign.bundle 99food-delivery-redesign
cd .\99food-delivery-redesign
git remote add origin https://github.com/SEU_USUARIO/99food-delivery-redesign.git
git push -u origin main
```

Troque `SEU_USUARIO` pelo seu usuário do GitHub.

## Ativar o site público

1. No repositório, abra **Settings → Pages**.
2. Em **Build and deployment → Source**, selecione **GitHub Actions**.
3. Acesse **Actions** e aguarde o workflow `Publish 99Food to GitHub Pages` terminar com sucesso.
4. Copie o endereço publicado em **Settings → Pages** e compartilhe com as pessoas que farão o teste.

O site é estático; não precisa configurar banco de dados, servidor ou variáveis secretas.
