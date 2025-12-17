# Rocco Converter - Página de Download

Página web simples para download do Rocco Converter.

## Estrutura

```
rocco-converter-website/
├── index.html      # Página principal
├── styles.css      # Estilos
├── script.js       # Detecção de SO e links
├── favicon.svg     # Ícone do site
└── README.md       # Este arquivo
```

## Como fazer o deploy

### Passo 1: Criar repositório no GitHub

1. Acesse https://github.com/new
2. Nome do repositório: `rocco-converter` (ou outro nome)
3. Marque como **Private** (para uso interno)
4. Clique em "Create repository"

### Passo 2: Fazer upload dos arquivos de release

1. No repositório criado, vá em **Releases** (menu lateral direito)
2. Clique em **Create a new release**
3. Tag: `v1.0.0`
4. Title: `Rocco Converter 1.0.0`
5. Na seção **Attach binaries**, arraste os arquivos:
   - `Rocco Converter Setup 1.0.0.exe` (Windows)
   - `Rocco Converter-1.0.0-arm64.dmg` (macOS)
   - `Rocco Converter-1.0.0-arm64.AppImage` (Linux)
6. Clique em **Publish release**

### Passo 3: Atualizar os links de download

Após criar o release, copie os links dos arquivos e atualize o arquivo `script.js`:

```javascript
const DOWNLOADS = {
    windows: {
        name: 'Windows',
        url: 'https://github.com/USUARIO/REPO/releases/download/v1.0.0/Rocco.Converter.Setup.1.0.0.exe',
        filename: 'Rocco Converter Setup 1.0.0.exe'
    },
    macos: {
        name: 'macOS',
        url: 'https://github.com/USUARIO/REPO/releases/download/v1.0.0/Rocco.Converter-1.0.0-arm64.dmg',
        filename: 'Rocco Converter-1.0.0-arm64.dmg'
    },
    linux: {
        name: 'Linux',
        url: 'https://github.com/USUARIO/REPO/releases/download/v1.0.0/Rocco.Converter-1.0.0-arm64.AppImage',
        filename: 'Rocco Converter-1.0.0-arm64.AppImage'
    }
};
```

### Passo 4: Fazer upload da página web

**Opção A: Mesmo repositório (recomendado)**

1. Crie uma branch `gh-pages`:
   ```bash
   cd rocco-converter-website
   git init
   git checkout -b gh-pages
   git add .
   git commit -m "Add download page"
   git remote add origin https://github.com/USUARIO/REPO.git
   git push -u origin gh-pages
   ```

2. Vá em **Settings** > **Pages** no repositório
3. Em **Source**, selecione `gh-pages` branch
4. Clique em **Save**

**Opção B: Repositório separado**

1. Crie um novo repositório: `rocco-converter-download`
2. Faça upload dos arquivos
3. Ative GitHub Pages nas configurações

### Passo 5: Acessar a página

Após alguns minutos, a página estará disponível em:
- `https://USUARIO.github.io/REPO/` (se usar gh-pages)
- `https://USUARIO.github.io/rocco-converter-download/` (se usar repo separado)

## Para repositório privado

Se o repositório for privado, os releases também serão privados. Nesse caso:

1. Os usuários precisam estar logados no GitHub
2. Ou use **GitHub Enterprise** com autenticação SSO
3. Ou hospede os arquivos em um servidor interno da empresa

## Personalizações

### Alterar cores
Edite as variáveis CSS no início do arquivo `styles.css`:

```css
:root {
    --primary: #6366f1;        /* Cor principal */
    --primary-dark: #4f46e5;   /* Cor principal escura */
    --bg: #0f0f23;             /* Fundo */
}
```

### Alterar logo
Substitua o conteúdo SVG no `index.html` dentro da classe `.logo-icon`.

### Adicionar mais plataformas
Adicione novas entradas no objeto `DOWNLOADS` em `script.js`.
