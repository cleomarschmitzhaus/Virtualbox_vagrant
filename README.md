# Virtualbox_vagrant

### Repositório de arquivos Vagrantfile para provisionamento de ambientes

#### instalação do Virtual box
- Executar comandos como *root*.

```
dnf -y upgrade
reboot
```

- Ferramentas de Desenvolvimento necessárias para construir os módulos do kernel Linux do VirtualBox no Fedora

```
dnf -y install @development-tools
dnf -y install kernel-headers kernel-devel dkms elfutils-libelf-devel qt5-qtx11extras
```

- Adicione-o ao seu sistema Fedora usando o comando abaixo.

```
cat <<EOF | sudo tee /etc/yum.repos.d/virtualbox.repo 
[virtualbox]
name=Fedora $releasever - $basearch - VirtualBox
baseurl=http://download.virtualbox.org/virtualbox/rpm/fedora/34/\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://www.virtualbox.org/download/oracle_vbox.asc
EOF
```

- importar a chave GPG usada para assinar pacotes.

```
dnf search virtualbox
```

- Instalação do VirtualBox

```
dnf install VirtualBox-6.1
```

- Dar permissão para o grupo para poder executar o VirtualBox sem ser *root*.

```
sudo usermod -a -G vboxusers $USER
$ newgrp vboxusers
$ id $USER
```