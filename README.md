# DevOps Bootcamp

Um pipeline completo de infraestrutura para implantar uma aplicação com capacidades de API e testes, incluindo destruição automatizada de infraestrutura.

## 🛠 Tecnologias

- Azure Cloud
- Terraform
- Ansible
- GitHub Actions

## 📋 Pré-requisitos

Configure as variáveis de ambiente do backend do Azure:

```bash
RESOURCE_GROUP="rg-tfstate"
STORAGE_ACCOUNT="tfstatecurso$RANDOM"
CONTAINER_NAME="tfstate"
LOCATION="eastus"
```

## 🚀 Comandos de Configuração

```bash
az group create --name $RESOURCE_GROUP --location $LOCATION

az storage account create \
    --name $STORAGE_ACCOUNT \
    --resource-group $RESOURCE_GROUP \
    --location $LOCATION \
    --sku Standard_LRS \
    --encryption-services blob

az storage container create \
    --name $CONTAINER_NAME \
    --account-name $STORAGE_ACCOUNT \
    --auth-mode login
```

## 📦 Modos de Pipeline

- **`destroy: false`** (padrão) - Cria infraestrutura, configura VM e executa testes
- **`destroy: true`** - Destrói toda a infraestrutura

## ✅ Resultados Esperados

- ✓ Criação automatizada de infraestrutura
- ✓ Configuração de VM com Ansible
- ✓ API Swagger disponível na porta 8081
- ✓ Destruição segura de infraestrutura via GitHub Actions

## ⚠️ Boas Práticas

Mantenha `destroy` como `false` por padrão. Defina como `true` apenas quando destruir intencionalmente a infraestrutura.