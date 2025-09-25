# CC Hook - Conventional Commits Hook

Um script shell simples e eficiente para configurar automaticamente um git hook que valida mensagens de commit seguindo o padrão [Conventional Commits](https://www.conventionalcommits.org/).

## 🎯 O que faz

Este script instala um hook `commit-msg` no seu repositório Git que:

- ✅ Valida automaticamente todas as mensagens de commit
- 🚫 Bloqueia commits que não seguem o padrão Conventional Commits
- 📝 Fornece feedback claro sobre erros e exemplos de uso correto
- 🔒 Mantém backup de hooks existentes
- 🎨 Interface colorida e amigável

## 📋 Pré-requisitos

- Git instalado no sistema
- Bash shell
- Estar dentro de um repositório Git inicializado

## 🚀 Instalação

### Opção 1: Instalação Global (Recomendada)

Para usar o comando `conventional-commit` de qualquer lugar:

1. **Baixe o script:**
   ```bash
   curl -o cc-hook https://raw.githubusercontent.com/thera-org/Conventional-Commits-Hook/main/cc-hook
   ```

2. **Mova para o diretório de scripts pessoais:**
   ```bash
   # Para diretório padrão do usuário (Linux/macOS)
   mkdir -p ~/.local/bin
   mv cc-hook ~/.local/bin/
   chmod +x ~/.local/bin/cc-hook
   
   # OU para diretório global (requer sudo)
   sudo mv cc-hook /usr/local/bin/
   sudo chmod +x /usr/local/bin/cc-hook
   ```

3. **Certifique-se que o diretório está no PATH:**
   ```bash
   # Verifique se ~/.local/bin está no PATH
   echo $PATH | grep -q "$HOME/.local/bin" && echo "✅ PATH configurado" || echo "❌ Precisa configurar PATH"
   
   # Se necessário, adicione ao seu ~/.bashrc ou ~/.zshrc:
   echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
   source ~/.bashrc
   ```

4. **Use o comando de qualquer repositório:**
   ```bash
   cd meu-projeto
   cc-hook
   ```

### Opção 2: Instalação Local

Para uso apenas no projeto atual:

1. **Baixe o script no projeto:**
   ```bash
   curl -o cc-hook https://raw.githubusercontent.com/thera-org/Conventional-Commits-Hook/main/cc-hook
   chmod +x cc-hook
   ```

2. **Execute o script:**
   ```bash
   ./cc-hook
   ```

### 📁 Diretórios comuns para scripts:

| Sistema         | Diretório          | Descrição                    |
|-----------------|-------------------|------------------------------|
| **Linux/macOS** | `~/.local/bin`    | Scripts do usuário (padrão) |
| **Linux/macOS** | `/usr/local/bin`  | Scripts globais (requer sudo)|
| **macOS**       | `/opt/homebrew/bin` | Via Homebrew               |
| **Windows**     | `C:\Users\%USER%\bin` | Pasta pessoal            |

> 💡 **Dica**: O diretório `~/.local/bin` é o mais recomendado para scripts pessoais, pois não requer permissões administrativas.

Após a instalação, o hook será executado automaticamente a cada commit. Se a mensagem não estiver no formato correto, o commit será rejeitado.

### Validação automática:

Após executar o script, o hook será ativado automaticamente a cada commit. Se a mensagem não estiver no formato correto, o commit será rejeitado.

### ✅ Exemplos de commits válidos:

```bash
git commit -m "feat: adicionar autenticação de usuário"
git commit -m "fix(api): corrigir bug de timeout"
git commit -m "docs: atualizar README"
git commit -m "feat!: remover suporte ao Node.js 14"
git commit -m "chore(deps): atualizar dependências"
```

### ❌ Exemplos de commits inválidos:

```bash
git commit -m "adicionar nova feature"        # Sem tipo
git commit -m "fix bug"                       # Sem dois pontos
git commit -m "invalid: "                     # Tipo inválido
git commit -m "feat:"                         # Sem descrição
```

## 🏷️ Tipos de commit suportados

| Tipo       | Descrição                                              |
|------------|-------------------------------------------------------|
| `feat`     | Nova funcionalidade                                   |
| `fix`      | Correção de bug                                       |
| `docs`     | Alterações na documentação                            |
| `style`    | Formatação, espaços (sem mudança de código)          |
| `refactor` | Refatoração (sem nova funcionalidade ou correção)    |
| `test`     | Adicionar ou modificar testes                         |
| `chore`    | Manutenção geral (dependências, ferramentas)         |
| `build`    | Sistema de build ou dependências externas            |
| `ci`       | Configuração de CI/CD                                 |
| `perf`     | Melhoria de performance                               |
| `revert`   | Reverter commit anterior                              |

## 🎯 Formato das mensagens

```
<tipo>(<escopo opcional>): <descrição>

Exemplos:
feat(auth): implementar login com JWT
fix: corrigir vazamento de memória
docs(api): adicionar documentação dos endpoints
```

### Breaking Changes

Para indicar mudanças que quebram compatibilidade, use `!`:

```bash
feat!: remover API v1
fix(api)!: alterar formato de resposta
```

## 🛠️ Funcionalidades

### ✨ Recursos do script:

- **Validação automática**: Verifica se está em um repositório Git
- **Backup inteligente**: Preserva hooks existentes com timestamp
- **Interface amigável**: Mensagens coloridas e informativas
- **Flexível**: Permite sobrescrever hooks existentes
- **Completo**: Feedback detalhado sobre erros

### 🔧 Exceções automáticas:

O hook ignora automaticamente:
- Merge commits (`Merge branch...`)
- Revert commits (`Revert...`)
- Commits iniciais (`Initial commit`)
- Commits vazios

## 🔧 Gerenciamento

### Ver status do hook:
```bash
ls -la .git/hooks/commit-msg
```

### Remover o hook:
```bash
rm .git/hooks/commit-msg
```

### Restaurar backup:
```bash
cp .git/hooks/commit-msg.backup.TIMESTAMP .git/hooks/commit-msg
```

## 🌍 Compatibilidade

- ✅ Linux
- ✅ macOS  
- ✅ Windows (Git Bash, WSL)
- ✅ Todas as versões do Git

## 🤝 Contribuindo

Contribuições são bem-vindas! Para contribuir:

1. Faça fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-funcionalidade`)
3. Commit suas mudanças (`git commit -m "feat: adicionar nova funcionalidade"`)
4. Push para a branch (`git push origin feature/nova-funcionalidade`)
5. Abra um Pull Request

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 📚 Links úteis

- [Conventional Commits Specification](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
- [Git Hooks Documentation](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)

## ❓ FAQ

### P: O hook funciona em repositórios já existentes?
R: Sim, funciona em qualquer repositório Git, novo ou existente.

### P: Posso personalizar os tipos de commit?
R: Sim, você pode editar o arquivo `.git/hooks/commit-msg` para adicionar tipos customizados.

### P: O que acontece se eu clonar o repositório?
R: Hooks não são versionados pelo Git, então cada colaborador precisa executar o script.

### P: Posso usar em repositórios corporativos?
R: Sim, o script é totalmente local e não envia dados para nenhum servidor.

### P: Como verifico se o comando está disponível globalmente?
R: Execute `which cc-hook` ou `cc-hook --help` para verificar se está no PATH.

### P: O que fazer se o comando não for encontrado?
R: Verifique se o diretório está no PATH e se o arquivo tem permissão de execução (`chmod +x`).

---

⭐ Se este projeto foi útil para você, considere dar uma estrela no GitHub!
