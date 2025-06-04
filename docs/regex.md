
# 🐧 Regex no Linux e 🪟 Windows

## 🔍 `grep`

Busca padrões com regex em arquivos ou comandos.

**Sintaxe básica:**
```bash
grep 'padrão' arquivo.txt
grep [opções] 'padrão' arquivo.txt
```

**Principais opções:**
- `-i` ignora maiúsculas/minúsculas
- `-v` inverte a busca
- `-r` busca recursiva
- `-l` exibe nomes dos arquivos com correspondência
- `-c` mostra o número de ocorrências
- `-n` exibe número da linha
- `-E` regex estendida
- `-P` regex Perl (se suportado)

**Ajuda:** `man grep`

---

## 📝 `sed`

Substitui texto com regex.

**Exemplo:**
```bash
sed 's/padrão/novo/g' arquivo.txt
```

---

## 🧠 `awk`

Processa texto baseado em padrões e campos.

**Exemplo:**
```bash
awk '/padrão/ {print $1}' arquivo.txt
```

---

## 🪟 `findstr` (Windows CMD)

Busca com regex simples.

**Exemplo:**
```cmd
findstr /r "padrão" arquivo.txt
```

**Opções úteis:**
- `/I` ignora maiúsculas/minúsculas
- `/N` mostra número da linha
- `/S` busca recursiva
- `/C:"texto exato"` busca literal

---

## ⚡ PowerShell (Windows)

Regex avançado com `-match`, `-replace`, `-split`.

**Exemplo com -match:**
```powershell
Get-Content arquivo.txt | ForEach-Object { if ($_ -match "padrão") { $_ } }
```

**Operadores:**
- `-match`: verifica correspondência
- `-replace`: substitui por regex
- `-split`: separa por padrão regex

---

# ✅ POSIX vs Metacaracteres

Depende do contexto e do problema que você quer resolver. Conheça os principais padrões POSIX e metacaracteres:

### 📋 Tabela POSIX - Bracket Expressions

| Expressão      | Significado                          |
|----------------|------------------------------------|
| `[[:digit:]]`  | Qualquer dígito                    |
| `[[:alpha:]]`  | Qualquer letra alfabética          |
| `[[:alnum:]]`  | Qualquer caractere alfanumérico    |
| `[[:blank:]]`  | Espaço em branco ou tabulação      |
| `[[:space:]]`  | Qualquer espaço em branco          |
| `[[:lower:]]`  | Qualquer letra minúscula           |
| `[[:upper:]]`  | Qualquer letra maiúscula           |
| `[[:print:]]`  | Qualquer caractere imprimível      |
| `[[:punct:]]`  | Qualquer caractere de pontuação    |
| `[[:graph:]]`  | Imprimíveis, exceto espaços        |
| `[[:xdigit:]]` | Dígitos hexadecimais (0-9, a-f, A-F) |
| `[[:cntrl:]]`  | Caracteres de controle             |

### 📋 Tabela de Metacaracteres em Regex

| Metacaractere | Significado                           |
|---------------|-------------------------------------|
| `.`           | Qualquer caractere (exceto quebra de linha) |
| `*`           | Zero ou mais ocorrências do anterior |
| `+`           | Uma ou mais ocorrências do anterior  |
| `?`           | Zero ou uma ocorrência do anterior   |
| `()`          | Grupo de captura                    |
| `[]`          | Classe de caracteres                |
| `[^]`         | Classe de caracteres negada         |
| `^`           | Início da linha                    |
| `$`           | Fim da linha                      |
| `\`           | Escape de metacaractere            |
| `{}`          | Quantificador personalizado         |

## Vantagens e Desvantagens do POSIX

### ✅ Vantagens

- **Legibilidade:** Sintaxe clara e fácil de entender para classes comuns (ex: `[[:digit:]]` para dígitos).
- **Portabilidade:** Suportado pela maioria das ferramentas Unix/Linux que usam regex POSIX (como `grep`, `sed`, `awk`).
- **Simplicidade:** Útil para buscas básicas e filtros de caracteres específicos sem complicações.

### ❌ Desvantagens

- **Limitado:** Menos flexível que metacaracteres avançados.
- **Menos poderosos:** Não suportam quantificadores complexos, lookaheads, ou outras construções avançadas.
- **Menor controle:** Não permitem agrupamentos e manipulações mais refinadas dentro da regex.
