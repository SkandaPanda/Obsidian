
```mermaid
graph TD
    %% --- STYLING ---
    classDef glu fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
    classDef cac fill:#fff9c4,stroke:#fbc02d,stroke-width:2px;
    classDef ox fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px;
    classDef atp fill:#ffcc80,stroke:#e65100,stroke-width:2px,color:#000,font-weight:bold;
    classDef electron fill:#f3e5f5,stroke:#7b1fa2,stroke-dasharray: 5 5;

    %% --- STEG 1: GLYKOLYSEN ---
    subgraph S1 [1. Glykolysen]
        direction TB
        G[Glukos]:::glu
        Process1(Nedbrytning):::glu
        Pyr[2 Pyruvat]:::glu
    end

    %% --- STEG 2: CITRONSYRACYKELN ---
    subgraph S2 [2. Citronsyracykeln]
        direction TB
        ACoA[Acetyl-CoA]:::cac
        Cycle((Krebs Cykel)):::cac
    end

    %% --- STEG 3: OXIDATIV FOSFORYLERING ---
    subgraph S3 [3. Oxidativ Fosforylering]
        direction TB
        ETC[Elektrontransportkedjan<br/>Protein-pumpar]:::ox
        O2(Syre O2):::ox
        H2O(Vatten H2O):::ox
        Grad[H+ Gradient]:::ox
        Turbin[ATP-syntas<br/>Turbinfunktion]:::ox
    end

    %% --- ATP SUMMARING ---
    ATP_G(2 ATP):::atp
    ATP_C(2 ATP):::atp
    ATP_O(34 ATP):::atp
    TOTAL{{TOTALT: 38 ATP}}:::atp

    %% --- FLÖDEN ---
    
    %% Kol-flödet (Substans)
    G --> Process1 --> Pyr
    Pyr -->|Omvandling| ACoA --> Cycle

    %% Elektron-flödet (NADH/FADH2)
    Process1 -.->|e- via NADH| ETC
    ACoA -.->|e- frigörs| ETC
    Cycle -.->|e- frigörs| ETC

    %% Oxidativ process
    O2 --> ETC
    ETC -->|e- + O2 + H+| H2O
    ETC -->|Pumpar väte| Grad
    Grad -->|H+ strömmar tillbaka| Turbin

    %% ATP Produktion
    Process1 --> ATP_G
    Cycle --> ATP_C
    Turbin -->|ADP + P -> ATP| ATP_O

    %% Sammanställning
    ATP_G --> TOTAL
    ATP_C --> TOTAL
    ATP_O --> TOTAL

    %% Länkar för layout (osynliga för styrning)
    S1 ~~~ S2 ~~~ S3
```


```mermaid
flowchart TD
  A[Glucose] --> B["Hexokinase\nG6P"]
  B --> C["Phosphoglucose isomerase\nF6P"]
  C --> D["PFK-1\nF1,6BP"]
  D --> E["Aldolase\nDHAP + GAP"]
  E --> F["Triose phosphate isomerase\n2 GAP"]

  F --> G["GAP dehydrogenase\n1,3-BPG\nProduces 2 NADH"]
  G --> H["Phosphoglycerate kinase\n3-PG\n2 ATP"]
  H --> I["Phosphoglycerate mutase\n2-PG"]
  I --> J["Enolase\nPEP"]
  J --> K["Pyruvate kinase\n2 Pyruvate\n2 ATP"]

  K --> L[Fermentation]

  subgraph Anaerobic_Fermentation ["Fermentation pathways"]
    direction LR
    M["LDH\nPyruvate → Lactate"] 
    N["Lactate\nRegenerates NAD+"]
    P["Pyruvate decarboxylase\nPyruvate → Acetaldehyde + CO2"]
    Q["Alcohol dehydrogenase\nAcetaldehyde → Ethanol"]
    R["Ethanol\nRegenerates NAD+"]
  end

  L --> M
  M --> N
  L --> P
  P --> Q
  Q --> R

  N --> F
  R --> F

  K --> T["Net ATP yield: 2 ATP per glucose"]

```

