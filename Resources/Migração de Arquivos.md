---

### **AzCopy**

O **AzCopy** é uma ferramenta de linha de comando otimizada para copiar ou sincronizar dados entre ambientes locais e o Azure Storage.

#### **Principais Comandos e Parâmetros**
| **Comando/Parâmetro**           | **Descrição**                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------|
| **`copy`**                      | Copia dados do local de origem para o destino no Azure Storage.                              |
| **`sync`**                      | Sincroniza os arquivos entre origem e destino (apenas atualiza arquivos diferentes).         |
| **`--recursive`**               | Inclui subdiretórios ao realizar cópias ou sincronizações.                                   |
| **`--include-pattern`**         | Define padrões de arquivos a serem incluídos na operação, como `*.jpg` ou `file*.txt`.      |
| **`--exclude-pattern`**         | Exclui arquivos específicos da operação com base em padrões (e.g., `*.log`).                |
| **`--overwrite`**               | Especifica se arquivos existentes no destino devem ser sobrescritos.                        |
| **`--from-to`**                 | Especifica o tipo de operação (e.g., `LocalBlob`, `BlobBlob`).                              |

#### **Exemplo Prático**
```bash
AzCopy copy "C:\LocalFolder" "https://<storage-account>.blob.core.windows.net/<container>" --recursive
```
- Copia todos os arquivos e subdiretórios de `C:\LocalFolder` para um container no Azure Blob Storage.

---

### **PowerShell**

O PowerShell oferece uma abordagem flexível para migração de dados usando cmdlets específicos para o Azure.

#### **Principais Cmdlets**
| **Cmdlet**                      | **Descrição**                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------|
| **`Get-ChildItem`**             | Lista arquivos e diretórios. Inclui a opção `-Recurse` para listar subdiretórios.            |
| **`Set-AzStorageBlobContent`**  | Faz o upload de arquivos para o Azure Blob Storage.                                           |
| **`Connect-AzAccount`**         | Autentica sua conta no Azure para permitir a execução de comandos.                           |
| **`Get-AzStorageContainer`**    | Lista os containers disponíveis em uma conta de armazenamento do Azure.                      |
| **`New-AzStorageContainer`**    | Cria um novo container no Azure Blob Storage.                                                |

#### **Principais Parâmetros do PowerShell**
| **Parâmetro**                   | **Descrição**                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------|
| **`-Path`**                     | Especifica o diretório ou arquivo local.                                                     |
| **`-Recurse`**                  | Permite que `Get-ChildItem` inclua subdiretórios na listagem.                                |
| **`-Container`**                | Nome do container no Azure onde os arquivos serão enviados.                                  |
| **`-File`**                     | Define um arquivo específico para upload.                                                   |
| **`-Blob`**                     | Nome do blob criado no container (usado com `Set-AzStorageBlobContent`).                    |

#### **Exemplo Prático**
```powershell
Get-ChildItem -Path "C:\LocalFolder" -Recurse | Set-AzStorageBlobContent -Container "mycontainer"
```
- Lista todos os arquivos de `C:\LocalFolder` (incluindo subdiretórios) e faz o upload para o container `mycontainer`.

---

### **Comparação entre AzCopy e PowerShell**

| **Aspecto**            | **AzCopy**                                         | **PowerShell**                                     |
|-------------------------|---------------------------------------------------|--------------------------------------------------|
| **Velocidade**          | Otimizado para transferências em massa.           | Mais lento, dependendo da quantidade de arquivos. |
| **Facilidade de Uso**   | Simples, com comandos diretos.                    | Flexível, mas requer scripts para casos complexos.|
| **Controle Granular**   | Menos granular em operações específicas.          | Granular, ideal para automação detalhada.        |
| **Requisitos**          | Apenas linha de comando.                         | Requer configuração de módulos do Azure.        |

---

### **Dicas Práticas**
1. **Quando usar AzCopy**:
   - Para grandes migrações ou sincronizações de arquivos em massa.
   - Cenários onde velocidade e simplicidade são importantes.

2. **Quando usar PowerShell**:
   - Quando você precisa de controle granular sobre os arquivos ou deseja automatizar processos complexos.
   - Para integrar migração com outras tarefas de gerenciamento no Azure.

3. **Ambos**:
   - Certifique-se de autenticar no Azure antes de iniciar.
   - Sempre verifique permissões no destino e no ambiente local.
