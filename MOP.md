composer create-project symfony/skeleton nom_projet
symfony server:start
composer require --dev symfony/profiler-pack
configruration docker (BDD)
fournir compose.yml
Variables d'environnement
POSTGRES_USER=db_user
POSTGRES_PASSWORD=12345
POSTGRES_DB=api_test
POSTGRES_HOST=db_api_test
docker compose up -d : 2 services (mail + postgres)
composer require symfony/orm-pack
.env : DATABASE_URL="postgresql://db_user:12345@127.0.0.1:5440/api_test?serverVersion=16&charset=utf8"
php bin/console doctrine:database:create => optionnel si docker
composer require symfony/maker-bundle --dev
php bin/console make:entity
php bin/console make:migration
php bin/console doctrine:migrations:migrate => php bin/console d:m:m
composer require easycorp/easyadmin-bundle
php bin/console make:admin:dashboard
a - créer "templates/admin/index.html.twig"
b - décomenter "return $this->render('admin/index.html.twig');" dans le DashboardController
c - ajouter : {% extends '@EasyAdmin/page/content.html.twig' %}

php bin/console make:admin:crud
lien dans dashboard : yield MenuItem::linkToCrud('Tests', 'fa-solid fa-user', Test::class);
passage fr : config/packages/translation.yaml

composer require symfony/validator : ex => EMAIL #[Assert\Email] #[Assert\Email(message: 'Email incorrect : john@doe.fr')] => surclasser message par défaut
composer require symfony/security-bundle
php bin/console make:user
php bin/console make:migration
php bin/console doctrine:migrations:migrate

php bin/console make:registration-form
ou php bin/console security:hash-password si utilisateur créé à la main
php bin/console make:admin:crud
Dans le dashBoardController : yield MenuItem::linkToCrud('Utilisateurs', 'fa fa-user', User::class);
