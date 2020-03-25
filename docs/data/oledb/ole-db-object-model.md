---
title: Modèle objet OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 192195d02b034546e50b1cb860b1f11c47dc2b65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210117"
---
# <a name="ole-db-object-model"></a>Modèle objet OLE DB

Le modèle objet OLE DB est constitué des objets ou des composants suivants. Les quatre premiers objets ou composants listés (sources de données, sessions, commandes et ensembles de lignes) vous permettent de vous connecter à une source de données et de l’afficher. Le reste, à partir des accesseurs, est lié à l’utilisation des données lorsqu’elles sont affichées.

## <a name="data-sources"></a>Sources de données

Les objets de source de données vous permettent de vous connecter à une source de données telle qu’un fichier ou un SGBD. Un objet source de données crée et gère la connexion et contient des autorisations et des informations d’authentification (telles que le nom de connexion et le mot de passe). Un objet source de données peut créer une ou plusieurs sessions.

## <a name="sessions"></a>Sessions

Une session gère une interaction particulière avec la source de données pour interroger et récupérer des données. Chaque session est une transaction unique. Une transaction est une unité de travail indivisible définie par le test ACID. Pour obtenir une définition d’ACID, consultez [transactions](#vcconoledbcomponents_transactions).

Les sessions effectuent des tâches importantes, telles que l’ouverture d’ensembles de lignes et le retour de l’objet de source de données qui l’a créé. Les sessions peuvent également retourner des métadonnées, ou des informations sur la source de données elle-même (par exemple, les informations de table).

Une session peut créer une ou plusieurs commandes.

## <a name="commands"></a>Commandes

Les commandes exécutent une commande de texte telle qu’une instruction SQL. Si la commande Text spécifie un ensemble de lignes, par exemple une instruction SQL **Select** , la commande crée l’ensemble de lignes.

Une commande est simplement un conteneur pour une commande de texte, qui est une chaîne (telle qu’une instruction SQL) passée d’un consommateur à un objet source de données pour être exécutée par le magasin de données sous-jacent du fournisseur. En règle générale, la commande de texte est une instruction SQL **Select** (dans ce cas, étant donné que SQL **Select** spécifie un ensemble de lignes, la commande crée automatiquement un ensemble de lignes).

## <a name="rowsets"></a>Ensembles de lignes

Les ensembles de lignes affichent les données sous forme de tableau. Un index est un cas spécial d’un ensemble de lignes. Vous pouvez créer des ensembles de lignes à partir de la session ou de la commande.

### <a name="schema-rowsets"></a>Ensembles de lignes de schéma

Les schémas ont des métadonnées (informations structurelles) sur une base de données. Les ensembles de lignes de schéma sont des ensembles de lignes qui contiennent des informations de schéma. Certains fournisseurs de OLE DB pour SGBD prennent en charge les objets d’ensemble de lignes de schéma. Pour plus d’informations sur les ensembles de lignes de schéma, consultez [obtention de métadonnées avec des ensembles](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) de lignes de schéma et de schéma [et classes typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Objets de vue

Un objet de vue définit un sous-ensemble des lignes et des colonnes d’un ensemble de lignes. Il n’a aucune donnée propre. Les objets de vue ne peuvent pas combiner des données provenant de plusieurs ensembles de lignes.

## <a name="accessors"></a>Accesseurs

Seul OLE DB utilise le concept des accesseurs. Un accesseur décrit la façon dont les données sont stockées dans un consommateur. Il possède un ensemble de liaisons (appelé « mappage de colonnes ») entre les champs d’ensemble de lignes (colonnes) et les données membres que vous déclarez dans le consommateur.

##  <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a> Transactions

Les objets de transaction sont utilisés lors de la validation ou de l’abandon de transactions imbriquées à un niveau autre que le plus bas. Une transaction est une unité de travail indivisible définie par le test ACID. ACID signifie :

- Atomicité, ne peuvent pas être divisées en unités de travail plus petites

- L’accès concurrentiel, plusieurs transactions peuvent être effectuées à la fois

- Isolation, une transaction a une connaissance limitée des modifications apportées par une autre

- Durabilité, la transaction effectue des modifications persistantes

## <a name="enumerators"></a>Énumérateurs

Les énumérateurs recherchent les sources de données disponibles et d’autres énumérateurs. Les consommateurs qui ne sont pas personnalisés pour une source de données particulière utilisent des énumérateurs pour rechercher une source de données à utiliser.

Un énumérateur racine, fourni dans le kit de développement logiciel (SDK) Microsoft Data Access, parcourt le registre pour rechercher des sources de données et d’autres énumérateurs. D’autres énumérateurs parcourent le registre ou effectuent une recherche de manière spécifique au fournisseur.

## <a name="errors"></a>Erreurs

Toute interface sur un objet OLE DB peut générer des erreurs. Les erreurs contiennent des informations supplémentaires sur une erreur, notamment un objet d’erreur personnalisé facultatif. Ces informations sont stockées dans un HRESULT.

## <a name="notifications"></a>Notifications

Les notifications sont utilisées par des groupes de consommateurs coopérants partageant un ensemble de lignes (où le partage signifie que les consommateurs sont supposés travailler dans la même transaction). Les notifications permettent aux consommateurs coopérants partageant un ensemble de lignes d’être informés des actions sur l’ensemble de lignes effectué par leurs pairs.

## <a name="see-also"></a>Voir aussi

[Programmation OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Vue d’ensemble de la programmation OLE DB](../../data/oledb/ole-db-programming-overview.md)
