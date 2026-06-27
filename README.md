# Relatório de Testes - Aplicativo Mobile

## Testes de Navegação e Validação de Dados

---

## Resumo Executivo

| Métrica | Valor |
|---------|-------|
| Total de Bugs Encontrados | 4 |
| Críticos | 0 |
| Altos | 0 |
| Médios | 2 |
| Baixos | 2 |
| Data do Teste | 27/06/2026 |

---

## Tabela Resumo de Bugs

| ID | Arquivo de Evidência | Severidade | Categoria | Descrição |
|----|----------------------|------------|-----------|-----------|
| 001 | `evidencias/evidencia1.png` | Baixa | UI/Layout | Campo de pesquisa com problema de posicionamento (desalinhado para baixo) |
| 002 | `evidencias/evidencia2.png` | Baixa | Validação | Caracteres especiais e emojis aceitos no nome da turma e dados da criança |
| 003 | `evidencias/evidencia3.png` | Média | Validação de Dados | Data de nascimento aceita o ano 1500 |
| 004 | `evidencias/evidencia4.png` | Média | Validação de Dados | Data de nascimento aceita valor inválido 00/00/0000 |

---

## Relatórios Detalhados dos Bugs

### Bug #001 - Campo de Pesquisa com Problema de Posicionamento

**Evidência:** `evidencias/evidencia1.png`

**Severidade:** Baixa (UI/Layout)

**Descrição:**
O campo de pesquisa "Pesquisar por turma..." apresenta um problema estético de layout, estando posicionado mais baixo do que o esperado, como se houvesse uma tabulação excessiva ou margem incorreta.

**Imagem do Erro:**
![Bug 001 - Problema de Layout](evidencias/evidencia1.png)

**Resultado Esperado:** O campo de pesquisa deve estar alinhado corretamente com os demais elementos da interface.

**Resultado Obtido:** Campo desalinhado, posicionado mais abaixo do que o padrão visual da aplicação.

---

### Bug #002 - Caracteres Especiais e Emojis Aceitos no Nome da Turma e Dados da Criança

**Evidência:** `evidencias/evidencia2.png`

**Severidade:** Baixa (Validação)

**Descrição:**
O sistema permite o cadastro de:
- **Nome da turma** com caracteres especiais, emojis e caracteres de outros idiomas (chinês: "不要點擊🎋")
- **Dados da criança** com os mesmos problemas: nome contendo emojis e caracteres especiais
- **Campo "Responsável"** também aceitando caracteres inválidos

A imagem mostra ambos os problemas concentrados na mesma tela: o nome da turma no header e os dados da criança "Zeca Luiz" com idade de 525 anos.

**Imagem do Erro:**
![Bug 002 - Caracteres Especiais](evidencias/evidencia2.png)

**Passos para Reproduzir:**
1. Criar turma com nome contendo emojis e caracteres especiais
2. Cadastrar criança na turma com dados inválidos
3. Visualizar a tela de detalhes da turma

**Resultado Esperado:**
- Validação de nomes (apenas letras, números e caracteres acentuados)
- Rejeição de emojis e caracteres especiais
- Limites de idade razoáveis

**Resultado Obtido:** Todos os dados inválidos foram aceitos e exibidos normalmente na interface.

---

### Bug #003 - Data de Nascimento com Ano 1500

**Evidência:** `evidencias/evidencia3.png`

**Severidade:** Média (Validação de Dados)

**Descrição:**
O sistema permite cadastrar o usuário principal "Anp" com data de nascimento 09/10/1500, resultando em uma idade impossível (~525 anos).

**Imagem do Erro:**
![Bug 003 - Data 1500](evidencias/evidencia3.png)

**Passos para Reproduzir:**
1. Acessar o perfil do usuário
2. Editar a data de nascimento
3. Inserir "09/10/1500"
4. Salvar

**Resultado Esperado:** O sistema deve limitar o ano mínimo (ex: 1900) ou validar a idade máxima permitida.

**Resultado Obtido:** A data foi salva e exibida como "09/10/1500".

---

### Bug #004 - Data de Nascimento 00/00/0000

**Evidência:** `evidencias/evidencia4.png`

**Severidade:** Média (Validação de Dados)

**Descrição:**
Após editar o perfil do usuário "Anp", a data de nascimento foi alterada para 00/00/0000, um valor completamente inválido.

**Imagem do Erro:**
![Bug 004 - Data Inválida](evidencias/evidencia4.png)

**Passos para Reproduzir:**
1. Acessar o perfil do usuário "Anp"
2. Clicar em "Editar"
3. Alterar a data de nascimento para "00/00/0000"
4. Salvar

**Resultado Esperado:** O sistema deve validar o formato da data e rejeitar valores nulos/zerados.

**Resultado Obtido:** A data "00/00/0000" foi salva e exibida no perfil.

---

