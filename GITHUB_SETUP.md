# 🚀 Como Fazer Deploy no GitHub

## Pré-requisitos
- Conta GitHub ativa
- Git instalado localmente
- Acesso ao repositório (permissões de push)

## Opção 1: Usando GitHub Web Interface

1. **Criar novo repositório**
   - Acesse https://github.com/new
   - Nome: `dashboard-terras-raras`
   - Descrição: "Dashboard de auditoria de terras raras — TCU/DAmin"
   - Visibilidade: **Public** (para órgãos públicos)
   - ✅ Marcar "Add a README file"
   - Criar repositório

2. **Upload dos arquivos**
   - Na página principal do repo, clique `Add file` → `Upload files`
   - Arraste ou selecione:
     - `dashboard-terras-raras.html`
     - `TCU_SIGMINE_Demo_TR.xlsx`
     - Remova o README.md gerado (vamos usar o nosso)
   - Commit: `Initial commit: Dashboard v1.0`

3. **Substituir README**
   - Clique no README.md gerado
   - Clique ✏️ (Edit)
   - Copie o conteúdo de `README.md` deste pacote
   - Commit changes

4. **Adicionar arquivos restantes**
   - `.gitignore`, `LICENSE`, `CHANGELOG.md`
   - Para cada um: `Add file` → `Create new file`
   - Cole o conteúdo
   - Commit

## Opção 2: Usando Git CLI (Recomendado)

```bash
# 1. Clone o repositório criado
git clone https://github.com/SEU_USUARIO/dashboard-terras-raras.git
cd dashboard-terras-raras

# 2. Copie os arquivos deste pacote
cp -r /caminho/para/dashboard-terras-raras/* .

# 3. Verifique os arquivos
git status

# 4. Adicione todos
git add .

# 5. Commit inicial
git commit -m "Initial commit: Dashboard de Terras Raras v1.0

- 12 módulos de análise de mineração
- IRATR (Rejeitos TR) com upload Excel/CSV
- Dados aerogeofísica SGB
- Compatível com SIGMINE ANM
- Dark theme responsivo
- Zero dependências (CDN Chart.js + SheetJS)"

# 6. Push para main
git push origin main
```

## Opção 3: GitHub Desktop

1. Abra GitHub Desktop
2. `File` → `Clone repository`
3. Selecione o repositório criado
4. Clone para pasta local
5. Copie os arquivos deste pacote para a pasta local
6. GitHub Desktop detectará automaticamente as mudanças
7. Commit: preencha título e descrição
8. Push

## Estrutura Final no GitHub

```
dashboard-terras-raras/
├── .gitignore
├── LICENSE
├── CHANGELOG.md
├── README.md
├── GITHUB_SETUP.md
├── dashboard-terras-raras.html      (389 KB)
└── TCU_SIGMINE_Demo_TR.xlsx         (9.4 KB)
```

## Configurações GitHub Recomendadas

Após o primeiro push, acesse **Settings** do repositório:

### General
- ✅ Marcar "Require status checks to pass before merging" (se tiver CI/CD)
- ✅ "Automatically delete head branches"

### Pages
- **Source**: Deploy from a branch
- **Branch**: `main`
- **Folder**: `/ (root)`
- **Clique Save**
- GitHub Pages gerado em: `https://SEU_USUARIO.github.io/dashboard-terras-raras/`

**Acesso direto ao Dashboard:**
```
https://raw.githubusercontent.com/SEU_USUARIO/dashboard-terras-raras/main/dashboard-terras-raras.html
```

Abra este URL em um navegador — o arquivo HTML funcionará diretamente!

### Topics (Labels)
- `auditoria`
- `mineracao`
- `terras-raras`
- `brasil`
- `governanca`
- `dashboard`
- `tcu`

### About
- **Description**: Dashboard de auditoria de terras raras — TCU/DAmin
- **Website**: (deixe em branco ou adicione sua página)
- **Topics**: conforme acima

## Updates Futuros

Quando quiser fazer updates:

```bash
# Atualize arquivos locais
git add .
git commit -m "Update: [descrição da mudança]"
git push origin main
```

## Licença e Atribuição

Todos os arquivos incluem:
- ✅ `LICENSE` — Restrição comercial
- ✅ Atribuição obrigatória ao TCU no README e no código

**Não remova estas informações!**

## Visibilidade e Acesso

### Público (Recomendado)
- Qualquer pessoa pode clonar e usar
- Compatível com Lei de Acesso à Informação (LAI)
- Demonstra transparência governamental

### Privado (Alternativa)
- Apenas usuários convidados podem acessar
- Use se tiver dados sensíveis

**Recomendação**: Público, pois dashboard usa dados SGB/CPRM que são públicos.

## Verificação Final

Após push, confirme:

```bash
# Verifique se está no repositório
git log  # Deve mostrar seu commit

# Verifique a branch
git branch  # Deve estar em main

# Verifique remote
git remote -v  # Deve apontar para seu repositório
```

## Problemas Comuns

**"Permission denied (publickey)"**
- Configure SSH key: https://docs.github.com/en/authentication/connecting-to-github-with-ssh

**"refused to merge unrelated histories"**
- Se clonou vazio: `git pull origin main --allow-unrelated-histories`

**"Files too large"**
- Dashboard HTML tem 389 KB (OK)
- Excel tem 9.4 KB (OK)
- Se ultrapassar 100 MB, usar Git LFS

## Próximos Passos

1. ✅ Criar repositório no GitHub
2. ✅ Fazer push dos arquivos
3. ⏭️ Testar o dashboard via GitHub Raw URL
4. ⏭️ Habilitar GitHub Pages (opcional)
5. ⏭️ Documentar no Wiki (opcional)
6. ⏭️ Criar releases quando houver updates

---

**Versão**: 1.0
**Data**: 2026-04-06
**Autor**: TCU/DAmin
