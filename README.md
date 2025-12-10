# Vitta - App de Agendamento Nutricional

Sistema de agendamento de consultas nutricionais desenvolvido com React Native + Expo Router + Firebase.

## Sobre o Projeto

O Vitta é um aplicativo que facilita o agendamento de consultas entre pacientes e nutricionistas, oferecendo:

- **Para Pacientes**: Visualização de horários disponíveis, solicitação de consultas, acompanhamento de status
- **Para Nutricionistas**: Gestão de solicitações, confirmação/recusa de consultas, visualização da agenda
- **Integrações**: Calendário nativo, notificações de lembrete

## Arquitetura

O projeto segue o padrão **MVVM simplificado** com separação clara de responsabilidades:

```
src/
├── app/              # Expo Router - Roteamento (sem lógica de negócio)
├── view/             # Interface do usuário
│   ├── pages/        # Telas (Patient, Nutritionist)
│   ├── components/   # Componentes reutilizáveis
│   └── themes/       # Tokens de design
├── viewmodel/        # ViewModels (estado e comandos da UI)
├── usecase/          # Casos de uso (regras de negócio)
├── model/            # Domínio
│   ├── entities/     # Entidades (User, Appointment)
│   ├── services/     # Interfaces de serviços
│   └── errors/       # Erros de domínio
├── infra/            # Implementações concretas
│   ├── firebase/     # Firebase Auth + Firestore
│   ├── calendar/     # Expo Calendar
│   └── notifications/# Expo Notifications
└── di/               # Injeção de dependências
```

## Começando

### Pré-requisitos

- Node.js 18+
- npm ou yarn
- Expo CLI
- Conta Firebase configurada

### Instalação

1. Clone o repositório
2. Instale as dependências:
   ```bash
   npm install
   ```

3. Configure o Firebase:
   - Crie um projeto no Firebase Console
   - Adicione as configurações em `src/infra/firebase/config.ts`

4. Inicie o app:
   ```bash
   npm start
   ```

## Documentação

Toda a documentação do projeto está em `/docs`:

- **ARQUITETURA.md**: Padrões, estrutura e boas práticas
- **RF.md**: Requisitos Funcionais
- **RNF.md**: Requisitos Não Funcionais
- **UC.md**: Casos de Uso
- **TELAS.md**: Especificação de interfaces
- **HUN.md, HUP.md, HUS.md**: Histórias de Usuário

## Testes

```bash
npm test              # Rodar testes
npm run test:watch    # Modo watch
npm run test:coverage # Cobertura
```

## Scripts Disponíveis

- `npm start` - Inicia o servidor Expo
- `npm run android` - Abre no emulador Android
- `npm run ios` - Abre no simulador iOS
- `npm run web` - Abre no navegador
- `npm run lint` - Executa linting

## Princípios Arquiteturais

1. **Inversão de Dependência**: ViewModels e Use Cases dependem de interfaces, não de implementações
2. **Separação de Camadas**: View não conhece Firebase, ViewModel não conhece React Native diretamente
3. **Testabilidade**: Injeção de dependências permite testes com mocks
4. **Single Responsibility**: Cada camada tem uma responsabilidade clara

## Stack Tecnológica

- **Framework**: React Native + Expo
- **Roteamento**: Expo Router (file-based)
- **Backend**: Firebase (Auth + Firestore)
- **Notificações**: Expo Notifications
- **Calendário**: Expo Calendar
- **Linguagem**: TypeScript
- **Testes**: Jest + React Native Testing Library

## 📝 Status do Projeto

🚧 Em desenvolvimento - Estrutura inicial configurada

### Concluído
✅ Estrutura de pastas MVVM criada  
✅ Expo Router configurado (roteamento básico)  
✅ Documentação completa em `/docs`  
✅ Path aliases configurados (`@/*` → `./src/*`)  
✅ TypeScript strict mode habilitado

### Estado Atual
- Apenas roteamento básico implementado (sem componentes visuais)
- Estrutura de pastas seguindo arquitetura MVVM
- Pronto para iniciar implementação das camadas

### Próximas Etapas
- [ ] Implementar camada de domínio (entidades e interfaces)
- [ ] Configurar Firebase
- [ ] Implementar casos de uso
- [ ] Desenvolver ViewModels
- [ ] Criar telas e componentes

## Perfis de Usuário

- **Paciente**: Pode se auto-registrar, visualizar disponibilidade, solicitar consultas
- **Nutricionista**: Gerencia solicitações, confirma/recusa consultas, visualiza agenda

## Licença

Este projeto é privado e destinado a uso acadêmico/profissional.

