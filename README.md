# Omnichat Data Cleaner

Pipeline em Python (focado no Google Colab) para higienização de contatos do Omnichat:

- Normaliza cabeçalhos (snake_case sem acentos).
- Padroniza telefones no formato E.164 (+55...).
- “Coalesce” de colunas com nomes diferentes (ex.: `limite`, `limite_disponível` → `limite_disponivel`).
- Conversão de valores BR para número (`R$ 1.234,56` → `1234.56`).
- Deduplicação por telefone (mantém o registro mais recente).
- **Filtra baixo potencial** por `ticket_medio` e `limite_disponivel` (configurável).
- Exporta:
  - `base_limpa.xlsx` (auditoria completa, **sem excluir nenhuma coluna original**);
  - `omnichat_contacts.csv` (Nome, fullNumber, Limite_Disponivel, Ticket_Medio, Loja).

## Como usar (Colab)

1. Suba seu arquivo `.xlsx` (ex.: `data (55).xlsx`) no Colab em `/content/`.
2. No script, ajuste:
   ```python
   INPUT_XLSX_PATH = "/content/data (55).xlsx"
   # dica: salvar saídas na mesma pasta
   OUTPUT_XLSX_PATH = "/content/base_limpa.xlsx"
   OUTPUT_CSV_PATH  = "/content/omnichat_contacts.csv"
