---
title: Recordset (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: b7a55621f4875b24cc33a0fd49a5b8b4c88b34cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368638"
---
# <a name="recordset-odbc"></a>Recordset (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Un objet [CRecordset](../../mfc/reference/crecordset-class.md) représente un jeu d’enregistrements sélectionnés dans une source de données. Les enregistrements peuvent provenir :

- Table.

- D’une requête.

- D’une procédure stockée qui accède à une ou plusieurs tables.

Exemple de recordset basé sur une table : « all customers », qui accède à une table Customer. Exemple de requête : « all invoices for Joe Smith ». Exemple de recordset basé sur une procédure stockée (parfois appelée requête prédéfinie) : « all of the deliquent accounts », qui appelle une procédure stockée dans la base de données de back-end. Un recordset peut joindre deux ou plusieurs tables de la même source de données, mais pas des tables de différentes sources de données.

> [!NOTE]
> Certains pilotes ODBC prennent en charge des vues de la base de données. Dans ce cas, une vue est une requête créée à l’origine avec l’instruction SQL `CREATE VIEW`.

## <a name="recordset-capabilities"></a><a name="_core_recordset_capabilities"></a> Fonctionnalités du recordset

Tous les objets recordset partagent les fonctionnalités suivantes :

- Si la source de données n’est pas en lecture seule, vous pouvez spécifier que votre recordset peut être [mis à jour](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [ajouté](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) ou en lecture seule. Si le recordset peut être mis à jour, vous pouvez choisir des méthodes de [verrouillage](../../data/odbc/recordset-locking-records-odbc.md) pessimistes ou optimistes, à condition que le pilote fournisse une prise en charge appropriée pour le verrouillage. Si la source de données est en lecture seule, le recordset est en lecture seule.

- Vous pouvez appeler des fonctions membres pour [faire défiler](../../data/odbc/recordset-scrolling-odbc.md) les enregistrements sélectionnés.

- Vous pouvez [filtrer](../../data/odbc/recordset-filtering-records-odbc.md) les enregistrements pour contraindre les enregistrements sélectionnés parmi ceux disponibles.

- Vous pouvez [trier](../../data/odbc/recordset-sorting-records-odbc.md) les enregistrements par ordre croissant ou décroissant, sur une ou plusieurs colonnes.

- Vous pouvez [paramétrer](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) le recordset pour qualifier la sélection de recordset au moment de l’exécution.

## <a name="snapshots-and-dynasets"></a><a name="_core_snapshots_and_dynasets"></a> Instantanés et feuilles de réponse dynamiques

Il existe deux types de jeux d’enregistrements principaux : les [instantanés](../../data/odbc/snapshot.md) et les [feuilles de réponse dynamiques](../../data/odbc/dynaset.md). Les deux sont pris en charge par la classe `CRecordset`. Chacun partage les caractéristiques communes de tous les recordsets, mais chacun étend également les fonctionnalités communes d’une façon qui lui est propre. Les instantanés fournissent une vue statique des données et sont utiles pour les rapports et d’autres situations dans lesquelles vous avez besoin d’une vue des données telles qu’elles étaient à un moment donné. Les feuilles de réponse dynamiques sont utiles quand vous voulez que les mises à jour effectuées par d’autres utilisateurs soient visibles dans le recordset sans avoir à réinterroger ou actualiser le recordset. Les instantanés et les feuilles de réponse dynamiques sont modifiables ou en lecture seule. Pour refléter les enregistrements ajoutés ou supprimés par d’autres utilisateurs, appelez [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset` autorise aussi deux autres types de recordsets : les recordsets dynamiques et les recordsets avant uniquement. Les recordsets dynamiques sont similaires aux feuilles de réponse dynamiques, toutefois, ils reflètent tous les enregistrements ajoutés ou supprimés sans appeler `CRecordset::Requery`. Pour cette raison, les recordsets dynamiques sont généralement gourmands en temps de traitement sur le SGBD et de nombreux pilotes ODBC ne les prennent pas en charge. En revanche, les recordsets de type avant uniquement fournissent la méthode d’accès aux données la plus efficace pour les recordsets qui n’ont pas besoin de mises à jour ni de défilement arrière. Par exemple, vous pouvez utiliser un recordset de type avant uniquement pour migrer des données d’une source de données vers une autre, où vous devez uniquement déplacer des données vers l’avant. Pour utiliser un recordset de type avant uniquement, vous devez effectuer les deux actions suivantes :

- Passer l’option `CRecordset::forwardOnly` comme paramètre *nOpenType* de la fonction membre [Open](../../mfc/reference/crecordset-class.md#open).

- Spécifier `CRecordset::readOnly` dans le paramètre *dwOptions* de `Open`.

    > [!NOTE]
    >  Pour plus d’informations sur les exigences du pilote ODBC pour la prise en charge des feuilles de réponse dynamiques, consultez [ODBC](../../data/odbc/odbc-basics.md). Pour la liste des pilotes ODBC inclus dans cette version de Visual C++ et pour des informations sur l’obtention de pilotes supplémentaires, consultez la [Liste des pilotes ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="your-recordsets"></a><a name="_core_your_recordsets"></a> Vos recordsets

Pour chaque table, vue ou procédure stockée distincte à laquelle vous voulez accéder, vous définissez généralement une classe dérivée de `CRecordset`. (L’exception est une jointure de base de données, dans laquelle un enregistrement représente des colonnes de deux tableaux ou plus.) Lorsque vous dérivez une classe de recordset, vous activez le mécanisme d’échange de champ record (RFX) ou le mécanisme d’échange d’enregistrements en vrac (Bulk RFX), qui sont similaires au mécanisme d’échange de données de dialogue (DDX). RFX et RFX en bloc simplifient le transfert des données de la source de données vers votre recordset. RFX transfère en plus les données de votre recordset vers la source de données. Pour plus d’informations, voir [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md) et [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Un objet recordset vous donne accès à tous les enregistrements sélectionnés. Vous faites défiler les enregistrements sélectionnés à l’aide de fonctions membres `CRecordset`, comme `MoveNext` et `MovePrev`. En même temps, un objet recordset représente un seul des enregistrements sélectionnés, l’enregistrement actuel. Vous pouvez examiner les champs de l’enregistrement actuel en déclarant des variables membres de la classe recordset qui correspondent aux colonnes de la table ou des enregistrements qui résultent de la requête de base de données. Pour plus d’informations sur les membres des données de recordset, voir [Recordset: Architecture (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

Les rubriques suivantes décrivent en détail l’utilisation des objets recordset. Les rubriques sont listées dans des catégories fonctionnelles et dans un ordre naturel de navigation pour permettre une lecture séquentielle.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Rubriques sur les mécanismes d’ouverture, de lecture et de fermeture des recordsets

- [Recordet: Architecture (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Recordset : déclaration de la classe d'une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Recordset : filtrage d'enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Recordset : tri d'enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Recordset : paramétrage d'un recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Rubriques sur les mécanismes de modification des recordsets

- [Recordset : ajout, modification et suppression d'enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Recordset : verrouillage d'enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Recordset : lancement d'une nouvelle requête sur un recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Rubriques sur les techniques un peu plus avancées

- [Recordset : création d'une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Recordset : déclaration de la classe d'une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Recordset : liaison dynamique de colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Recordset : extraction globale d'enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Recordset : utilisation d'éléments de données volumineux (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Recordset : calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Rubriques sur le fonctionnement des recordsets

- [Recordset : sélection d'enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Recordset : modification des enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Voir aussi

[Connectivité open Database (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Consommation ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transaction (ODBC)](../../data/odbc/transaction-odbc.md)
