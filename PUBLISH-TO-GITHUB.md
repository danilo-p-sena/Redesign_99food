# Como publicar no GitHub e compartilhar para testes

O pacote inclui um repositório Git em formato bundle (`99food-delivery-redesign.bundle`) e uma versão ZIP dos arquivos do site.

## 1. Criar o repositório remoto

1. Acesse https://github.com/new.
2. Nome: `99food-delivery-redesign`.
3. Marque **Public** se quiser compartilhar com participantes por um link público.
4. Não marque as opções de criar README, `.gitignore` ou licença: os arquivos já estão no projeto.
5. Clique em **Create repository**.

## 2. Enviar o histórico pronto (Windows PowerShell)

Coloque `99food-delivery-redesign.bundle` em uma pasta local e execute:

```powershell
git clone .\99food-delivery-redesign.bundle 99food-delivery-redesign
cd .\99food-delivery-redesign
git remote add origin https://github.com/SEU_USUARIO/99food-delivery-redesign.git
git push -u origin main
```

Troque `SEU_USUARIO` pelo seu usuário do GitHub. Se preferir, também é possível extrair o ZIP, abrir a pasta no GitHub Desktop e publicar o repositório por lá.

## 3. Ativar o site público

1. No repositório, abra **Settings → Pages**.
2. Em **Build and deployment → Source**, selecione **GitHub Actions**.
3. Acesse **Actions** e aguarde o workflow `Publish 99Food to GitHub Pages` terminar com sucesso.
4. Copie o endereço publicado em **Settings → Pages** e compartilhe com as pessoas que farão o teste.

O site é estático; não precisa configurar banco de dados, servidor ou variáveis secretas.
