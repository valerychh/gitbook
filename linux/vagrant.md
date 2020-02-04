# Vagrant

### Установка

> Предполагается, что у Вас уже установлен один из провайдеров виртуальных машин\(VirtualBox, KVM etc.\)

Устанавливаем **Vagrant**:

```bash
apt install vagrant
```

### Подготавливаем рабочее окружение

Создадим папку и перейдём в неё:

```bash
mkdir vagrant && cd vagrant
```

Инициализируем:

```bash
$ vagrant init ubuntu/eoan64
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```

> Название необходимого образа можно взять [здесь](https://app.vagrantup.com/boxes/search)

В директории появится файл **Vagrantfile** со следующим содержимым:

```bash
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/eoan64"
end
```

> Закомментированные строки удалены

> **Vagrantfile** использует язык **Ruby**. Вы можете в нём прописывать имя виртуальной машины, провайдера, задавать настройки сети и многое другое. Полную документацию можно найти [здесь](https://www.vagrantup.com/docs/vagrantfile/).

Запускаем виртуальную машину:

```bash
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'ubuntu/eoan64'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'ubuntu/eoan64' version '20190514.0.0' is up to date...
==> default: Setting the name of the VM: vagrant_default_1580826818972_50525
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default:
    default: Guest Additions Version: 4.3.40
    default: VirtualBox Version: 6.0
==> default: Mounting shared folders...
    default: /vagrant => C:/Users/valerych/vagrant
```

Подключаемся к ВМ по **ssh**:

```bash
vagrant ssh default
```

> Список полезных команд:
>
> **vagrant halt** - останавливает ВМ  
> **vagrant reload** - перезагрузить ВМ  
> **vagrant destroy** - удаляет ВМ  
> **vagrant suspend** - "замораживает" ВМ  
> **vagrant global-status** - выводит список всех ранее созданных ВМ в хост-системе  
> **vagrant box list** - список доступных \(уже добавленных\) боксов, на основе которых мы можем запускать нашу ВМ

