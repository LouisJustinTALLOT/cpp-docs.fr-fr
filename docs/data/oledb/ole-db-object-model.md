---
title: Modèle objet OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: b37205eb91317c602010a4b568057845b2345ef0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369796"
---
# <a name="ole-db-object-model"></a>Modèle objet OLE DB

Le modèle d’objet OLE DB est composé des objets ou composants suivants. Les quatre premiers objets ou composants répertoriés (sources de données, sessions, commandes et ensembles de lignes) vous permettent de vous connecter à une source de données et de la visualiser. Le reste, à commencer par les accesseurs, se rapporte au travail avec les données lorsqu’elles sont affichées.

## <a name="data-sources"></a>Sources de données

Les objets sources de données vous permettent de vous connecter à une source de données telle qu’un fichier ou un DBMS. Un objet source de données crée et gère la connexion et contient des autorisations et des authentifications d’informations (comme le nom de connexion et le mot de passe). Un objet source de données peut créer une ou plusieurs sessions.

## <a name="sessions"></a>Sessions

Une session gère une interaction particulière avec la source de données pour interroger et récupérer des données. Chaque session est une seule transaction. Une transaction est une unité de travail indivisible définie par le test ACID. Pour une définition de l’ACID, voir [Transactions](#vcconoledbcomponents_transactions).

Les sessions effectuerent des tâches importantes telles que l’ouverture de rames et le retour de l’objet source de données qui l’a créé. Les sessions peuvent également retourner les métadonnées ou les informations sur la source de données elle-même (telles que les informations de table).

Une session peut créer une ou plusieurs commandes.

## <a name="commands"></a>Commandes

Les commandes exécutent une commande de texte telle qu’une déclaration SQL. Si la commande de texte spécifie un jeu de ligne, tel qu’une déclaration SQL **SELECT,** la commande crée le jeu de ligne.

Une commande est simplement un conteneur pour une commande de texte, qui est une chaîne (comme une déclaration SQL) passée d’un consommateur à un objet source de données pour exécution par le magasin de données sous-jacent du fournisseur. Typiquement, la commande de texte est une déclaration **SQL SELECT** (dans ce cas, parce que SQL **SELECT** spécifie un jeu de ligne, la commande crée automatiquement un jeu de ligne).

## <a name="rowsets"></a>Ensembles de lignes

Les lignes affichent les données en format tabulaire. Un index est un cas particulier d’un rowset. Vous pouvez créer des rames à partir de la session ou de la commande.

### <a name="schema-rowsets"></a>Ensembles de lignes de schéma

Schemas ont des métadonnées (informations structurelles) sur une base de données. Les rangées de schema sont des rames qui ont des informations sur le schéma. Certains fournisseurs OLE DB pour les objets encastrés DBMS support. Pour plus d’informations sur les rames de schémas, voir [Obtenir des métadonnées avec Schema Rowsets](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) et [Schema Rowset Classes et Typesdef Classes](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Afficher les objets

Un objet de vue définit un sous-ensemble des lignes et des colonnes d’un aviron. Il n’a pas de données propres. Afficher les objets ne peuvent pas combiner les données de plusieurs jeux de lignes.

## <a name="accessors"></a>Accesseurs

Seul OLE DB utilise le concept d’accesseurs. Un accesseur décrit comment les données sont stockées chez un consommateur. Il dispose d’un ensemble de liaisons (appelées carte de colonne) entre les champs encastrés (colonnes) et les membres de données que vous déclarez chez le consommateur.

## <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>Transactions

Les objets de transaction sont utilisés lors de l’engagement ou de l’avortement des transactions imbriquées à d’autres que le niveau le plus bas. Une transaction est une unité de travail indivisible définie par le test ACID. ACID signifie :

- L’atome, ne peut pas être divisé en unités de travail plus petites

- La concordance, plus d’une transaction peut se produire à la fois

- L’isolement, une transaction a une connaissance limitée des changements apportés par une autre

- Durabilité, la transaction apporte des changements persistants

## <a name="enumerators"></a>Énumérateurs

Les enumérateurs recherchent les sources de données disponibles et d’autres enumérateurs. Les consommateurs qui ne sont pas personnalisés pour une source de données particulière utilisent des enumérateurs pour rechercher une source de données à utiliser.

Un enumérateur racine, expédié dans le Microsoft Data Access SDK, traverse le registre à la recherche de sources de données et d’autres enumérateurs. D’autres enumérateurs traversent le registre ou recherchent d’une manière spécifique au fournisseur.

## <a name="errors"></a>Erreurs

Toute interface sur n’importe quel objet OLE DB peut générer des erreurs. Les erreurs ont des informations supplémentaires sur une erreur, y compris un objet d’erreur personnalisé en option. Ces informations sont stockées dans un HRESULT.

## <a name="notifications"></a>Notifications

Les notifications sont utilisées par des groupes de consommateurs coopérant partageant un jeu d’affilée (où le partage signifie que les consommateurs sont supposés travailler dans le cadre de la même transaction). Les notifications permettent aux consommateurs coopérant partageant un jeu de ligne d’être informés des actions sur le rowset effectuées par leurs pairs.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Aperçu de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)
