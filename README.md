# desafiio-criacao-configuracao-VM
Este repositório foi cuidadosamente criado para ser o seu companheiro de jornada no universo da computação em nuvem da Microsoft Azure

Chegando com mais um pedacinho da minha jornada na Azure, e dessa vez, vamos falar de algo super fundamental: as Máquinas Virtuais (VMs). Se você já trabalhou com computadores, sabe o que é ter um ambiente para instalar seus programas e rodar suas coisas. As VMs na Azure são exatamente isso, só que na nuvem! Elas te dão toda a flexibilidade de um PC ou servidor físico, mas com a superpotência e escalabilidade da Azure.
O que é uma Máquina Virtual na Azure?
Pense na VM como um computador completo, mas que existe apenas virtualmente nos datacenters da Microsoft. Você pode instalar o sistema operacional que quiser (Windows, Linux), rodar seus softwares, hospedar sites, bancos de dados – as possibilidades são gigantes! O legal é que você só paga pelo tempo que ela está ligada e pelos recursos que usa, o que é uma mão na roda para otimizar custos.
Criando Sua Primeira VM: O Processo Simplificado
Criar uma VM na Azure pode parecer um bicho de sete cabeças no começo, mas juro que é mais tranquilo do que parece. A gente vai seguir um fluxo lógico, como se estivesse montando um PC, mas com alguns detalhes de rede e segurança que são a cara da nuvem.
Vamos ver os principais passos:
 * Grupo de Recursos (Resource Group): Pense nisso como uma "caixa" onde você vai guardar tudo que se refere à sua VM: a própria VM, os discos, a rede, etc. Isso ajuda muito na organização e na hora de gerenciar seus custos.
 * Detalhes da Instância: Aqui é onde a mágica começa! Você vai dar um nome pra sua VM, escolher em qual região da Azure ela vai morar (pertinho de você ou dos seus usuários pra ter menos lag), e decidir qual sistema operacional ela vai rodar (Windows Server, Ubuntu, CentOS, etc.). Ah, e claro, o "tamanho" dela – que é basicamente a quantidade de CPU, memória e outras coisinhas que ela vai ter.
 * Administrador: Hora de criar o usuário e senha (ou chave SSH) pra você conseguir "entrar" na sua VM depois.
 * Regras de Porta de Entrada (Inbound Port Rules): Isso é super importante! É como você diz "quem pode bater na porta" da sua VM. Se for um servidor web, vai precisar liberar a porta 80 (HTTP) ou 443 (HTTPS). Se for acessar remotamente, a 3389 (RDP para Windows) ou 22 (SSH para Linux) são essenciais. Cuidado aqui, ok? Não saia liberando tudo!
 * Discos: Onde os arquivos do seu sistema operacional e seus dados vão ficar guardados. Você escolhe o tipo (SSD para velocidade, HDD para custo) e o tamanho.
 * Rede: Aqui você define a rede virtual onde sua VM vai se conectar. É tipo a sua rede Wi-Fi em casa, mas na nuvem. Você pode ter um IP público para acessá-la da internet, ou mantê-la só na sua rede interna.
 * Gerenciamento: Opções para deixar sua vida mais fácil, tipo desligar a VM automaticamente em certos horários (ótimo pra economizar!), fazer backups e monitorar o desempenho.
 * Tags: Pensa nas tags como etiquetas. Elas servem pra organizar seus recursos e até pra ajudar a controlar os gastos, categorizando o que é de qual projeto ou equipe.
 * Revisar + Criar: A Azure vai dar uma olhada em tudo que você configurou e, se estiver tudo certo, é só clicar em criar e esperar a mágica acontecer!
Mão na Massa: Criando Sua VM no Portal Azure
Vamos ver como isso se traduz nos cliques lá no portal:
 * Entrando no Portal: Primeiro de tudo, acesse o portal.azure.com e faça login.
 * Criar Recurso: Na barra de pesquisa lá em cima, digite "Máquinas Virtuais" e clique na opção que aparecer. Depois, é só ir em "+ Criar" e "Máquina virtual".
 * Configurações Básicas:
   * Assinatura e Grupo de Recursos: Escolha sua assinatura e crie um novo grupo de recursos (ex: rg-minha-vm-dio) ou selecione um existente.
   * Nome da VM: Dê um nome legal para sua VM (ex: vm-webserver-dev).
   * Região: Selecione a região que faz mais sentido para você (ex: Brazil South).
   * Imagem (Sistema Operacional): Aqui você escolhe seu OS! Windows Server 2022, Ubuntu Server 22.04 LTS... qual você prefere?
   * Tamanho: É o famoso "tamanho" da VM. Pra começar, um Standard_B2s já serve, mas se for pra algo mais parrudo, olhe as opções D ou E.
   * Autenticação: Defina um nome de usuário e uma senha forte (para Windows) ou gere um par de chaves SSH (para Linux). Não subestime a senha!
   * Portas de Entrada Pública: Para testar, pode deixar RDP (3389) para Windows ou SSH (22) para Linux. Mas lembre-se: em produção, o ideal é ser mais restritivo ou usar outras ferramentas de acesso seguro.
 * Discos: Geralmente, um SSD Standard já atende bem para o disco do sistema operacional, oferecendo um bom equilíbrio entre performance e custo. Você pode adicionar mais discos depois se precisar de espaço extra para dados.
 * Rede: A Azure geralmente configura uma Rede Virtual (VNet) e Sub-rede padrão para você. Ela também vai te dar um IP Público para acessar a VM da internet. Um Grupo de Segurança de Rede (NSG) é criado automaticamente para controlar o tráfego (aqueles "portas de entrada" que falamos).
 * Gerenciamento: Aqui é um pulo do gato para economizar! Ative o desligamento automático para sua VM desligar sozinha em horários que não está em uso (tipo fora do horário de trabalho). Isso evita que você pague por algo que não está usando.
 * Revisar + Criar: Dê aquela última olhada em tudo. Se a validação da Azure estiver verdinha, é só clicar em "Criar" e aguardar. A VM vai ser provisionada em poucos minutos.
Acessando Sua Nova VM!
Depois que a VM estiver pronta, é hora de entrar nela!
 * Para Windows (via RDP): No portal da sua VM, clique em "Conectar" e depois em "RDP". Baixe o arquivo RDP, abra-o e coloque o usuário e a senha que você definiu.
 * Para Linux (via SSH): Copie o IP público da sua VM no portal. Abra seu terminal (no Linux/macOS) ou use um cliente SSH (como PuTTY no Windows) e digite: ssh seu_usuario@IP_PUBLICO_DA_VM.
É isso! Criar e configurar VMs é um passo super importante na sua jornada Azure. Brinque bastante, explore as opções e não tenha medo de testar. A melhor forma de aprender é colocando a mão na massa!
