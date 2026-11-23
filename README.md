# 🏥 Gerenciador de Unidades de Saúde (Gerador de Documentos)

Este é um sistema web *client-side* (roda inteiramente no navegador) desenvolvido para automatizar a criação de pastas e a geração de documentos oficiais (Comunicação Interna e Despacho) para unidades de saúde.

O script cria toda a estrutura de diretórios no computador do usuário e gera arquivos no formato `.docx` (Microsoft Word) pré-preenchidos com os dados fornecidos, prontos para serem salvos ou convertidos em PDF.

## ✨ Funcionalidades

- **Seleção de Diretório Raiz:** Utiliza a *File System Access API* para criar as pastas diretamente no computador do usuário.
- **Criação Automática de Estrutura:** Cria a pasta principal (com o nome da unidade) e as subpastas `Documentos PDF` e `Documentos Word`.
- **Formulário Dinâmico:** Interface amigável para preencher metadados como Nº do CI, Data, Processo, Objeto, Endereço, Serviço, Valor, Prazo, Fiscal e Empresa.
- **Geração de Documentos Nativos:** Cria arquivos `.docx` reais (Office Open XML) sem a necessidade de servidores ou bibliotecas externas de terceiros.
- **Cabeçalho Oficial:** Os documentos já saem com o Brasão do Estado da Bahia, cabeçalho institucional (SESAB/CEIRF/CEM) e tabelas de identificação formatadas.
- **Validação de Dados:** Impede a criação de pastas duplicadas e exige que os campos principais sejam preenchidos.

## 🚀 Como Usar

1. Faça o download do arquivo `index.html` (ou clone este repositório).
2. Abra o arquivo em um navegador compatível (veja a seção **Requisitos**).
3. Clique no botão **📁 Selecionar pasta raiz** e escolha onde os documentos serão salvos.
4. Preencha o nome da unidade e os demais dados no formulário.
5. Clique em **➕ Criar Unidade e Gerar Documentos**.
6. Acesse a pasta selecionada: os documentos `.docx` estarão prontos para uso!

## ⚠️ Requisitos e Compatibilidade

Como o sistema utiliza a **File System Access API**, ele **não funciona em todos os navegadores**.

- ✅ **Navegadores Suportados:** Google Chrome, Microsoft Edge e Opera.
- ❌ **Navegadores Não Suportados:** Firefox, Safari, Internet Explorer e a maioria dos navegadores mobile.
- **Segurança:** A API exige que o arquivo HTML seja servido via `localhost` ou `HTTPS`. Se você abrir o arquivo diretamente (`file:///C:/...`), a API pode não funcionar. Recomenda-se usar uma extensão como o *Live Server* no VS Code ou hospedar via GitHub Pages.

## 🛠️ Tecnologias Utilizadas

O projeto foi construído do zero, sem frameworks ou dependências (Zero Dependencies), garantindo leveza e facilidade de execução:

- **HTML5 & CSS3:** Interface limpa e responsiva.
- **JavaScript (Vanilla):** Toda a lógica de manipulação de arquivos, DOM e geração de documentos.
- **Office Open XML (OOXML):** Escrita manual da estrutura XML necessária para o Word.
- **ZIP Store:** Implementação nativa em JavaScript (via `Uint8Array` e `DataView`) para compactar os arquivos `.docx` sem precisar da biblioteca `JSZip`.
- **Base64 / Data URI:** Uso do brasão oficial convertido em imagem para embutir diretamente no `.docx`.

## 📂 Estrutura de Pastas Gerada

Para cada unidade criada, o sistema gera o seguinte padrão:

```text
[Pasta Raiz Selecionada]/
└── NOME DA UNIDADE/
    ├── Documentos PDF/          (Vazio, pronto para receber os PDFs)
    └── Documentos Word/
        ├── CI [NUM]-2026 - DESP [EMPRESA].docx
        └── CI n[NUM]-2026.docx
