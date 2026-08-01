graph TD
    %% Internet & Borda
    Internet[🌐 Internet / ISP] --- Router[🛡️ Roteador de Borda / Firewall]

    %% Camada de Core Colapsado (Core + Distribuição)
    subgraph Camada_Core_Colapsado ["Camada Core Colapsada (Core + Distribuição)"]
        CoreSwitch[🔀 Switch Principal Layer 3 L3-Core]
    end

    Router --- CoreSwitch

    %% Camada de Acesso
    subgraph Camada_Acesso ["Camada de Acesso (Switches & WLC)"]
        SW_Sala_Principal[🔌 Switch Acesso L2 - Salão]
        SW_Salas_Anexas[🔌 Switch Acesso L2 - Salas Direitas]
        WLC[📡 Wireless Controller / Switch PoE]
    end

    CoreSwitch --- SW_Sala_Principal
    CoreSwitch --- SW_Salas_Anexas
    CoreSwitch --- WLC

    %% Dispositivos Finais - Salão Principal
    subgraph Salao_Principal ["Salão Principal"]
        PCs_Bloco1[💻 PCs Bloco 1 - Desktops]
        PCs_Bloco2[💻 PCs Bloco 2 - Desktops]
        PCs_Bloco3[💻 PCs Bloco 3 - Desktops]
        AP1[📶 Access Point 1]
        AP2[📶 Access Point 2]
        AP3[📶 Access Point 3]
    end

    SW_Sala_Principal --- PCs_Bloco1
    SW_Sala_Principal --- PCs_Bloco2
    SW_Sala_Principal --- PCs_Bloco3
    WLC --- AP1
    WLC --- AP2
    WLC --- AP3

    %% Dispositivos Finais - Salas Anexas
    subgraph Salas_Anexas ["Salas Direitas"]
        PCs_Salas[💻 PCs de Escritório / Reunião]
        AP4[📶 Access Point 4]
        AP5[📶 Access Point 5]
    end

    SW_Salas_Anexas --- PCs_Salas
    WLC --- AP4
    WLC --- AP5