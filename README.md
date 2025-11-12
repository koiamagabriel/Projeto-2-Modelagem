# Projeto-1---Grupo-A

## UC_01 — Preparar Eleição nas Urnas

Função: Preparar e carregar nas urnas os dados da eleição<br>
Atores: Administrador<br>
Prioridade: Essencial<br>
Pré-condição: Urnas cadastradas/validadas; base com candidatos e eleitores padronizados para todas as urnas do mesmo processo.<br>
Pós-condição: Urnas autenticadas e carregadas, prontas para operar de forma autônoma.

Fluxo Principal
 • Administrador seleciona urnas-alvo.<br>
 • Sistema valida urnas e compõe o pacote da eleição com cargos, candidatos padronizados e eleitores.<br>
 • Sistema carrega/autentica o pacote nas urnas.<br>
 • Sistema confirma conclusão.
 
Fluxo Secundário [FS001]
 • Inconsistência de dados → sistema bloqueia o carregamento e notifica.

## UC_02 — Identificar Eleitor

Função: Confirmar o número de inscrição/documento do eleitor para iniciar a votação.<br>
Atores: Eleitor<br>
Prioridade: Essencial<br>
Pré-condição: Urna carregada com listas de eleitores.<br>
Pós-condição: Eleitor identificado e liberado para votar.

Fluxo Principal<br>
 • Eleitor informa nº de inscrição/documento.<br>
 • Sistema localiza o registro e exibe identificação.<br>
 • Sistema valida elegibilidade do eleitor.
 
Fluxo Secundário [FS001]<br>
 • Documento não encontrado → negar prosseguimento; orientar atendimento.
 
Fluxo Secundário [FS002]<br>
 • Eleitor já votou → bloquear votação.

## UC_03 — Registrar Voto

Função: Permitir ao eleitor registrar seu voto para cada cargo (até 8), com confirmação e opções de corrigir, branco e nulo.<br>
Atores: Eleitor<br>
Prioridade: Essencial<br>
Pré-condição: UC_02 concluído; urna operando autonomamente após ter sido autenticada e carregada.<br>
Pós-condição: Voto do eleitor gravado; eleitor marcado como “votou”

Fluxo Principal<br>
 • Sistema apresenta a sequência de cargos .<br>
 • Para cada cargo:<br>
  – Eleitor digita o número do candidato.<br>
  – Sistema mostra dados do candidato .<br>
  – Eleitor confirma o voto.<br>
 • Ao final da sequência, sistema registra conclusão do voto do eleitor.
 
Fluxo Secundário [FS001] — Corrigir Escolha<br>
 • Antes de confirmar um cargo, eleitor solicita corrigir e digita novamente.
 
Fluxo Secundário [FS002] — Voto em Branco<br>
 • Eleitor opta por branco para o cargo atual e confirma.
 
Fluxo Secundário [FS003] — Voto Nulo<br>
 • Número digitado não corresponde a candidato válido; sistema indica nulo e permite confirmar.
 
Fluxo Secundário [FS004] — Elegibilidade negada<br>
 • Caso o sistema detecte, antes da gravação final, que o eleitor já votou , cancela o registro e orienta atendimento.

## UC_04 — Encerrar Votação e Enviar Apuração

Função: Encerrar a votação na urna e transmitir a apuração à central quando a comunicação for solicitada.<br>
Atores: Administrador<br>
Prioridade: Importante<br>
Pré-condição: Período de votação finalizado; apuração local consolidada.<br>
Pós-condição: Apuração enviada contendo total por cargo e contagens de brancos, nulos e ausentes.

Fluxo Principal<br>
 • Operador encerra a votação.<br>
 • Sistema consolida votos por cargo e contabiliza brancos, nulos e ausentes.<br>
 • Sistema solicita comunicação e envia a apuração à central.<br>
 • Sistema registra confirmação de envio/recebimento.
 
Fluxo Secundário [FS001]<br>
 • Falha de comunicação → armazenar e re-tentar até sucesso (política de reenvio).

## UC_05 — Totalizar e Divulgar Resultados

Função: Totalizar resultados por urna e no geral, gerando tabelas/gráficos.<br>
Atores: Administrador<br>
Prioridade: Importante<br>
Pré-condição: Apurações recebidas das urnas.<br>
Pós-condição: Relatórios por urna e totalizados; com brancos, nulos e ausentes.

Fluxo Principal<br>
 • Administrador escolhe o escopo.<br>
 • Sistema totaliza e produz tabelas ou gráficos.<br>
 • Sistema disponibiliza/expõe os relatórios.
 
Fluxo Secundário [FS001]<br>
 • Apuração incompleta → emitir parcial com aviso.

## Diagrama de Casos de Uso
<img src="https://github.com/koiamagabriel/Projeto-1---Grupo-A/blob/main/Diagrama%20de%20casos%20de%20uso.png" alt="Diagrama de Casos de Uso">

 


