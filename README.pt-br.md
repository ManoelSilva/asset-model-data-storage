[Read in English](README.md)

# Sistema de Abstração de Armazenamento

Este módulo fornece uma abstração flexível de armazenamento, permitindo que sistemas de modelos salvem arquivos tanto no sistema de arquivos local quanto na AWS S3, de acordo com a configuração do ambiente.

## Visão Geral

O sistema de armazenamento determina automaticamente onde salvar os arquivos com base na variável de ambiente `enviroment`:

- `enviroment=AWS`: arquivos são salvos na AWS S3
- `enviroment=SYSTEM` ou não definida: arquivos são salvos no sistema de arquivos local

## Componentes Principais

1. **DataStorageHandler** (Classe Base Abstrata)
2. **DataStorageService** (Fábrica/Coordenador)
3. **S3DataStorageService** (Implementação S3)
4. **SystemDataStorageService** (Implementação Local)

## Uso Básico

```python
from asset_model_data_storage.data_storage_service import DataStorageService

storage_service = DataStorageService()

# Salvar um arquivo
dados = b"Olá, Mundo!"
caminho_salvo = storage_service.save_file("teste/arquivo.txt", dados, "text/plain")

# Carregar um arquivo
dados_carregados = storage_service.load_file("teste/arquivo.txt")
```

## Configuração de Ambiente

Veja o README em inglês para detalhes completos de configuração e exemplos.

### Dependências para S3

- `boto3`: SDK AWS para Python
- `botocore`: Biblioteca de cliente de serviço AWS de baixo nível (necessária pelo boto3)
- Credenciais AWS configuradas (via variáveis de ambiente, AWS CLI ou funções IAM)

---

*Tradução em andamento. Para informações completas, consulte o [README.md](README.md).*
