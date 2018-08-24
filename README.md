# Setup Laravel
#### Configurando o Homestead

1. Instalar o VirtualBox -> [Clique aqui](https://www.virtualbox.org/ "Clique aqui")
2. Instalar o Vagrant -> [Clique aqui](https://www.vagrantup.com/ "Clique aqui")
3. Instalar o Homestead -> [Clique aqui](https://laravel.com/docs/5.6/homestead "Clique aqui")
4. Configurar o **Homestead.yaml**
5. Instalar o Vagrant::Hostsupdater -> [Clique aqui](https://github.com/cogitatio/vagrant-hostsupdater "Clique aqui")

#### Iniciando um projeto Laravel
1. Instalar o Composer -> [Clique aqui](https://getcomposer.org/ "Clique aqui")
2. Instalar o Instalador do Laravel `composer global require "laravel/installer"` e dar um `laravel new nome_do_projeto` ou via Compsoer `composer create-project --prefer-dist laravel/laravel nome_do_projeto`
3. Instalar o Homestead no projeto `composer require laravel/homestead --dev`
4. Criar um arquivo **Homestead.yaml.example** para servir de base para seu arquivo **Homestead.yaml** ou depois de rodar o compando `vendor/bin/homestead` altere o arquivo gerado de acordo com suas preferências.
5. Apontar o banco no arquivo **.env.example** para o database criado no arquivo **Homestead.yaml**

```yaml
ip: 192.168.10.69
memory: 2048
cpus: 1
provider: virtualbox
authorize: ~/.ssh/id_rsa.pub
keys:
    - ~/.ssh/id_rsa
folders:
    -
        map: .
        to: /var/www/laravel_project
sites:
    -
        map: laravel_project.test
        to: /var/www/laravel_project/public
databases:
    - laravel_project
name: laravel_project
hostname: secret
```

5. Rodar o comando `vendor/bin/homestead make`
6. Subir a máquina virtual `vagrant up`

#### Utilizando o projeto
1. `composer install`
2. `vendor/bin/homestead make`
3. `sudo vi /etc/hosts`
4. `criar um host com o IP do homestead.yaml e sites: map`
5. `vagrant up`
6. `vagrant ssh`
7. `cd /vagrant`
8. `cp .env.example .env`
9. `php artisan key:generate`
10. `php artisan migrate --seed`
11. `exit`
12. `npm i`