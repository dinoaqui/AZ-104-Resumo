### **Azure Management Groups**

---

### **O que são Azure Management Groups?**
- **Definição**: Os **Management Groups** (Grupos de Gerenciamento) no Azure são contêineres que ajudam a organizar e gerenciar **várias assinaturas**. Eles permitem aplicar **políticas, controle de acesso (RBAC)** e configurações de governança em escala.
- **Propósito**: Gerenciar centralmente assinaturas e recursos relacionados, garantindo que as organizações possam aplicar políticas e permissões consistentes em toda a hierarquia.

---

### **Estrutura Hierárquica**
- A hierarquia do Azure começa com o **tenant root group** no topo:
  1. **Raiz**: O grupo raiz (habilitado por padrão) está no topo da hierarquia e inclui todos os **Management Groups** e **assinaturas** do tenant.
  2. **Management Groups**: Agrupam assinaturas relacionadas para facilitar a governança.
  3. **Assinaturas**: Contêm os recursos como grupos de recursos, VMs, armazenamento, etc.

- **Exemplo de hierarquia**:
  ```
  Tenant Root Group
      └── Management Group MG1
           ├── Assinatura 1
           ├── Assinatura 2
      └── Management Group MG2
           ├── Assinatura 3
  ```

---

### **Funções de Acesso (RBAC) em Management Groups**
1. **Função Leitor (Reader)**:
   - Permite **visualizar recursos**, mas não realizar alterações.
   - Ideal para auditoria e acesso de leitura.

2. **Função Colaborador (Contributor)**:
   - Permite **gerenciar recursos**, incluindo criação, modificação e exclusão, mas não configura acesso.

3. **Função Proprietário (Owner)**:
   - Controle total, incluindo gerenciamento de acesso (atribuir permissões a outros).

4. **Leitor de Cobrança (Billing Reader)**:
   - Permite acesso a informações financeiras, como faturas e custos de assinatura.

---

### **Cenários Comuns de Uso**
1. **Aplicação de Políticas**:
   - Aplicar políticas como controle de tags, restrições de localizações ou habilitar logs de auditoria para todas as assinaturas.
   - **Exemplo**: Restringir que recursos sejam criados fora da região "East US".

2. **Gerenciamento de Acesso Centralizado**:
   - Conceder permissões específicas em um grupo de assinaturas ou recursos relacionados.
   - **Exemplo**: Adicionar a função "Leitor" para uma equipe de auditoria em todo o MG.

3. **Organização de Recursos**:
   - Agrupar assinaturas por unidades de negócio, como TI, Marketing ou RH.
   - **Exemplo**: `MG-Financeiro`, `MG-Tecnologia`.

---

### **Princípios Importantes**
1. **Privilégios Mínimos**:
   - Sempre atribuir o menor nível de permissão necessário para uma tarefa.

2. **Herança**:
   - Permissões e políticas aplicadas em um Management Group **são herdadas** por todas as assinaturas e recursos abaixo dele.

3. **Limite de Management Groups**:
   - Cada tenant pode ter até **10.000 Management Groups**.
   - Cada grupo pode conter até **6 níveis de profundidade** (excluindo o nível raiz).

---

### **Exemplo Prático de Configuração**
1. **Criar um Management Group**:
   ```powershell
   New-AzManagementGroup -GroupName "MG-Financeiro" -DisplayName "Financeiro"
   ```

2. **Atribuir uma Função**:
   ```powershell
   New-AzRoleAssignment -ObjectId <UserID> -RoleDefinitionName "Reader" -Scope "/providers/Microsoft.Management/managementGroups/MG-Financeiro"
   ```

3. **Aplicar uma Política**:
   ```powershell
   New-AzPolicyAssignment -Name "RestrictRegion" -PolicyDefinitionName "AllowedLocations" -Scope "/providers/Microsoft.Management/managementGroups/MG-Financeiro"
   ```

---

### **Vantagens dos Management Groups**
- **Governança centralizada**: Aplicar políticas e controle de acesso em várias assinaturas.
- **Facilidade de gerenciamento**: Organização lógica de recursos em grandes organizações.
- **Escalabilidade**: Gerencia até milhares de assinaturas em um único tenant.

---

### **Resumo**
- **Management Groups** são uma ferramenta essencial para governança e gerenciamento centralizado no Azure.
- Use funções apropriadas (Reader, Contributor, Owner) para aplicar o princípio de privilégios mínimos.
- Aplique políticas e permissões em escala para simplificar a governança organizacional.
