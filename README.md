# AssetOps-Product-Requirements-Document


# AssetOps – Product Requirements Document (PRD)

**Versão:** 1.0 (Draft)
**Projeto:** AssetOps
**Subtítulo:** Operational Asset Management Platform

---

# 1. Visão Geral

## Objetivo

Desenvolver uma plataforma cliente/servidor para gerenciamento de operações de TI e ciclo de vida de ativos corporativos, centralizando informações, reduzindo retrabalho e garantindo rastreabilidade completa de todas as atividades.

O sistema deverá operar inicialmente em uma rede local da empresa, hospedado em um servidor Windows (Dell G15), suportando aproximadamente seis usuários simultâneos, com arquitetura preparada para crescimento futuro.

---

# 2. Objetivos do Produto

O AssetOps deverá permitir:

* Gerenciar Operations (Tasks) de forma estruturada.
* Gerenciar o ciclo de vida completo dos Assets.
* Registrar todas as ações realizadas pelos usuários.
* Controlar empréstimos, entregas, devoluções, reparos, scraps, issues e solicitações a fornecedores.
* Armazenar documentos, imagens, e-mails e anexos relacionados.
* Gerar indicadores operacionais.
* Automatizar notificações e comunicações.
* Integrar-se ao Microsoft Outlook via COM.
* Sincronizar inventários através de planilhas Excel.

---

# 3. Escopo da Versão 1

## Incluído

### Dashboard

* Resumo das Operations
* Minha fila
* Indicadores
* Notificações
* Calendário
* Assets recentes
* Timeline
* Pesquisa Global

### Operations

* Criar
* Atualizar
* Pausar
* Concluir
* Reabrir
* Timeline
* Comentários
* Anexos
* Checklists
* Templates
* Prioridades
* SLA
* VIP
* Auditoria

### Assets

* Cadastro
* Pesquisa
* Histórico
* Timeline
* Operações relacionadas
* Garantia
* Empréstimos
* Entregas
* Reparos
* Scrap
* Issues
* Fotos
* Documentos

### Synchronization

* Importação Excel (.xlsx)
* Validação
* Prévia
* Comparação
* Atualização inteligente
* Batch de sincronização
* Rollback por lote
* Histórico
* Auditoria

### Comunicação

* Outlook (COM)
* Templates bilíngues
* Calendário
* Notificações
* Pop-ups

### Administração

* Usuários
* Permissões
* Status
* Categorias
* Workflows
* Templates
* Checklists
* Configurações
* Idiomas

---

# 4. Fora do Escopo da V1

* Active Directory
* Microsoft Teams
* Aplicativo Mobile
* Integrações externas via API
* Inteligência Artificial
* Portal de fornecedores

A arquitetura deverá permanecer preparada para essas evoluções.

---

# 5. Perfis de Usuário

## Administrator

Permissão total.

Pode:

* Configurar sistema
* Gerenciar usuários
* Alterar qualquer Operation
* Gerenciar Assets
* Executar sincronizações
* Restaurar backups

---

## Supervisor

Pode:

* Criar Operations
* Editar Operations
* Atribuir responsáveis
* Encerrar Operations
* Consultar relatórios
* Aprovar sincronizações

---

## Manager

Pode:

* Visualizar indicadores
* Criar e editar Operations
* Concluir Operations
* Acompanhar métricas

---

## User

Pode:

* Criar Operations
* Atualizar próprias Operations
* Pausar com justificativa
* Concluir Operations
* Inserir anexos
* Comentar

---

## Visitor

Somente consulta.

Não pode alterar informações.

---

# 6. Regras Gerais

## Operation

Toda Operation possui:

* Identificador único
* Responsável
* Criador
* Participantes
* Categoria
* Prioridade
* Status
* Datas
* SLA
* Timeline
* Auditoria

---

## Estados

* Waiting
* In Progress
* Paused
* Completed

---

## Ordem padrão

Waiting:

Mais antiga primeiro.

Mais recente por último.

Filtros poderão alterar a visualização.

---

## Pausa

Pode ocorrer a qualquer momento.

Obrigatório informar justificativa.

---

## Conclusão

Permitida para:

* Administrator
* Supervisor
* Manager
* User

Não permitida para:

* Visitor

---

# 7. Assets

## Campos protegidos

Nunca poderão ser alterados automaticamente:

* Asset Number
* Serial Number
* First Service Date

Caso haja divergência na sincronização, será criado um conflito para análise manual.

---

## Campos sincronizáveis

* Owner
* Address
* Remark
* Asset Description (configurável)

---

## Categorias

### Trackable

Controle individual.

Exemplos:

* Notebook
* Desktop
* Monitor
* Impressora
* Switch

---

### Non-Trackable

Controle por quantidade ou lote.

Exemplos:

* Mouse
* Cabo HDMI
* Mochila
* Adaptadores
* Mouse Pad

---

# 8. Sincronização de Assets

Fluxo oficial:

1. Exportar inventário.
2. Copiar arquivo para pasta monitorada.
3. Executar sincronização manual.
4. Detectar arquivo.
5. Validar estrutura.
6. Comparar registros.
7. Exibir prévia.
8. Aprovar.
9. Aplicar alterações.
10. Registrar auditoria.
11. Arquivar arquivo.

---

## Arquivo aceito

Microsoft Excel (.xlsx)

Modelo oficial fornecido pelo AssetOps.

---

## Frequência

Verificação automática configurada para cada 8 horas.

Botão "Sincronizar Agora" disponível para execução manual.

---

# 9. Comunicação

O sistema utilizará Microsoft Outlook via COM para:

* Envio de e-mails
* Templates
* Atualizações
* Encerramento de Operations
* Convites de calendário

Todos os templates deverão possuir versão em Português e Inglês.

---

# 10. Internacionalização

Idiomas suportados na V1:

* Português (Brasil)
* Inglês

Arquitetura preparada para:

* Chinês Simplificado
* Espanhol
* Francês

Os valores armazenados no banco utilizarão identificadores técnicos (ex.: `IN_PROGRESS`), enquanto a interface exibirá o texto traduzido conforme o idioma selecionado.

---

# 11. Princípios do Projeto

* Zero Retrabalho
* Auditoria Total
* Configuração antes de Programação
* Soft Delete
* Arquitetura Modular
* Orientação a Eventos
* Escalabilidade
* Simplicidade Operacional

---

# 12. Tecnologias

## Backend

* Python
* Flask
* Flask-SocketIO
* SQLAlchemy
* PostgreSQL
* APScheduler

## Frontend

* PySide6
* Qt Designer

## Comunicação

* Socket.IO
* REST API

## Servidor

* Windows
* Dell G15

---

# 13. Roadmap

## Sprint 0

Infraestrutura.

## Sprint 1

Operations.

## Sprint 2

Assets.

## Sprint 3

Synchronization.

## Sprint 4

Dashboard.

## Sprint 5

Reports.

## Sprint 6

Knowledge Base.

## Sprint 7

Administração.

---

# Aprovação

Este documento servirá como base oficial para a arquitetura, modelagem do banco de dados e desenvolvimento da primeira versão do AssetOps.
