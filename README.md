shell
Copy code
# Baixe o pacote Lando
curl -sS https://lando.dev/dl/latest/linux -o lando.deb

# Instale o Lando
sudo dpkg -i lando.deb

# Verifique a instalação
lando --version
Passo 2: Configurando o projeto Drupal com Lando
shell
Copy code
# Crie o diretório do projeto Drupal
mkdir meu-projeto-drupal
cd meu-projeto-drupal

# Inicialize o Lando com a versão mais recente do Drupal 10
lando init --source remote --remote-url https://ftp.drupal.org/files/projects/drupal-10.x.x.tar.gz --remote-options="--strip-components 1"

# Inicie o ambiente Lando
lando start

# Baixe e descompacte o Drupal
lando composer create-project drupal/recommended-project:^10.0 meu-projeto
cd meu-projeto
Passo 3: Instalando o Drupal
shell
Copy code
# Configure o arquivo de ambiente .env
lando info  # Copie as informações do banco de dados e atualize o arquivo .env

# Instale o Drupal
lando drush site:install
Passo 4: Configurando o Admin Toolbar
shell
Copy code
# Instale o Admin Toolbar
lando composer require drupal/admin_toolbar

# Ative o módulo Admin Toolbar
lando drush en admin_toolbar -y
Passo 5: Configurando o Drush
shell
Copy code
# Instale o Drush
lando composer require drush/drush

# Use o Drush globalmente
lando drush @none --root=/app/drupal/web site:install
