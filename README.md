---

# 🐧 Instalação e Configuração do FTP no Ubuntu via VirtualBox

Este guia ensina como instalar e configurar um servidor **FTP** no Ubuntu Linux em uma máquina virtual utilizando o **VirtualBox**, com acesso via Windows Explorer.

---

## 🧰 Pré-requisitos

* Ubuntu instalado em uma máquina virtual via **VirtualBox**
* Acesso à internet
* VirtualBox instalado no Windows

---

## 🚀 Passo a Passo

### 1. Configurar o Modo de Rede no VirtualBox

Antes de iniciar a VM, vá até as **Configurações da máquina virtual** > **Rede** e:

* Altere o modo de rede de `NAT` ou `Rede Interna` para **Adaptador em Ponte (Bridged Adapter)**
* Isso permite que o Ubuntu obtenha um IP acessível diretamente pela rede local

---

### 2. Iniciar a VM e Atualizar o Sistema

Com a VM iniciada, abra o terminal e execute:

```bash
sudo apt-get update
```

---

### 3. Instalar o Servidor FTP

Execute o seguinte comando para instalar o `vsftpd`:

```bash
sudo apt-get install vsftpd
```

---

### 4. Verificar o Status do Serviço FTP

Após a instalação, verifique se o serviço está ativo:

```bash
sudo /etc/init.d/vsftpd status
```

---

### 5. Habilitar Escrita no Servidor FTP

Abra o arquivo de configuração:

```bash
sudo nano /etc/vsftpd.conf
```

Localize e descomente (ou adicione) a seguinte linha:

```conf
write_enable=YES
```

Salve o arquivo (`Ctrl + O`, `Enter`) e saia (`Ctrl + X`).

---

### 6. Reiniciar o Serviço

Reinicie o `vsftpd` para aplicar as mudanças:

```bash
sudo /etc/init.d/vsftpd restart
```

---

## 🖥️ Acessar o FTP pelo Windows

Com o VirtualBox rodando no Windows:

1. No terminal da VM, descubra o IP da máquina com:

   ```bash
   ip a
   ```

   Ou apenas:

   ```bash
   hostname -I
   ```

   Exemplo de IP: `192.168.0.10`

2. No Windows Explorer (atalho `Win + E`), digite na barra de endereços:

   ```
   ftp://192.168.0.10
   ```

3. Quando solicitado, insira o **nome de usuário** e a **senha** do Ubuntu

Pronto! Agora você tem acesso aos arquivos da máquina virtual via FTP diretamente do Windows.

---

## ✅ Testado em

* Ubuntu 22.04 LTS
* VirtualBox 7.x
* Windows 10 / 11

---

## 📎 Referências

* [Documentação oficial do vsftpd](https://security.appspot.com/vsftpd.html)
* [Guia VirtualBox - Rede Bridged](https://www.virtualbox.org/manual/ch06.html)

---
