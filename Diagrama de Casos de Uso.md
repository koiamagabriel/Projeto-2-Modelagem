# Projeto-2---Grupo-L

## UC_01 — Autenticar no Sistema

Função: Permitir o acesso ao sistema de controle e exibir o último login.<br>
Atores: Administrador<br>
Prioridade: Essencial<br>
Pré-condição: Usuário cadastrado e ativo.<br>
Pós-condição: Sessão aberta com perfil de autorização carregado; último login exibido/atualizado.

Fluxo Principal<br>
 • Administrador informa credenciais.<br>
 • Sistema valida credenciais e status ativo.<br>
 • Sistema exibe data/hora do último login.<br>
 • Sistema abre sessão e carrega autorizações.
 
Fluxo Secundário [FS001]<br>
 • Credenciais inválidas → negar acesso e informar.
 
Fluxo Secundário [FS002]<br>
 • Usuário inativo/bloqueado → negar e orientar contato com responsável.

---

## UC_02 — Gerenciar Usuários e Autorizações

Função: Incluir, editar, desativar usuários e seus níveis de autorização.<br>
Atores: Administrador<br>
Prioridade: Importante<br>
Pré-condição: UC_01 concluído; perfil com permissão de gestão.<br>
Pós-condição: Base de usuários/autorizações atualizada.

Fluxo Principal<br>
 • Administrador lista usuários.<br>
 • Administrador inclui/edita dados e perfis.<br>
 • Sistema valida e grava alterações.<br>
 • Sistema confirma operação.
 
Fluxo Secundário [FS001]<br>
 • Login duplicado → impedir inclusão e informar.
 
Fluxo Secundário [FS002]<br>
 • Perfil inválido → bloquear e solicitar correção.

---

## UC_03 — Configurar Rede de Elevadores

Função: Definir quantidade de elevadores por unidade e faixas de andares por grupo (máx. 12 andares por grupo).<br>
Atores: Administrador<br>
Prioridade: Essencial<br>
Pré-condição: UC_01 concluído.<br>
Pós-condição: Configuração salva e aplicada aos controladores da unidade.

Fluxo Principal<br>
 • Administrador seleciona a unidade.<br>
 • Informa quantidade de elevadores e mapeia grupos de andares.<br>
 • Sistema valida regras (12 andares/grupo, sem sobreposição).<br>
 • Sistema grava e confirma.
 
Fluxo Secundário [FS001]<br>
 • Grupo com mais de 12 andares → impedir gravação e informar regra.
 
Fluxo Secundário [FS002]<br>
 • Faixas sobrepostas/inconsistentes → impedir e solicitar ajuste.

---

## UC_04 — Cadastrar VIP e Hóspedes VIP

Função: Definir andares VIP e cadastrar hóspedes VIP (com vínculo de reconhecimento facial no check-in).<br>
Atores: Administrador<br>
Prioridade: Importante<br>
Pré-condição: UC_01; unidade configurada (UC_03).<br>
Pós-condição: Andares VIP e hóspedes VIP registrados.

Fluxo Principal<br>
 • Administrador marca/edita andares VIP.<br>
 • Registra hóspede VIP (dados e imagens).<br>
 • Sistema valida e salva.
 
Fluxo Secundário [FS001]<br>
 • Captura/arquivo de imagem inválido → solicitar nova coleta.
 
Fluxo Secundário [FS002]<br>
 • Hóspede não elegível → negar e informar.

---

## UC_05 — Atender Chamada Externa

Função: Atender chamadas em botoeira externa (seleção de destino fora da cabine), indicando elevador e sentido.<br>
Atores: Hóspede<br>
Prioridade: Essencial<br>
Pré-condição: UC_03 concluído; elevadores operacionais.<br>
Pós-condição: Chamada enfileirada, elevador selecionado e atendimento iniciado.

Fluxo Principal<br>
 • Hóspede seleciona destino na botoeira externa.<br>
 • Sistema escolhe elevador conforme grupo e disponibilidade.<br>
 • Sistema indica elevador e sentido no painel externo.<br>
 • Elevador desloca e atende.
 
Fluxo Secundário [FS001]<br>
 • Nenhum elevador disponível → manter na fila e priorizar quando possível.
 
Fluxo Secundário [FS002]<br>
 • Indicador externo indisponível → prosseguir atendimento e registrar anomalia.

---

## UC_06 — Operar Cabine

Função: Registrar seleção de andares na cabine, respeitando VIP e controle de carga; exibir posição e paradas.<br>
Atores: Hóspede<br>
Prioridade: Essencial<br>
Pré-condição: Cabine em operação; sensores ativos; andares VIP definidos.<br>
Pós-condição: Deslocamento executado com segurança; acessos VIP respeitados.

Fluxo Principal<br>
 • Hóspede seleciona andar na cabine.<br>
 • Sistema exibe andar atual e paradas previstas no display interno.<br>
 • Para andar VIP, sistema realiza verificação correspondente.<br>
 • Sistema verifica carga; se adequada, movimenta cabine e realiza paradas.
 
Fluxo Secundário [FS001]<br>
 • Acesso VIP negado → impedir parada VIP e informar.
 
Fluxo Secundário [FS002]<br>
 • Carga excedida → emitir aviso, bloquear movimento até normalização.

---

## UC_07 — Responder a Incêndio

Função: Em incêndio, conduzir elevadores ao térreo e abrir portas.<br>
Atores: Administrador<br>
Prioridade: Essencial<br>
Pré-condição: Sistema em operação.<br>
Pós-condição: Elevadores no térreo, portas abertas, modo emergência ativo.

Fluxo Principal<br>
 • Sistema detecta incêndio (ou comando do Administrador).<br>
 • Cancela filas e comanda descida ao térreo.<br>
 • Abre portas e sinaliza estado de emergência.
 
Fluxo Secundário [FS001]<br>
 • Falha em um elevador → sinalizar e orientar evacuação por escadas.

---

## UC_08 — Responder a Outras Emergências

Função: Em emergência não-incêndio, parar no andar mais próximo, abrir portas e suspender operação.<br>
Atores: Administrador<br>
Prioridade: Essencial<br>
Pré-condição: Sistema em operação.<br>
Pós-condição: Cabine parada e indisponível após evacuação.

Fluxo Principal<br>
 • Sistema detecta emergência.<br>
 • Para no andar mais próximo e abre portas.<br>
 • Após evacuação, fecha portas e imobiliza.
 
Fluxo Secundário [FS001]<br>
 • Porta obstruída → emitir alerta e instruir remoção da obstrução.

---

## UC_09 — Visualizar Status dos Elevadores

Função: Exibir posição, direção, filas de chamadas e alertas (indicadores internos/externos).<br>
Atores: Administrador<br>
Prioridade: Importante<br>
Pré-condição: UC_01; telemetria ativa.<br>
Pós-condição: Painel atualizado exibido ao Administrador.

Fluxo Principal<br>
 • Administrador abre painel.<br>
 • Sistema mostra posição, direção e filas por elevador.<br>
 • Sistema destaca alertas/anomalias.
 
Fluxo Secundário [FS001]<br>
 • Sem telemetria de um elevador → exibir alerta e sugestão de checagem.

---

## UC_10 — Auditar Logs

Função: Consultar/filtrar/exportar logs auditáveis das ações de controle.<br>
Atores: Administrador<br>
Prioridade: Importante<br>
Pré-condição: UC_01; perfil autorizado.<br>
Pós-condição: Registros exibidos e, quando solicitado, exportados.

Fluxo Principal<br>
 • Administrador define filtros (período, usuário, ação).<br>
 • Sistema lista logs e permite exportar.
 
Fluxo Secundário [FS001]<br>
 • Intervalo sem registros → exibir “sem dados” e sugerir ajuste de filtros.

# Diagrama de casos de uso

<img src="https://github.com/koiamagabriel/Projeto-2-Modelagem/blob/main/DiagramaCasosUso.png"
     alt="Diagrama de sequencia 2">
