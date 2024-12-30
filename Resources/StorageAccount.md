Tabela comparativa dos tipos de redundância de armazenamento no Azure:

| **Tipo de Redundância**      | **Descrição**                                                                 | **Proteção Oferecida**                            | **Regiões**             | **Acesso**                         |
|------------------------------|-------------------------------------------------------------------------------|--------------------------------------------------|-------------------------|-------------------------------------|
| **Locally Redundant Storage (LRS)** | Armazena **3 cópias dos dados** no mesmo datacenter.                             | Falhas de hardware no mesmo datacenter.          | Uma região (local).     | Apenas na região primária.         |
| **Zone-Redundant Storage (ZRS)**   | Armazena os dados em **3 zonas diferentes** dentro da mesma região.              | Falhas em zonas de disponibilidade na região.    | Uma região (multi-zona).| Apenas na região primária.         |
| **Geo-Redundant Storage (GRS)**    | Replica os dados para uma **região secundária distante geograficamente**.         | Falhas regionais.                                | Primária e secundária.  | Apenas na região primária.         |
| **Read-Access Geo-Redundant Storage (RA-GRS)** | Igual ao GRS, mas permite **leitura na região secundária**.                      | Falhas regionais e leitura em região secundária. | Primária e secundária.  | Leitura em ambas as regiões.       |

---

### **Observações**:
- **LRS**: Econômico, ideal para dados que não precisam de alta resiliência.
- **ZRS**: Alta disponibilidade dentro de uma região, usado para aplicações críticas regionais.
- **GRS**: Recomendado para dados que precisam de resiliência geográfica, mas sem leitura secundária.
- **RA-GRS**: Ideal para cenários onde leitura contínua é necessária, mesmo durante falhas regionais.

---
