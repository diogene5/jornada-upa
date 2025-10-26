# Jornada do Paciente na UPA

## Chegada e Acolhimento
- Chegada na unidade
- Espera para cadastro
- Cadastro na recepção
## Classificação de Risco
- Espera para triagem
- Classificação de risco pela enfermagem (triagem)
## Atendimento Médico
- Espera para consulta médica
- Consulta médica
## Procedimentos Complementares
- Exames laboratoriais
- Exames de imagem
- Medicação
- Observação
- Indicação de transferência
- Encaminhamento para sala vermelha
## Desfecho
- Alta
- Evasão
- Transferência

---
## Análise dos tempos de espera em cada etapa
- [Arquivo base ](https://docs.google.com/spreadsheets/d/1ADjBKwcxvYHsuQTn9ePB81kiWBPV_5tQsQwW8uW1mUE/edit?usp=sharing)

A análise de 15 pacientes atendidos revela que o principal gargalo do fluxo está relacionado aos **exames laboratoriais**, que quando necessários (**27% dos casos**), elevam o tempo de permanência de aproximadamente **58 minutos para mais de 3 horas** — um aumento de **300% no tempo total**.

```mermaid
flowchart TD
    %% --- Fase 1: Chegada e Acolhimento ---
    subgraph F1["Chegada e Acolhimento"]
        A1([Chegada na UPA])
        A2[Espera para cadastro]
        A3[Cadastro na recepção]
        A1 --> A2 --> A3
    end

    %% --- Fase 2: Triagem ---
    subgraph F2["Triagem"]
        B1[Espera para triagem]
        B2[Classificação de risco<br/>pela enfermagem]
        A3 --> B1 --> B2
    end

    %% --- Fase 3: Atendimento Médico ---
    subgraph F3["Atendimento Médico"]
        C1[Espera para consulta]
        C2[Consulta médica]
        B2 --> C1 --> C2
    end

    %% --- Fase 4: Decisão Clínica e Procedimentos ---
    subgraph F4["Decisão e Procedimentos"]
        D1{Decisão clínica}
        D2[Medicação]
        D3[Raio-X]
        D4[Laboratório]
        D5[Observação]
        D6[Sala vermelha]
        C2 --> D1
        D1 --> D2
        D1 --> D3
        D1 --> D4
        D1 --> D5
        D1 --> D6
    end

    %% --- Fase 5: Desfecho ---
    subgraph F5["Desfecho"]
        E1{Desfecho final}
        F1a([Alta])
        F1b([Transferência])
        F1c([Evasão])
        D2 --> E1
        D3 --> E1
        D4 --> E1
        D5 --> E1
        D6 --> E1
        E1 --> F1a
        E1 --> F1b
        E1 --> F1c
    end

    %% --- Estilo visual ---
    classDef chegada fill:#e1f5fe,stroke:#90caf9
    classDef triagem fill:#fff9c4,stroke:#fbc02d
    classDef consulta fill:#e8f5e9,stroke:#66bb6a
    classDef exame fill:#fce4ec,stroke:#f06292
    classDef desfecho fill:#ede7f6,stroke:#9575cd
    classDef alerta fill:#ffcdd2,stroke:#e53935

    class A1,A2,A3 chegada
    class B1,B2 triagem
    class C1,C2 consulta
    class D2,D3,D4,D5 exame
    class D6 alerta
    class E1,F1a,F1b,F1c desfecho
```
