<!--
Objetivo: Documentar os casos de uso do sistema de agendamento.
Escopo: Fluxos principais de interação entre usuários e sistema.
-->

## Casos de Uso

**UC01 – Registrar Paciente**  
*Ator principal:* Paciente (não cadastrado)  
*Objetivo:* Permitir que novos pacientes criem uma conta no sistema.  
*Resumo do fluxo:* Paciente acessa tela de registro → informa nome, e-mail e senha → sistema valida dados → cria conta no Firebase Auth → cria documento do usuário no Firestore com role "patient" → redireciona para área do paciente.  
*Observação:* Apenas pacientes podem se auto-registrar. A nutricionista é pré-cadastrada pelo administrador.

**UC02 – Autenticar Usuário**  
*Ator principal:* Nutricionista, Paciente  
*Objetivo:* Permitir acesso ao app de forma segura.  
*Resumo do fluxo:* Usuário informa credenciais → sistema valida no Firebase → se ok, entra na área apropriada (nutri ou paciente).

**UC03 – Visualizar Disponibilidade de Consultas (Paciente)**  
*Ator:* Paciente  
*Objetivo:* Ver dias e horários disponíveis para agendamento.  
*Resumo:* Paciente abre tela de agenda → app consulta backend e lógica interna de disponibilidade → exibe calendário/lista com slots livres.

**UC04 – Solicitar Consulta**  
*Ator:* Paciente  
*Objetivo:* Enviar uma solicitação de consulta para a nutricionista.  
*Resumo:* Paciente escolhe data/horário → confirma → sistema cria registro de consulta com status "pendente" no Firebase.

**UC05 – Listar Solicitações Pendentes (Nutricionista)**  
*Ator:* Nutricionista  
*Objetivo:* Visualizar todas as solicitações pendentes.  
*Resumo:* Nutri abre tela "Solicitações" → app busca no Firebase todas as consultas da nutri com status "pendente" → exibe lista.

**UC06 – Aceitar Solicitação de Consulta**  
*Ator:* Nutricionista  
*Objetivo:* Confirmar uma consulta.  
*Resumo:* Nutri abre detalhes de uma solicitação → clica em "Aceitar" → sistema verifica conflito de horário → se ok, muda status para "aceita", dispara notificações necessárias e permite criação de evento no calendário.

**UC07 – Recusar Solicitação de Consulta**  
*Ator:* Nutricionista  
*Objetivo:* Recusar uma consulta.  
*Resumo:* Nutri abre detalhes → clica em "Recusar" → sistema atualiza status para "recusada" e avisa o paciente.

**UC08 – Visualizar Agenda Confirmada da Nutricionista**  
*Ator:* Nutricionista  
*Objetivo:* Ver todas as consultas aceitas.  
*Resumo:* Nutri abre tela "Minha agenda" → app lista consultas com status "aceita", organizadas por data/horário.

**UC09 – Visualizar Minhas Consultas (Paciente)**  
*Ator:* Paciente  
*Objetivo:* Acompanhar suas consultas e seus status.  
*Resumo:* Paciente abre tela "Minhas consultas" → app lista todas as consultas do paciente, status e detalhes.

**UC10 – Sincronizar com Calendário do Dispositivo**  
*Ator:* Sistema  
*Objetivo:* Manter o calendário do dispositivo sincronizado com as consultas.  
*Resumo:* Quando uma consulta for aceita, o sistema adiciona automaticamente um evento ao calendário do dispositivo com lembretes de 1h e 24h antes. Quando a consulta for cancelada ou recusada, o evento é removido automaticamente do calendário.  
*Observação:* A sincronização é automática e não requer ação do usuário. Caso a permissão de calendário seja negada, o app continua funcionando normalmente.

**UC11 – Agendar Notificações de Lembrete**  
*Ator:* Sistema  
*Objetivo:* Notificar o paciente próximo à data da consulta.  
*Resumo:* Ao ter uma consulta "aceita", app agenda notificações locais para horários pré-definidos (24h e 1h antes).

**UC12 – Reverter Cancelamento de Consulta (Nutricionista)**  
*Ator:* Nutricionista  
*Objetivo:* Permitir que a nutricionista aceite posteriormente uma consulta que estava cancelada.  
*Resumo:* Nutri abre detalhes de uma consulta cancelada → clica em "Aceitar" → sistema atualiza o status para "aceita", verifica conflitos de horário, dispara notificações necessárias e permite criação/atualização do evento no calendário.
