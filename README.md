# Aula de Máquinas Virtuais (VM)

## 1. O que é uma Máquina Virtual (VM)?

Uma **Máquina Virtual (VM)** é um software que simula um computador físico dentro de outro computador. As VMs permitem que você execute sistemas operacionais e aplicativos em um ambiente isolado, o que proporciona flexibilidade, segurança e melhor utilização dos recursos do hardware.

### Principais Conceitos de Máquinas Virtuais:

- **Hypervisor**: É o software que gerencia as VMs. Ele pode ser de dois tipos:
  - **Tipo 1 (bare-metal)**: O hypervisor roda diretamente no hardware do computador. Exemplos incluem VMware ESXi e Microsoft Hyper-V.
  - **Tipo 2 (hosted)**: O hypervisor roda em cima de um sistema operacional já existente. Exemplos incluem VMware Workstation e VirtualBox.

- **Guest OS**: É o sistema operacional que roda dentro da máquina virtual. Pode ser Windows, Linux, macOS, entre outros.

- **Host OS**: É o sistema operacional no qual o hypervisor e as VMs estão sendo executados. Ele pode ser Windows, Linux, etc.

- **Snapshot**: Um snapshot é uma captura do estado da máquina virtual em um ponto no tempo. Ele pode ser usado para restaurar a VM a um estado anterior, útil para testes e desenvolvimento.

- **Resource Allocation**: Ao criar uma VM, é possível alocar recursos do sistema host para ela, como CPU, memória RAM e armazenamento.

---

## 2. Vantagens das Máquinas Virtuais

- **Isolamento**: Cada VM é isolada do sistema host e das outras VMs. Isso aumenta a segurança e a estabilidade, pois falhas ou ataques em uma VM não afetam diretamente o sistema host ou outras VMs.
  
- **Portabilidade**: Você pode mover uma VM de um host para outro com facilidade, o que torna a VM ideal para ambientes de desenvolvimento e testes.
  
- **Eficiência de Recursos**: VMs permitem usar melhor os recursos de hardware, já que você pode executar múltiplos sistemas operacionais em uma única máquina física.

- **Ambientes de Teste e Desenvolvimento**: Você pode criar ambientes de teste e desenvolvimento isolados, sem afetar o sistema principal.

---

## 3. Como Criar e Configurar uma Máquina Virtual

Agora, vamos criar uma VM simples usando o **VirtualBox**, um dos hypervisores mais populares e gratuitos.

### 3.1. Instalando o VirtualBox

Para instalar o VirtualBox, siga as instruções oficiais para seu sistema operacional:

- [Instalar o VirtualBox no Windows](https://www.virtualbox.org/wiki/Downloads)
- [Instalar o VirtualBox no macOS](https://www.virtualbox.org/wiki/Downloads)
- [Instalar o VirtualBox no Linux](https://www.virtualbox.org/wiki/Downloads)

### 3.2. Criando uma Nova Máquina Virtual

Após instalar o VirtualBox, siga os passos abaixo para criar uma nova VM:

1. Abra o VirtualBox e clique em **Novo**.
2. Dê um nome à sua VM, selecione o tipo de sistema operacional que você deseja instalar (por exemplo, Linux ou Windows) e a versão do sistema (por exemplo, Ubuntu 64-bit).
3. Atribua memória RAM à sua VM. Um valor recomendado para sistemas modernos é 2048 MB (2 GB).
4. Crie um disco rígido virtual para a VM:
   - Selecione **Criar um disco rígido virtual agora**.
   - Escolha o tipo de arquivo de disco (VHD, VDI ou VMDK).
   - Selecione o tipo de armazenamento (dinâmico ou fixo). O **dinâmico** aumenta conforme o uso, enquanto o **fixo** ocupa o espaço total imediatamente.
   - Defina o tamanho do disco virtual (por exemplo, 20 GB).

### 3.3. Instalando o Sistema Operacional na VM

Agora, que você tem uma VM configurada, vamos instalar um sistema operacional nela:

1. Selecione a VM criada no VirtualBox e clique em **Iniciar**.
2. O VirtualBox solicitará a mídia de instalação (por exemplo, uma ISO do sistema operacional que você deseja instalar).
   - Se você estiver instalando uma distribuição Linux, como o Ubuntu, baixe a ISO do site oficial [Ubuntu](https://ubuntu.com/download/desktop).
   - Para sistemas Windows, baixe uma ISO oficial do site da Microsoft.
3. Após selecionar a ISO, a VM iniciará a instalação do sistema operacional. Siga as instruções do instalador como faria em um computador físico.

### 3.4. Configurações Avançadas

Após a instalação, você pode configurar alguns aspectos da VM, como:

- **Ajustar o número de CPUs**: Vá em **Configurações** > **Sistema** > **Processador** e ajuste a quantidade de CPUs alocadas à VM.
- **Compartilhar Pastas**: Vá em **Configurações** > **Pastas compartilhadas** para compartilhar uma pasta entre o sistema host e a VM.
- **Ajustar Rede**: Vá em **Configurações** > **Rede** para configurar a rede da VM, podendo ser em modo NAT, bridge ou outras opções.

---

## 4. Comandos Básicos para Gerenciar Máquinas Virtuais

Se você estiver usando uma interface de linha de comando (CLI) como o **VBoxManage** (para VirtualBox) ou **virsh** (para KVM), aqui estão alguns comandos úteis:

### 4.1. Comandos para VirtualBox (VBoxManage)

- **Listar VMs**:
  ```bash
  VBoxManage list vms
  ```
- **Iniciar uma VM**:
  ```bash
  VBoxManage startvm "Nome_da_VM" --type headless
   ```
- **Parar uma VM**:
 ```bash
  VBoxManage controlvm "Nome_da_VM" acpipowerbutton
   ```
- **Salvar o estado de uma VM**:
 ```bash
  VBoxManage controlvm "Nome_da_VM" savestate
 ```


## 5. Vantagens e Desvantagens das VMs

### Vantagens:
- **Isolamento**: Cada VM é isolada, então qualquer problema ou falha em uma VM não afeta as outras ou o sistema hospedeiro.
- **Flexibilidade**: Você pode rodar diferentes sistemas operacionais e versões de aplicativos.
- **Eficiência no uso de recursos**: VMs permitem otimizar o uso de hardware, consolidando várias máquinas em um único servidor físico.

### Desvantagens:
- **Desempenho**: VMs podem ser mais lentas do que máquinas físicas devido à sobrecarga do hypervisor.
- **Consumo de recursos**: VMs consomem memória e CPU, o que pode ser um problema em máquinas com recursos limitados.
- **Gerenciamento**: Gerenciar múltiplas VMs pode ser complexo e requer ferramentas adequadas de automação.

---


