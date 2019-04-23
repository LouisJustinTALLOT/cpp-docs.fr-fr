---
title: Modèle objet OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 303ad4166f0f1126182956fae9c19f513be7cfb3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039154"
---
# <a name="ole-db-object-model"></a>Modèle objet OLE DB

Le modèle objet OLE DB comprend les objets suivants ou les composants. Les quatre premiers objets ou composants répertoriés (sources de données, sessions, commandes et ensembles de lignes) permettent de se connecter à une source de données et l’afficher. Le reste, en commençant par les accesseurs, sont liées à l’utilisation avec les données lorsqu’elle est affichée.

## <a name="data-sources"></a>Data Sources

Objets source de données vous permettent de vous connecter à une source de données tel qu’un fichier ou un SGBD. Un objet de source de données crée et gère la connexion et contient des informations d’autorisations et les authentifications (par exemple, le nom de connexion et mot de passe). Un objet de source de données peut créer une ou plusieurs sessions.

## <a name="sessions"></a>Sessions

Une session gère une interaction particulière avec la source de données pour interroger et récupérer des données. Chaque session est une transaction unique. Une transaction est une unité de travail indivisible définie par le test ACID. Pour une définition de ACID, consultez [Transactions](#vcconoledbcomponents_transactions).

Sessions d’effectuer des tâches importantes telles que l’ouverture des ensembles de lignes et le retour de l’objet de source de données qui l’a créé. Sessions peut également retourner des métadonnées ou des informations sur la source de données (par exemple, des informations sur les tables).

Une session peut créer une ou plusieurs commandes.

## <a name="commands"></a>Commandes

Commandes exécutent une commande de texte telle qu’une instruction SQL. Si la commande texte spécifie un ensemble de lignes, telles que SQL **sélectionnez** instruction, la commande crée l’ensemble de lignes.

Une commande est simplement un conteneur pour une commande de texte, qui est une chaîne (par exemple, une instruction SQL) passée à partir d’un consommateur à un objet de source de données pour l’exécution par le magasin de données du fournisseur sous-jacent. En règle générale, la commande de texte est une instance SQL **sélectionnez** instruction (dans ce cas, étant donné que SQL **sélectionnez** spécifie un ensemble de lignes, la commande crée automatiquement un ensemble de lignes).

## <a name="rowsets"></a>Ensembles de lignes

Ensembles de lignes affichent des données au format tabulaire. Un index est un cas spécial d’un ensemble de lignes. Vous pouvez créer des ensembles de lignes à partir de la session ou de la commande.

### <a name="schema-rowsets"></a>Jeux de lignes du schéma

Schémas contiennent des métadonnées (informations structurelles) sur une base de données. Ensembles de lignes de schéma sont des ensembles de lignes qui contiennent des informations de schéma. Certains fournisseurs OLE DB pour SGBD prennent en charge les objets d’ensemble de lignes de schéma. Pour plus d’informations sur les ensembles de lignes de schéma, consultez [récupération de métadonnées avec les ensembles de lignes de schéma](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) et [Classes d’ensemble de lignes de schéma et Classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Afficher les objets

Un objet de vue définit un sous-ensemble des lignes et des colonnes à partir d’un ensemble de lignes. Il ne comporte aucune donnée de son propre. Objets de vue ne peut pas combiner des données à partir de plusieurs ensembles de lignes.

## <a name="accessors"></a>Accesseurs

Uniquement la OLE DB utilise le concept d’accesseur. Un accesseur décrit comment les données sont stockées dans un consommateur. Il possède un ensemble de liaisons (appelé un mappage de colonnes) entre les champs de l’ensemble de lignes (colonnes) et les membres de données que vous déclarez dans le consommateur.

##  <a name="vcconoledbcomponents_transactions"></a> Transactions

Les objets de transaction sont utilisés lors de la validation ou l’abandon de transactions imbriquées à autre que le niveau le plus bas. Une transaction est une unité de travail indivisible définie par le test ACID. Les propriétés ACID sont :

- Atomicité, ne peut pas être divisé en petites unités de travail

- L’accès simultané, plusieurs transactions peuvent se produire à la fois

- Isolation, une seule transaction a une connaissance limitée des modifications apportées par un autre

- Durabilité, la transaction rend permanentes les modifications apportées

## <a name="enumerators"></a>Énumérateurs

Énumérateurs rechercher des sources de données disponibles et d’autres énumérateurs. Les consommateurs qui ne sont pas adaptées à une source de données particulière utilisent des énumérateurs pour rechercher une source de données à utiliser.

Un énumérateur racine, fourni dans Microsoft Data Access SDK, parcourt le Registre, recherchez des sources de données et d’autres énumérateurs. D’autres énumérateurs parcourent le Registre ou la recherche de manière spécifique au fournisseur.

## <a name="errors"></a>Erreurs

N’importe quelle interface sur un objet OLE DB peut générer des erreurs. Erreurs d’autres informations concernant une erreur, y compris un objet d’erreur personnalisé facultatif. Ces informations sont stockées dans un HRESULT.

## <a name="notifications"></a>Notifications

Les notifications sont utilisées par les groupes de consommateurs coopératifs partageant un ensemble de lignes (où partage signifie que les consommateurs sont censés fonctionner dans la même transaction). Notifications permettent aux consommateurs coopératifs partage un ensemble de lignes être informé sur les actions sur l’ensemble de lignes effectuées par leurs pairs.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)