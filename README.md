# **Rastreador de Encomendas - Cargas**
> Sistema para rastreamento de cargas com funcionalidades distintas para clientes e administradores.

---

## **Descrição Geral**
Este projeto consiste no desenvolvimento de um sistema para rastreamento de encomendas/cargas utilizado por uma empresa. O sistema possui dois tipos de usuários:  
- **Cliente**: Consulta o status e informações da carga por meio de um código de rastreamento.  
- **Administrador**: Possui controle total sobre as cargas, podendo criar, atualizar, apagar e reverter alterações para corrigir erros.

---

## **Tecnologias Utilizadas**
### **Front-end**  
- React (JavaScript).  
- CSS Modules.  
- Gerenciamento de estado: Context API ou Redux.
- Motion

### **Back-end**  
- Node.js com Fastify (TypeScript).  
- Banco de dados: PostgreSQL (Neon).  
- ORM: Prisma.  
- Autenticação: JWT.  

### **Extras**  
- Deploy Front-end: Vercel.  
- Deploy Back-end: Render .  
- Controle de versão: Git/GitHub.

---

## **Requisitos do Sistema**
### **Cliente**
- Inserir código de rastreamento para consultar status e informações da carga.  
- Visualizar status, descrição, e última atualização da carga.  

### **Administrador**
- CRUD completo de cargas:
  - Criar nova carga.  
  - Atualizar status e descrição.  
  - Deletar cargas.  
- Reverter ações (exemplo: voltar ao status anterior).  
- Gerenciar histórico de alterações para cada carga.  

---

## **Planejamento Técnico**
### **Estrutura do Banco de Dados**
#### Tabelas Principais
1. **Users**:  
   - `id` (PK, UUID), `name`, `email`, `password` (hashed), `role` (enum: cliente/adm), `createdAt`, `updatedAt`.

2. **Shipments (Cargas)**:  
   - `id` (PK, UUID), `trackingCode` (string único), `status`, `description`, `createdBy` (FK para Users), `createdAt`, `updatedAt`.

3. **Histórico de Alterações**:  
   - `id` (PK, UUID), `shipmentId` (FK para Shipments), `action`, `previousState` (JSON), `newState` (JSON), `performedBy` (FK para Users), `timestamp`.

---

### **Endpoints da API**
#### Rotas para Cliente:
1. `GET /shipments/:trackingCode`:  
   - Retorna detalhes da carga com base no código de rastreamento.  

#### Rotas para Administrador:
1. `POST /shipments`:  
   - Cria uma nova carga.  
2. `PUT /shipments/:id`:  
   - Atualiza informações da carga.  
3. `DELETE /shipments/:id`:  
   - Remove uma carga.  
4. `POST /shipments/:id/revert`:  
   - Reverte a última ação realizada.

---

## **Estrutura do Front-end**
### **Páginas Planejadas**
1. **Cliente**:
   - Tela inicial:
     - Input para código de rastreamento.  
     - Exibição do status e informações da carga.  

2. **Administrador**:
   - Dashboard:
     - Listagem de todas as cargas.  
     - Botões para editar, deletar e reverter ações.  
   - Formulário de CRUD:
     - Criar e editar cargas.

---

## **Etapas do Desenvolvimento**
### **Fase 1: Planejamento**  
- Desenhar as interfaces do front-end.  
- Estruturar o banco de dados no Neon.  

### **Fase 2: Desenvolvimento do Front-end**  
- Criar estrutura inicial com React e organizar os componentes.  
- Desenvolver a página inicial para busca de cargas (cliente).  
- Desenvolver o dashboard do administrador.

### **Fase 3: Desenvolvimento do Back-end**  
- Configurar servidor Fastify e conexão com o Neon.  
- Criar rotas para cliente e administrador.  
- Implementar autenticação com JWT.

### **Fase 4: Testes e Deploy**  
- Realizar testes unitários e de integração.  
- Deploy no Vercel (front-end) e Render/Railway (back-end).

---

### **Notas Finais**
Este documento será atualizado conforme o projeto evolui.
