# 📈 Générer, transformer et manipuler un fichier Parquet (Big Data) via Polars & interconnexion avec DuckDB pour exécuter des requêtes SQL


## Démarche

Dans ce notebook ci-joint, nous allons mettre en pratique l’ensemble des points abordés ci-dessous.




## Polars : un package Python plus performant que Pandas et permettant de manipuler les données tabulaires à partir de différents types de fichiers tels que Parquet, CSV

Polars est un package Python permettant de manipuler les données tabulaires à partir de différents types de fichiers (CSV, Parquet, etc.).
Il est une alternative directe et moderne à Pandas, pensée pour être très performante tout en offrant une syntaxe compréhensible à pour des data scientists habitués à d’autres frameworks de manipulation de données comme dplyr.




## Les fichiers Parquet ont un format optimisé pour stocker et interroger de façon efficace du Big Data

Les fichiers Parquet ont un format binaire beaucoup plus léger que les fichiers CSV pour le stockage des tableaux de données.
Ex : faire une requête SQL quasi instantanée sur des millions de lignes répartis sur différents fichiers parquets
En effet, aujourd'hui le format parquet est utilisé en big data pour stocker et interroger de façon efficace des données volumineuses grâce à un modèle orienté colonne basée sur Apache Arrow. À cela, s'ajoute de nouveaux outils en Python pour pouvoir manipuler et interroger ces fichiers.



## Architecture d'un fichier parquet : Base de données orientée colonnes

Dans un fichier parquet, ce sont les colonnes qui sont sauvegardées de manière contiguë (collé) en mémoire.
Ceci permet de faire des opérations de façon très efficace sur les colonnes au détriment des opérations transactionnelles. Cette architecture est très performante pour des systèmes OLAP (OnLine Analytical Processing). Par exemple un entrepôt de données destinés à être lu uniquement.




## Le format parquet, développé par Apache, est entièrement compatible avec Arrow

Apache Arrow est un format standard de donnée orienté colonne pour la mémoire vive. C'est-à-dire qu'il décrit, indépendamment du langage de programmation,comment représenter un tableau dans votre RAM.
Par exemple, si vous manipulez les mêmes données stockées dans un DataFrame Python ou un DataFrame R, la structure mémoire sous-jacent sera la même. Autrement dit, vous allez pouvoir transférer un DataFrame Python vers un DataFrame R, sans faire la moindre copie ou transformation. Et lorsque l'on travaille avec beaucoup de données, cela est loin d'être négligeable.

Le format parquet, développé par Apache, est entièrement compatible avec Arrow. La sérialisation et la déserialisation d'un DataFrame, c'est à dire l'écriture et la lecture d'un fichier parquet sera très performante avec un minimum de transformation.

Sans Arrow, il est nécessaire de faire des conversions et des copies coûteuses entre les différentes sources de données. Le format mémoire agnostique d'Apache Arrow permet d'éviter toutes ces opérations coûteuses

Sans Arrow, il est nécessaire de faire des conversions et des copies coûteuses entre les différentes sources de données. Le format mémoire agnostique d'Apache Arrow permet d'éviter toutes ces opérations coûteuses




## Une interconnexion avec DuckDB pour faire des requêtes SQL

Polars s’appuie sur Apache Arrow, un écosystème pour lire des données (CSV ou Parquet) de manière très efficace et les stocker dans des objets peu volumineux pour gagner en performance. C’est également le cas d’une autre librairie intéressante pour le traitement de données: DuckDB.

Plutôt que concurrentes, ces deux librairies sont très complémentaires. Il est possible d’effectuer des requêtes SQL depuis un DataFrame Polars via DuckDB ou d’utiliser DuckDB pour lire les données et convertir celles-ci en DataFrame Polars à l’issue des requêtes. Ces deux approches sont intéressantes pour les personnes familières avec le langage SQL.

