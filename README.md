# EXO_MODELS

* __Les differents champs de models django__

Les differents types de champs en Django sont:

. __AutoField__ : Un champ IntegerField qui incrémente automatiquement sa valeur par rapport aux identifiants disponibles.Il est utiliser pour les chapms id

. __BigAutoField__ : Un entier 64 bits, ressemblant à un AutoField sauf qu’il garantit la couverture des nombres de 1 à 9223372036854775807.

. __BigIntegerField__ : Un entier 64 bits, ressemblant à un IntegerField sauf qu’il garantit la couverture des nombres de -9223372036854775808 à 9223372036854775807. Le composant de formulaire par défaut de ce champ est un TextInput.

. __BinaryField__ : Un champ pour stocker des données binaires brutes. Il peut recevoir des données de type bytes, bytearray ou memoryview.

. __BooleanField__ : Le composant de formulaire par défaut de ce champ est un CheckboxInput, ou NullBooleanSelect si null=True.

La valeur par défaut de BooleanField est None lorsque Field.default n’est pas défini.

. __CharField__ : Un champ pour les chaînes de caractères, courtes ou longues.
Pour une grande quantité de texte, utilisez TextField.

. __DateField__ : Une date, représentée en Python par une instance de datetime.date. Accepte quelques paramètres supplémentaires et facultatifs. Il a plusieurs attributs tel que auto_now, auto_now_add

. __DateTimeField__ : Une date et une heure, représentées en Python par une instance de datetime.datetime. Ce champ accepte les mêmes paramètres supplémentaires que le champ DateField.

. __DecimalField__ : Un nombre décimal de taille fixe, représenté en Python par une instance de Decimal. Les saisies sont validées en utilisant DecimalValidator.
Il requiert deux paramètres obligatoires : DecimalField.max_digits et DecimalField.decimal_places

. __DurationField__ : Un champ pour stocker des périodes de temps, représentées en Python par des objets timedelta. Avec PostgreSQL, le type de données utilisé est un interval et avec Oracle, le type de données est INTERVAL DAY(9) TO SECOND(6). Sinon, c’est un grand nombre entier bigint de microsecondes qui est utilisé.

. __EmailField__ : Un champ CharField qui vérifie que sa valeur est une adresse électronique valide en utilisant EmailValidator.

. __FileField__ : Un champ de fichier à téléverser. Il possède plusieurs attribut dont notamement : 
- upload_to :Cet attribut permet de définir le répertoire de téléversement et le nom de fichier.
- storage : Un objet de stockage, qui prend en charge l’enregistrement et la récupération des fichiers.

. __FilePathField__ : Un CharField dont les choix sont limités aux noms de fichiers dans un répertoire déterminé du système de fichiers. Il possède trois paramètres spéciaux, dont le premier est obligatoire :
- FilePathField.path :Obligatoire. Le chemin d’accès absolu vers le répertoire dont le contenu fournit la source des choix du FilePathField.
- FilePathField.match : Facultatif. Une expression régulière sous forme de chaîne de caractères qui sera utilisée par FilePathField pour filtrer les noms de fichier.

. __FloatField__ : Un nombre flottant représenté en Python par une instance de float.

. __ImageField__ : Hérite de tous les attributs et méthodes de FileField, mais valide également que l’objet téléversé est une image valide. En complément des attributs spéciaux disponibles pour FileField, un champ ImageField possède aussi les attributs height et width.

. __IntegerField__ : Un nombre entier. Les valeurs de -2147483648 à 2147483647 sont acceptées par toutes les base de données prises en charge par Django.

. __GenericIPAddressField__ :Une adresse IPv4 ou IPv6 au format textuel (par ex. 192.0.2.30 ou 2a02:42fe::4). Le composant de formulaire par défaut de ce champ est un TextInput. il possede deux attributs : protocol qui de difinit le protocole accepté et unpack_ipv4 

. __NullBooleanField__ : Comme BooleanField avec null=True. Utilisez ce dernier à la place de ce champ car il est probable qu’il sera rendu obsolète dans une prochaine version de Django.

. __PositiveIntegerField__ : Comme un champ IntegerField, mais doit être un entier positif ou zéro (0). Les valeurs de 0 à 2147483647 sont acceptées par toutes les base de données prises en charge par Django. La valeur 0 est acceptée pour des raisons de rétrocompatibilité.

. __PositiveSmallIntegerField__ : Comme un PositiveIntegerField, mais n’autorise que des valeurs plus petites qu’un certain plafond (dépendant du moteur de base de données). Toutes les valeurs de 0 à 32767 sont acceptées par toutes les bases de données prises en charge officiellement par Django.

. __SlugField__ : Slug est un terme anglophone de journalisme. Un slug est une brève étiquette d’un contenu, composée uniquement de lettres, de chiffres, de soulignements ou de tirets. Ils sont généralement utilisés dans les URL.

. __SmallIntegerField__ : Comme un IntegerField, mais n’autorise que des valeurs plus petites qu’un certain plafond (dépendant du moteur de base de données). Toutes les valeurs de -32768 jusqu’à 32767 sont acceptées par toutes les bases de données prises en charge officiellement par Django.

. __TextField__ : Un champ de texte long. Le composant de formulaire par défaut de ce champ est un Textarea.

. __TimeField__ : Une heure, représentée en Python par une instance de datetime.time. Ce champ accepte les mêmes options d’auto-complétion qu’un champ DateField.

. __URLField__ : Un champ CharField pour les URL, validé par URLValidator.

. __UUIDField__ : Un champ pour stocker des identifiants universels uniques (UUID). Utilise la classe Python UUID. Avec PostgreSQL, le type de données uuid est employé, sinon c’est un type char(32).


* __Migrate and migrations__
Les migrations sont le moyen utilisé par Django pour propager les modifications apportées à vos modèles (ajout d'un champ, suppression d'un modèle, etc.) dans le schéma de votre base de données. Ils sont conçus pour être généralement automatiques, mais vous aurez besoin de savoir quand effectuer les migrations, quand les exécuter et les problèmes courants que vous pourriez rencontrer.
Il existe plusieurs commandes que vous utiliserez pour interagir avec les migrations et la gestion du schéma de base de données par Django:
- migrate, responsable de l’application et de la non application des migrations.
- makemigrations, responsable de la création de nouvelles migrations en fonction des modifications apportées à vos modèles. -
_ sqlmigrate, qui affiche les instructions SQL d’une migration.
_ showmigrations, qui répertorie les migrations d’un projet et leur statut.
Vous devez considérer les migrations comme un système de contrôle de version pour votre schéma de base de données. makemigrationsest responsable de la compression de vos modifications de modèle dans des fichiers de migration individuels - de la même manière que les validations - et migrateest responsable de leur application à votre base de données.
Les fichiers de migration de chaque application résident dans un répertoire «migrations» à l'intérieur de cette application et sont conçus pour être validés et distribués dans le cadre de sa base de code. Vous devriez les créer une fois sur votre machine de développement, puis exécuter les mêmes migrations sur les machines de vos collègues, vos machines de transfert et, éventuellement, vos machines de production.

