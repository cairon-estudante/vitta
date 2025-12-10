<!--
Objetivo: Listar os requisitos não funcionais do sistema de agendamento.
Escopo: Restrições técnicas, de desempenho e segurança do sistema.
-->

## Requisitos Não Funcionais (RNF)

**RNF01 – Plataforma**  
O aplicativo deve ser desenvolvido em React Native com Expo, suportando Android e iOS.

**RNF02 – Backend**  
O backend deve ser implementado utilizando Firebase (Auth, Firestore/Realtime Database).

**RNF03 – Segurança de dados**  
Os acessos ao backend devem ser protegidos por regras de segurança do Firebase (segurança em nível de coleção e por usuário), garantindo que:  
- Um paciente só veja/edite suas próprias solicitações.  
- A nutricionista veja apenas suas consultas aceitas, pendentes e canceladas.

**RNF04 – Privacidade**  
Dados pessoais dos pacientes e da nutricionista devem ser armazenados minimamente e usados apenas para o funcionamento da agenda, em conformidade com boas práticas de privacidade.

**RNF05 – Desempenho / Responsividade**  
O app deve carregar listas de consultas e agenda em no máximo 3 segundos, sem travamentos perceptíveis para o usuário em cenários de uso normal (poucas dezenas/centenas de consultas).

**RNF06 – Usabilidade**  
As telas devem ser simples, com navegação clara e textos em linguagem acessível, considerando o uso diário por profissionais de saúde e pacientes em geral.

**RNF07 – Confiabilidade das notificações**  
As notificações de lembrete devem ser agendadas localmente no dispositivo, de forma que funcionem mesmo se o app não estiver aberto na hora do lembrete.

**RNF08 – Integração com calendário**  
A integração com o calendário deve pedir permissões de forma clara ao usuário, explicando o motivo, e degradar caso o usuário negue a permissão (app continua funcionando sem a criação automática de evento).

**RNF09 – Mantenabilidade**  
O código deve ser organizado em MVVM, facilitando manutenção e evolução futura.

**RNF10 – Disponibilidade**  
Como o app é de agenda, espera-se que o sistema backend (Firebase) esteja disponível 99,9% do tempo; em caso de falta de conexão, o app deve informar o usuário e oferecer tentativa de recarregar.