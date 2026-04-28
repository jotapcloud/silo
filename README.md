# Silo 📦 

**Silo** é uma ferramenta de interface de linha de comando (CLI) escrita em Go, projetada para simplificar o backup e a sincronização de diretórios no Linux com um foco intransigente em segurança. 

O Silo garante que os seus dados nunca saiam da sua máquina sem estarem devidamente comprimidos e encriptados (End-to-End Encryption).

## 🚀 Funcionalidades

- **Criptografia de Ponta a Ponta**: Utiliza AES-256-GCM para garantir que nem mesmo o provedor de storage consiga ler os seus ficheiros.
- **Compressão Nativa**: Reduz o tamanho do upload e preserva permissões de ficheiros Linux (tar.gz).
- **Múltiplos Destinos**: Suporte inicial para AWS S3 e servidores remotos via SCP.
- **Histórico Local**: Base de dados SQLite integrada para monitorizar o sucesso, data e integridade (checksum) de cada backup.
- **Binário Único**: Sem dependências externas. Basta descarregar e executar.

## 🛠️ Como funciona (Workflow)

O Silo segue uma pipeline de processamento segura:
1. **Target**: O diretório local é selecionado.
2. **Compress**: O conteúdo é compactado num ficheiro temporário.
3. **Encrypt**: O ficheiro é cifrado com uma chave mestre (gerada no `init`).
4. **Transport**: O pacote cifrado é enviado para o destino (S3/SCP).
5. **Log**: O histórico é atualizado no SQLite local.
