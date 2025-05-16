## Guia para Criar e Configurar VMs no Azure

Este documento fornece um resumo completo do processo de criação e configuração de máquinas virtuais (VMs) no Microsoft Azure, juntamente com anotações e dicas práticas.

### 1. Criação de uma Máquina Virtual

O processo de criação de uma VM no Azure envolve os seguintes passos:

#### 1.1 Acessar o Portal do Azure

* Faça login no portal do Azure ([https://portal.azure.com/](https://portal.azure.com/)).
* Navegue até o serviço "Máquinas Virtuais".

#### 1.2 Configuração Básica

* **Assinatura:** Selecione a assinatura do Azure na qual a VM será criada.
* **Grupo de recursos:** Crie um novo grupo de recursos ou selecione um existente para organizar os recursos relacionados.
* **Nome da máquina virtual:** Forneça um nome exclusivo para a VM.
* **Região:** Escolha a região do Azure onde a VM será implantada. A proximidade aos usuários e a disponibilidade de serviços são fatores importantes a considerar.
* **Opções de disponibilidade:**
    * **Conjunto de disponibilidade:** Para alta disponibilidade, distribua as VMs em vários domínios de falha e domínios de atualização.
    * **Zonas de disponibilidade:** Para maior resiliência, distribua as VMs em zonas de disponibilidade físicas separadas dentro de uma região.
    * **Conjunto de dimensionamento de máquinas virtuais:** Para escalar horizontalmente as VMs, crie um conjunto de dimensionamento que possa aumentar ou diminuir automaticamente o número de instâncias.
* **Imagem:** Selecione o sistema operacional para a VM (Windows Server, Ubuntu, etc.). O Azure Marketplace oferece uma variedade de imagens pré-configuradas.
* **Arquitetura**: Escolha entre as arquiteturas de 64 bits (x64) e ARM64.
* **Tamanho:** Selecione o tamanho da VM, que determina os recursos de hardware (CPU, memória, armazenamento). O Azure oferece vários tamanhos otimizados para diferentes cargas de trabalho.

#### 1.3 Disco

* **Tipo de disco do sistema operacional:**
    * **SSD Premium:** Para cargas de trabalho de alto desempenho com baixa latência.
    * **SSD Padrão:** Para cargas de trabalho da Web e aplicativos com requisitos de E/S moderados.
    * **HDD Padrão:** Para cargas de trabalho com requisitos de E/S pouco frequentes e armazenamento de dados de longo prazo.
* **Criar um novo disco:** Anexe discos de dados adicionais à VM para armazenamento de aplicativos e dados.

#### 1.4 Rede

* **Rede virtual:** Selecione uma rede virtual existente ou crie uma nova para isolar a VM logicamente.
* **Sub-rede:** Segmente a rede virtual em sub-redes para organizar os recursos e melhorar a segurança.
* **Endereço IP público:** Atribua um endereço IP público à VM para permitir a conectividade da Internet. Considere as implicações de segurança e os custos.
* **NIC de rede:** Configure a interface de rede da VM, incluindo o grupo de segurança de rede (NSG) para controlar o tráfego de rede.

#### 1.5 Gerenciamento

* **Login com uma conta de administrador local:**
    * **Nome de usuário:** Forneça um nome de usuário para a conta administrativa na VM.
    * **Senha:** Defina uma senha forte para a conta administrativa.
* **Chaves SSH:** Para VMs Linux, use chaves SSH para autenticação mais segura. Gere um par de chaves e forneça a chave pública.
* **Gerenciamento:**
    * **Habilitar login com Azure AD:** Habilite o login com o Azure Active Directory para gerenciar VMs Windows com credenciais do Azure AD.
    * **Selecionar grupo de administração de convidados**
* **Monitoramento:**
    * **Diagnóstico de inicialização:** Habilite os diagnósticos de inicialização para solucionar problemas de inicialização da VM.
    * **Diagnósticos do sistema operacional:**
* **Identidade:**
    * **Habilitar identidade gerenciada:**

#### 1.6 Opções avançadas

* **Extensões:** Instale extensões de VM para habilitar funcionalidades adicionais, como configuração de estado desejado, software antivírus e outras ferramentas.
* **Dados personalizados:** Forneça scripts Cloud-init (para Linux) ou PowerShell DSC (para Windows) para automatizar a configuração da VM após a criação.

#### 1.7 Tags

* Aplique tags à VM para organizar os recursos, gerenciar os custos e simplificar o gerenciamento.

#### 1.8 Revisar e criar

* Revise todas as configurações e valide a configuração da VM.
* Clique em "Criar" para implantar a VM.

### 2. Conexão à Máquina Virtual

Depois que a VM estiver em execução, você poderá se conectar a ela usando os seguintes métodos:

* **RDP (Protocolo de área de trabalho remota):** Para VMs Windows, use um cliente RDP para se conectar usando o endereço IP público ou privado.
* **SSH (Shell seguro):** Para VMs Linux, use um cliente SSH para se conectar usando o endereço IP público ou privado. Use a chave privada correspondente para autenticação.
* **Azure Bastion:** Para conectividade RDP/SSH segura diretamente através do portal do Azure, use o Azure Bastion. Isso elimina a necessidade de expor a VM à Internet.

### 3. Configuração da Máquina Virtual

Depois de se conectar à VM, você pode configurá-la ainda mais de acordo com seus requisitos:

* Instale o software e os aplicativos necessários.
* Configure as configurações de rede, incluindo firewalls e DNS.
* Configure o armazenamento, incluindo a criação de volumes e a montagem de sistemas de arquivos.
* Ajuste o desempenho do sistema operacional e dos aplicativos.
* Implemente medidas de segurança, como instalar software antivírus e configurar regras de firewall.

### 4. Administração da Máquina Virtual

O Azure fornece várias ferramentas e serviços para administrar as VMs:

* **Portal do Azure:** Gerencie as VMs através da interface da Web, incluindo iniciar, parar, reiniciar e excluir VMs.
* **CLI do Azure:** Automatize o gerenciamento de VMs usando a interface de linha de comando.
* **Azure PowerShell:** Automatize o gerenciamento de VMs usando scripts do PowerShell.
* **Modelos do Azure Resource Manager (ARM):** Defina a infraestrutura da VM como código e automatize as implantações.

### 5. Monitoramento da Máquina Virtual

Monitore o desempenho e a saúde das VMs usando as ferramentas do Azure:

* **Azure Monitor:** Colete e analise métricas, logs e eventos da VM. Configure alertas para notificações proativas.
* **Azure Log Analytics:** Colete e analise dados de log para solucionar problemas e obter insights.

### 6. Segurança da Máquina Virtual

Implemente as melhores práticas de segurança para proteger as VMs:

* Use senhas fortes ou autenticação baseada em chave para acesso à VM.
* Habilite firewalls e grupos de segurança de rede (NSGs) para controlar o tráfego de rede.
* Mantenha o sistema operacional e o software atualizados com os patches de segurança mais recentes.
* Instale software antivírus e antimalware.
* Considere usar o Azure Security Center para gerenciamento de segurança centralizado e detecção de ameaças.
* Use a criptografia de disco do Azure para criptografar os discos da VM em repouso.

### 7. Backup e recuperação de desastres

Implemente uma estratégia de backup e recuperação de desastres para garantir a continuidade dos negócios:

* **Backup do Azure:** Faça backup das VMs no Azure para protegê-las contra perda de dados.
* **Recuperação de site do Azure:** Habilite a replicação de VMs para uma região secundária do Azure para recuperação de desastres.

### 8. Escalonamento de máquinas virtuais

Escalone as VMs para atender às demandas de aplicativos em constante mudança:

* **Escalonamento vertical:** Altere o tamanho de uma VM para adicionar mais recursos (CPU, memória).
* **Escalonamento horizontal:** Adicione mais instâncias de VM através de conjuntos de dimensionamento de máquinas virtuais.
* **Escalonamento automático:** Configure o escalonamento automático para ajustar dinamicamente o número de instâncias de VM com base na carga.

### 9. Otimização de custos

Otimize os custos das VMs do Azure:

* **Redimensione as VMs:** Escolha o tamanho de VM apropriado para corresponder aos requisitos da carga de trabalho.
* **Desligue as VMs quando não estiverem em uso:** Desative as VMs não críticas durante as horas de pico.
* **Instâncias reservadas:** Para cargas de trabalho de longo prazo, considere comprar instâncias reservadas para economizar até 72% em comparação com os preços pagos conforme o uso.
* **Instâncias spot:** Para cargas de trabalho tolerantes a interrupções, use instâncias spot para aproveitar os preços com grandes descontos.
* **Benefício híbrido do Azure:** Use suas licenças locais do Windows Server para economizar custos.

### 10. Solução de problemas da máquina virtual

Aqui estão algumas dicas para solucionar problemas comuns de VM:

* **Problemas de conexão:**
    * Verifique a conectividade de rede, NSGs e endereços IP públicos.
    * Verifique se o serviço RDP ou SSH está em execução na VM.
    * Verifique se há regras de firewall bloqueando o tráfego.
    * Use o Azure Bastion para descartar problemas relacionados à exposição da VM à Internet.
* **Problemas de inicialização da VM:**
    * Revise os diagnósticos de inicialização no portal do Azure para verificar se há erros.
    * Tente reimplantar a VM.
    * Verifique o status dos serviços do Azure.
* **Problemas de desempenho:**
    * Monitore o uso de CPU, memória, disco e rede usando o Azure Monitor.
    * Redimensione a VM ou ajuste os aplicativos para otimizar o desempenho.
* **Problemas de autenticação:**
    * Verifique as credenciais (nome de usuário e senha) ou a configuração da chave SSH.
    * Se estiver usando o Azure AD, verifique se a VM está associada a um domínio e se a autenticação do Azure AD está configurada corretamente.

### 11. Melhores práticas

* Siga o princípio do menor privilégio ao atribuir permissões às VMs.
* Automatize as implantações de VM usando modelos do ARM ou ferramentas de infraestrutura como código (IaC), como o Terraform.
* Use o Azure Policy para aplicar padrões de conformidade e governança.
* Implemente uma estratégia centralizada de gerenciamento de logs usando o Azure Monitor.
* Use o Azure Update Management para gerenciar as atualizações do sistema operacional.


## Resumo do que aprendi sobre o painel do Azure. Durante o primeiro laboratório AZ-900 no Bootcamp Bradesco - Java Cloud Native da Dio.

O painel do Azure é a interface principal para acessar e gerenciar os serviços e recursos da plataforma de nuvem da Microsoft. O menu do painel oferece várias categorias para organizar e facilitar a navegação. Este resumo fornece uma visão geral das seções mais relevantes que chamaram minha atenção como desenvolvedor.

### Configuração

A seção **Configuração** permite personalizar minha experiência no Azure, incluindo:

* **Assinaturas:** Gerencio minhas assinaturas do Azure, que são contêineres para recursos relacionados e usados para fins de faturamento.
* **Usuários e grupos:** Controlo o acesso aos recursos do Azure, atribuindo permissões a usuários e grupos.
* **Faturamento:** Monitorizo e gerencio os custos de meus serviços do Azure.
* **Configuração:** Defino as preferências globais para o portal do Azure.

### Serviços de Armazenamento

Os **Serviços de Armazenamento** do Azure oferecem soluções escalonáveis e seguras para diversos tipos de dados:

* **Contas de armazenamento:** Contêineres de nível superior para serviços de armazenamento.
* **Blobs:** Armazenamento de objetos para dados não estruturados, como texto e arquivos binários.
* **Arquivos:** Compartilhamentos de arquivos gerenciados para aplicativos legados.
* **Filas:** Filas de mensagens para comunicação assíncrona.
* **Tabelas:** Armazenamento NoSQL para dados estruturados.
* **Discos:** Volumes de armazenamento em nível de bloco para máquinas virtuais.

### Serviços de Computação

Os **Serviços de Computação** do Azure fornecem a infraestrutura para executar meus aplicativos:

* **Máquinas Virtuais:** Servidores virtuais sob demanda para executar cargas de trabalho do Windows e Linux.
* **Serviço de Aplicativo:** Plataforma totalmente gerenciada para hospedar aplicativos da Web.
* **Funções:** Plataforma de computação sem servidor.
* **Instâncias de Contêiner:** Executo contêineres do Docker sem gerenciar VMs.
* **Kubernetes:** Orquestração de contêineres gerenciada.
* **Lote:** Processamento em lote para computação em escala.

### Versão Prévia de Produtos

O Azure geralmente oferece **Versões Prévia de Produtos**, que são novos serviços ou recursos que ainda estão em desenvolvimento e teste. Eles me permitem experimentar as inovações mais recentes antes do lançamento oficial. Lembro-me de que as versões prévias podem estar sujeitas a alterações, não são recomendadas para produção e podem não ter suporte completo.
