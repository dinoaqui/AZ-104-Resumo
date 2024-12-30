### **Exportação e Implantação de Templates ARM**

1. **Exportar Template ARM do Resource Group**:  
   - Selecionando **Download** na página **Export Template** das propriedades do grupo de recursos (**RG1**) exporta o **template ARM**.
   - Para implantar o template, use o cmdlet:  
     ```powershell
     New-AzResourceGroupDeployment
     ```

2. **Salvar Template ARM com PowerShell**:  
   - O cmdlet **Save-AzDeploymentTemplate** salva o **template ARM** de um recurso.  
   - Depois, use o mesmo cmdlet **New-AzResourceGroupDeployment** para implantar o template.

3. **Exportar Configuração de uma VM (VM1)**:  
   - Na VM, selecionando **Deploy** na página **Export Template**, é possível criar uma nova máquina virtual com base na configuração da VM existente.

4. **Salvar Logs de Script de Implantação**:  
   - O cmdlet **Save-AzDeploymentScriptLog** salva os logs da execução de um script de implantação.

5. **Listar Máquinas Virtuais na Assinatura**:  
   - O cmdlet **Get-AzVM** gera uma lista de VMs criadas na assinatura do Azure.

---

### **Principais Cmdlets**

| **Cmdlet**                      | **Descrição**                                              |
|----------------------------------|----------------------------------------------------------|
| `New-AzResourceGroupDeployment` | Implanta um template ARM no grupo de recursos.           |
| `Save-AzDeploymentTemplate`     | Salva um template ARM de um recurso.                     |
| `Save-AzDeploymentScriptLog`    | Salva logs da execução de um script de implantação.      |
| `Get-AzVM`                      | Lista todas as VMs na assinatura.                        |

---

- **Virtual machines são implantadas em Resource Groups**: Para isso, deve-se usar o cmdlet **`New-AzResourceGroupDeployment`**.
  
- **VMs não podem ser implantadas diretamente em assinaturas (subscriptions) ou grupos de gerenciamento (management groups)**: Isso significa que **`New-AzManagementGroupDeployment`** e **`New-AzSubscriptionDeployment`** não podem ser utilizados para este fim.

- **`New-AzVM` pode ser utilizado para criar uma nova VM**: Contudo, esse cmdlet não permite a criação usando um template ARM (Azure Resource Manager). Ele é uma opção direta para provisionar uma máquina virtual sem o uso de modelos predefinidos.

---
