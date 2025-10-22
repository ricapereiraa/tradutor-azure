# Tradutor de Documentos (.docx)

Este projeto traduz documentos `.docx` usando o Azure Translator. O código principal está em `translator.py`.

## Requisitos
- Python 3.10+
- Pacotes Python listados em `requirements.txt`
- Uma chave do serviço Azure Translator (Text Translation API) na região correta (ex.: `eastus2`)

## Instalação
1. (Opcional) Crie um ambiente virtual.
2. Instale as dependências:
```bash
pip install -r requirements.txt
```

## Configuração
- Defina a chave do Azure Translator como variável de ambiente `AZURE_TRANSLATOR_KEY`.

Windows PowerShell (persistente para novas janelas):
```
setx AZURE_TRANSLATOR_KEY "SUA_CHAVE_AQUI"
```
Windows PowerShell (apenas na sessão atual):
```
$env:AZURE_TRANSLATOR_KEY = "SUA_CHAVE_AQUI"
```
Git Bash (apenas na sessão atual):
```
export AZURE_TRANSLATOR_KEY="SUA_CHAVE_AQUI"
```

- Confirme a região do recurso em `location` (ex.: `eastus2`). Deve ser a mesma do recurso da sua chave.
- Defina o caminho do arquivo de entrada (já configurado no projeto para):
```python
input_file = r"C:\Users\ricpe\Desktop\tradutor\Document.docx"
```
Coloque seu arquivo com este nome e caminho.

## Como usar
Execute o script:
```bash
python "C:\Users\ricpe\Desktop\tradutor\translator.py"
```
Saída esperada:
- Um novo arquivo traduzido no mesmo diretório, com sufixo do idioma, por exemplo:
```
C:\Users\ricpe\Desktop\tradutor\Document_pt-br.docx
```

## Observações
- O idioma de destino está configurado em `language_destination = 'pt-br'`.
- O idioma de origem está fixo como `'en'` na chamada da API. Se o documento não estiver em inglês, a tradução pode não ficar ideal.
- O arquivo contém seções adicionais (raspagem de página e uso de AzureChatOpenAI). Elas não são necessárias para traduzir `.docx`. Se desejar, basta executar até a chamada `translate_document(input_file)`.

## Solução de problemas
- 401/403 na API: verifique chave `subscription_key` e região `location` correspondendo ao recurso.
- Erro de caminho: confirme que `C:\Users\ricpe\Desktop\tradutor\Document.docx` existe.
- Dependências: rode `pip install -r requirements.txt`.

## Publicar no GitHub
1. Inicialize o repositório no diretório do projeto:
```bash
git init
git add .
git commit -m "Inicializa projeto do tradutor"
```
2. Crie um repositório vazio no GitHub e copie a URL (ex.: `https://github.com/SEU_USUARIO/tradutor-azure.git`).
3. Configure o remoto e envie:
```bash
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/tradutor-azure.git
git push -u origin main
```
