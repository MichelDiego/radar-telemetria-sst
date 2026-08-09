#  Radar Meteorológico Preditivo & Motor de Telemetria SST (NR-35)

![Node-RED](https://img.shields.io/badge/Node--RED-%238F0000.svg?style=for-the-badge&logo=node-red&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![OpenWeatherMap](https://img.shields.io/badge/OpenWeatherMap-EB6E4B?style=for-the-badge&logo=openweathermap&logoColor=white)
![IT/OT Convergence](https://img.shields.io/badge/IT/OT_Convergence-0056b3?style=for-the-badge)

[![Repositório no GitHub](https://img.shields.io/badge/-Reposit%C3%B3rio_no_GitHub-0D1117?style=for-the-badge&logo=github&logoColor=white)](https://github.com/MichelDiego/radar-telemetria-sst/)&nbsp;
[![Google Drive](https://img.shields.io/badge/-Documenta%C3%A7%C3%A3o_do_Projeto_(Google_Drive)-0D1117?style=for-the-badge&logo=googledrive&logoColor=34A853)](https://drive.google.com/drive/u/1/folders/1avHsMMq5jcwGjY_69YBqfBE1B63znS5A)

Motor de inteligência preditiva desenvolvido em **Node-RED** para ambientes de infraestrutura, construção civil e Facilities. O sistema realiza varreduras meteorológicas cruzadas via satélite e aplica regras de negócio focadas em **Segurança e Saúde no Trabalho (SST)** e na **Norma Regulamentadora 35 (NR-35)**.

O objetivo principal é antecipar riscos de ventos fortes, chuvas extremas e raios, alertando a Liderança de Campo e os Técnicos de Segurança do Trabalho com precisão, evitando acidentes em trabalhos em altura (balancins, andaimes, fachadas).

---

##  Principais Funcionalidades (Motor V4.2)

* **Varredura Preditiva 24h:** O algoritmo rastreia a matriz meteorológica em 40 blocos de tempo futuros, isolando o pior cenário nas próximas 24 horas.
* **Escudo Anti-Spam Resiliente:** Sistema de gestão de memória dinâmica (`flow context`) que impede alertas duplicados e fadiga de alarmes. O sistema fica em silêncio absoluto até que a janela crítica se aproxime.
* **Resumo Operacional de 12h & Alerta Térmico:** Envio de Boletim Matinal diário com o resumo das próximas 12 horas e disparo automático de recomendações de hidratação e pausa caso a sensação térmica exceda limites seguros.
* **Funil de Alertas (Time-to-Impact):** Gatilhos escalonados para $T-1\text{h}$ (Lembrete) e $T-0\text{h}$ (Impacto Confirmado).
* **Botão de Confirmação (Webhook):** Integração HTTP que permite ao responsável de campo clicar em "Ciente" diretamente do e-mail de emergência, registrando a auditoria no Node-RED.
* **Delegação de Responsabilidade (DDS):** Rodapé fixo de isenção, garantindo que a tecnologia serve como apoio à decisão humana da equipe técnica presente no local.

---

##  Arquitetura e Tecnologias

1. **Fonte de Dados (TI):** API REST do *OpenWeatherMap* (Modelo *5 day / 3 hour forecast*).
2. **Processamento (Middleware):** Node-RED com regras avançadas em JavaScript (ES6+).
3. **Saída de Alertas (OT/Operação):** SMTP (E-mail HTML dinâmico) e integração preparada para Webhooks de WhatsApp (Z-API/Evolution).
4. **Monitoramento de Saúde (Watchdog):** Nó de `Catch` dedicado que alerta automaticamente a equipe de TI/Automação em caso de falha de conexão ou erro de DNS da API.

---

##  Como Importar e Usar

1. Tenha o [Node-RED](https://nodered.org/) instalado em seu servidor local, Raspberry Pi ou Docker.
2. Certifique-se de ter instalado as bibliotecas:
   * `node-red-node-openweathermap`
   * `node-red-node-email`
3. Vá no menu superior direito do Node-RED > **Import**.
4. Cole o conteúdo do arquivo `flows/radar_sst_v4.2.json` disponível neste repositório.
5. No nó do OpenWeatherMap, insira a sua **API Key** e configure a Location para **Coordinates** (Latitude e Longitude da sua obra/site).
6. Configure suas credenciais de e-mail no nó de saída SMTP.

---

##  Demonstração

<img width="1365" height="635" alt="image" src="https://github.com/user-attachments/assets/3b82e6f4-fbb6-484e-ab7d-8a518ced6510" />

---

##  Autor

**Michel Coutinho** Tecnólogo em Automação Industrial | Eletromecânica  
Focado na convergência IT/OT e Automação Predial (BMS).
