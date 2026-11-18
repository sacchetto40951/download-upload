# Manual da API

## Requisitos
- **Python 3.10+**
- `pip` (gerenciador de pacotes do Python)
- **Postman** (versão desktop ou web) – https://www.postman.com/

---

## Executando a API localmente
```bash
# Crie e ative um ambiente virtual (recomendado)
python -m venv .venv
.venv\Scripts\activate   # Windows
# source .venv/bin/activate   # macOS / Linux

# Instale as dependências
pip install Flask

# Inicie o servidor
python app.py
```
O serviço ficará disponível no servidor local `http://127.0.0.1:5000`.

---

## Testando os endpoints no Postman
### Upload de Arquivo
- **Método:** `POST`
- **URL:** `(URL)/uploads/upload`
- **Body:** `form-data`
  - **Key:** `file` – tipo **File** – escolha o arquivo usando a variável `{{filePath}}`.
- **Enviar** → Você deve receber:
  ```json
  {
    "mensagem": "Arquivo salvo com sucesso!",
    "arquivo": "nome_do_arquivo.ext"
  }
  ```
  
---

### Download de Arquivo
- **Método:** `GET`
- **URL:** `{{baseUrl}}/downloads/download/{{filename}}`
- **Enviar** → O arquivo será baixado como anexo. Caso o nome esteja errado, a resposta será:
  ```json
  {"error": "Arquivo não encontrado"}
  ```
