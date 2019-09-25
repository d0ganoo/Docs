# Présentation AWS
> 20 Septembre 2019, PCF
> Marc et Michel de Amazon

## Les grandes lignes
- Services liés à une localisation dans le monde (4 continents)
- "Shared responsability" : le client est responsable de la configuration et de "l'ouverture" des outils qu'il utilise

## Comment fonctionne une app "3 tier" typique
- App 3 tiers : DB, app (métier), web
- Amazon Virtual Private Cloud (VPC) : Réseau "local" pour les machines/ressources situées sur AWS
- Web tier : stockage dans S3 des ressources statiques et code JS + service via CDN (cloudfront)
- S3 : 99,999999999% de durabilité (11 neufs) grâce à la réplication dans différents datacenters
- App tier : ELB (Elastic Load Balancing) + EC2 (Elastic Compute Cloud) => auto scaling
- EC2 : instance "sizable" pour l'exécution du code. ex : C5n.large (famille generation capabilités . taille)
- DB tier : RDS (Relational Db Services)
- RDS : cost-efficient and resizable capacity, read replica entre Master et Standby
        -> MariaDB, MySQL, Oracle, SQL server, PostgreS, ...
        -> ou Amazon Aurora (placement des données dans la bonne région, fonctionnalités de backtracking, ...)
- AWS DMS (Database Migration Service) : réplication de database => database en env de dev synchronisée à chaud depuis la prod ?

## Continuous Integration & Continuous Delivery/Deployment
- CI/CD : Source -> Build -> Staging -> Production
- CI : Source + Build
- CD : Source + Build + Staging + Production
- CD = Continuous Delivery ou Continuous Deployment
    - Delivery = Contrôle humain avant mise en prod
    - Deployment = Déploiement en prod directement à la fin du pipe
- Pour ça : AWS Code Pipeline :
    - Source : AWS CodeCommit
    - Build : AWS CodeBuild
    - Test : AWS CodeBuild + Third Party
    - Deploy : AWS CodeDeploy
- Monitoring : AWS X-Ray et Amazon CloudWatch
- "infrastructure as code" : AWS CloudFormation (concurrent de Terraform qu'on utilise aujourd'hui)

## Du monolithe vers le micro-service
- monolithe : fait tout, pipeline de release partagé, sensible au changement
- microservice : fait une tâche, déploiements indépendants les uns des autres, moins sensible au changement
- Les micro-services sont reliés via API. On peut donc mettre ce qu'on veut derrière chaque API, travailler avec des langages et composants différents d'un service à l'autre, du moment que l'interface fonctionne correctement pour interagir avec les autres services.
    => 1 équipe et 1 pipeline de delivery par service

## Containers
- Management : Déploiement, scheduling, scaling (Amazon Elastic Container Service, Amazon Elastic Container Service for Kubernetes)
- Hosting : là où le container est éxecuté (Amazon EC2, Amazon Fargate)
- Image Registry : Stockage d'images de containers prêtes à être lancées (Amazon Elastic Container Registry)

## Serverless
- Pas d'infrastructure à gérer
- Scaling automatique
- Haute disponibilité et sécurisé
- Facturation à l'utilisation
- Différents produits serverless :
    - S3 : stockage d'objets
    - SQS (Simple Queue Service) : système de file d'attente pour stocker et récupérer des messages
    - AWS Lambda : Lancement d'un calcul ponctuel suite à un évènement donné. Conçu pour des traitements courts, timeout au bout de 15mn.
    - Amazon API Gateway : créer, publier, gérer, surveiller et sécuriser des API
    - Amazon SNS (Simple Notification Service) : pour faire un système de notifications
    - AWS Step Functions : Pour ordonnancer des traitements sur différents services AWS (EC2, Lambda, ...)



Et le mot du jour : "Leverager" à prononcer à la française :D
