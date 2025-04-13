# ![PostgreSQL](postgresql.png) **PostgreSQL**

## 📥 Installation

### 🐧 **Linux**

```bash
sudo apt install postgresql postgresql-contrib
```

```bash
sudo -i -u postgres
psql
```

### 🪟 **Windows**

[Lien de téléchargement PostgreSQL](https://www.postgresql.org/download/windows/)

## 🔧 Configuration

```SQL
CREATE USER votre_utilisateur WITH PASSWORD 'votre_mot_de_passe';
```

```SQL
CREATE USER votre_utilisateur WITH PASSWORD 'votre_mot_de_passe';
```

```SQL
GRANT ALL PRIVILEGES ON DATABASE votre_base_de_donnees TO votre_utilisateur;
```

## ![SQL](sql.png) **Commandes SQL**

**Création de table :**

```SQL
CREATE TABLE "User"(
   user_id UUID PRIMARY KEY,
   user_name VARCHAR(20) NOT NULL UNIQUE,
   user_mail VARCHAR(64) NOT NULL UNIQUE,
   user_password VARCHAR(128) NOT NULL
);
```

**Insérer dans une table :**

```SQL
INSERT INTO "User" (user_id, user_name, user_mail, user_password)
VALUES (
   gen_random_uuid(),
   'axel',
   'axel@mail.com',
   'mypassword'
);
```

**Vérifier les éléments dans une table :**

```SQL
SELECT * FROM "User";
```

**Modifier des éléments dans une table :**

```SQL
UPDATE "User" SET user_mail = 'newmail@mail.com' WHERE user_name = 'axel';
```

**Supprimer une colonne précise :**

```SQL
DELETE FROM "User" WHERE user_name = 'axel';
```

**Supprimer une table :**

```SQL
DROP TABLE "User";
```

**Clé étrangère :**

```SQL
CREATE TABLE "Post"(
   post_id UUID PRIMARY KEY,
   post_title VARCHAR(50) NOT NULL,
   post_description VARCHAR(250) NOT NULL,
   user_id UUID NOT NULL UNIQUE,
   FOREIGN KEY (user_id) REFERENCES User(user_id)
);
```

_ou_

```SQL
ALTER TABLE "Post" ADD CONSTRAINT user_id FOREIGN KEY (user_id) REFERENCES "User"(user_id);
```

## 🐘 **Commandes PSQL**

| Commande        | Description                                |
| --------------- | ------------------------------------------ |
| `\l` ou `\list` | Liste les bases de données                 |
| `\c nom_base`   | Se connecter à une base                    |
| `\conninfo`     | Informations de connexion actuelles        |
| `\dt`           | Liste les tables                           |
| `\dt+`          | Liste les tables avec détails              |
| `\dv`           | Liste les vues                             |
| `\d nom_table`  | Description d’une table                    |
| `\d+ nom_table` | Détails étendus sur une table              |
| `\di`           | Liste les index                            |
| `\ds`           | Liste les séquences                        |
| `\df`           | Liste les fonctions                        |
| `\dn`           | Liste les schémas                          |
| `\du`           | Liste les rôles utilisateurs               |
| `\dx`           | Liste les extensions installées            |
| `\d`            | Liste tous les objets dans le schéma actif |
| `\d nom_objet`  | Description d’un objet                     |
