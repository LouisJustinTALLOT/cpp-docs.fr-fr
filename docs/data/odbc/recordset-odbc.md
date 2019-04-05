---
title: Recordset (ODBC)
ms.date: 11/04/2016
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
ms.openlocfilehash: b201e152d83d3812253aa4803eebe715d726219d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034493"
---
# <a name="recordset-odbc"></a>Recordset (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Un [CRecordset](../../mfc/reference/crecordset-class.md) objet représente un ensemble d’enregistrements sélectionnés à partir d’une source de données. Les enregistrements peuvent être à partir de :

- Une table.

- Une requête.

- Une procédure stockée qui accède à une ou plusieurs tables.

Un exemple d’un jeu d’enregistrements basé sur une table est « all customers », qui accède à une table Customer. Un exemple d’une requête est « toutes les factures de Joe Smith ». Un exemple d’un jeu d’enregistrements basé sur une procédure stockée (parfois appelée une requête prédéfinie) est « tous les comptes impayées, » qui appelle une procédure stockée dans la base de données back-end. Un jeu d’enregistrements peut joindre deux ou plusieurs tables de la même source de données, mais pas les tables à partir de différentes sources de données.

> [!NOTE]
>  Pour plus d’informations sur la dérivation des classes de jeu d’enregistrements à l’aide des Assistants, consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) et [prise en charge de la base de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md).

> [!NOTE]
>  Certains pilotes ODBC prennent en charge les vues de la base de données. Dans ce sens, une vue est une requête créée à l’origine avec le code SQL `CREATE VIEW` instruction. Les Assistants ne prennent actuellement pas en charge les vues, mais il est possible d’écrire le code vous-même.

##  <a name="_core_recordset_capabilities"></a> Fonctionnalités de jeu d’enregistrements

Tous les objets de jeu d’enregistrements partagent les fonctionnalités suivantes :

- Si la source de données n’est pas en lecture seule, vous pouvez spécifier que le recordset est [actualisable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [modifiable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), ou en lecture seule. Si le jeu d’enregistrements est modifiable, vous pouvez choisir optimiste ou pessimiste [verrouillage](../../data/odbc/recordset-locking-records-odbc.md) fourni de méthodes, le pilote fournit la prise en charge appropriée de la méthode de verrouillage. Si la source de données est en lecture seule, le jeu d’enregistrements sera en lecture seule.

- Vous pouvez appeler des fonctions de membres [défilement](../../data/odbc/recordset-scrolling-odbc.md) via les enregistrements sélectionnés.

- Vous pouvez [filtre](../../data/odbc/recordset-filtering-records-odbc.md) les enregistrements pour limiter les enregistrements qui sont sélectionnées parmi celles qui sont disponibles.

- Vous pouvez [tri](../../data/odbc/recordset-sorting-records-odbc.md) les enregistrements dans l’ordre, croissant ou décroissant selon une ou plusieurs colonnes.

- Vous pouvez [paramétrer](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) le jeu d’enregistrements pour qualifier la sélection du jeu d’enregistrements en cours d’exécution.

##  <a name="_core_snapshots_and_dynasets"></a> Les instantanés et les feuilles de réponse dynamiques

Il existe deux principaux types de jeux d’enregistrements : [instantanés](../../data/odbc/snapshot.md) et [les dynasets](../../data/odbc/dynaset.md). Les deux sont pris en charge par la classe `CRecordset`. Chacun partage les caractéristiques communes de tous les jeux d’enregistrements, mais chacun étend également les fonctionnalités communes dans sa propre façon spécialisée. Les instantanés fournissent une vue statique des données et sont utiles pour les rapports et d’autres situations, dans lequel vous souhaitez un affichage des données telles qu’elles existaient à un moment donné. Feuilles de réponse dynamiques sont utiles lorsque vous souhaitez que les mises à jour effectuées par d’autres utilisateurs soient visibles dans le jeu d’enregistrements sans avoir à actualiser ou actualiser le jeu d’enregistrements. Captures instantanées et feuilles de réponse dynamiques peuvent être modifiables ou en lecture seule. Pour refléter les enregistrements ajoutés ou supprimés par d’autres utilisateurs, appeler [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset` permet également de deux autres types de jeux d’enregistrements : jeux d’enregistrements dynamiques et les recordsets avant uniquement. Recordsets dynamiques sont similaires aux feuilles de réponse ; Toutefois, les jeux d’enregistrements dynamiques reflète tous les enregistrements ajoutés ou supprimés sans appeler `CRecordset::Requery`. Pour cette raison, les jeux d’enregistrements dynamiques est généralement coûteux en temps de traitement sur le SGBD et nombre de pilotes ODBC ne prennent pas en charge les. En revanche, recordsets avant uniquement fournir la méthode la plus efficace d’accès aux données pour les jeux d’enregistrements qui ne nécessite pas de mises à jour ou défilement arrière. Par exemple, vous pouvez utiliser un jeu d’enregistrements avant uniquement pour migrer des données à partir d’une source de données vers un autre, où vous devez uniquement déplacer des données vers l’avant. Pour utiliser un jeu d’enregistrements avant uniquement, vous devez effectuer les actions suivantes :

- Passer l’option `CRecordset::forwardOnly` en tant que le *nOpenType* paramètre de la [Open](../../mfc/reference/crecordset-class.md#open) fonction membre.

- Spécifiez `CRecordset::readOnly` dans le *dwOptions* paramètre de `Open`.

    > [!NOTE]
    >  Pour plus d’informations sur le pilote ODBC requis pour la prise en charge de la feuille de réponse dynamique, consultez [ODBC](../../data/odbc/odbc-basics.md). Pour obtenir la liste des pilotes ODBC inclus dans cette version de Visual C++ et pour plus d’informations sur l’obtention de pilotes supplémentaires, consultez [liste de pilotes ODBC](../../data/odbc/odbc-driver-list.md).

##  <a name="_core_your_recordsets"></a> Les jeux d’enregistrements

Pour chaque table distincte, vue ou procédure stockée que vous souhaitez accéder, vous définissez généralement une classe dérivée de `CRecordset`. (L’exception est une jointure de base de données, dans lequel un jeu d’enregistrements représente les colonnes à partir de deux ou plusieurs tables.) Lorsque vous dérivez une classe de jeu d’enregistrements, vous activez le mécanisme record field exchange (RFX) ou le mécanisme en bloc record field exchange (RFX en bloc), qui sont similaires à la boîte de dialogue (mécanisme DDX data exchange). RFX et RFX en bloc simplifient le transfert de données à partir de la source de données dans votre jeu d’enregistrements ; En outre, RFX peut transférer les données à partir de votre jeu d’enregistrements à la source de données. Pour plus d’informations, consultez [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md) et [jeu d’enregistrements : Extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Un objet recordset vous donne accès à tous les enregistrements sélectionnés. Vous faites défiler les enregistrements sélectionnés à l’aide de `CRecordset` fonctions membres, telles que `MoveNext` et `MovePrev`. En même temps, un objet recordset représente un seul des enregistrements sélectionnés, l’enregistrement actif. Vous pouvez examiner les champs de l’enregistrement en cours en déclarant des variables de membre de classe qui correspondent aux colonnes de la table ou des enregistrements qui résultent de la requête de base de données de jeu d’enregistrements. Pour plus d’informations sur les membres de données de jeu d’enregistrements, consultez [jeu d’enregistrements : Architecture (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

Les rubriques suivantes expliquent les détails d’utilisation des objets de jeu d’enregistrements. Les rubriques sont répertoriées dans les catégories fonctionnelles et un ordre naturel pour permettre une lecture séquentielle.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Rubriques relatives aux mécanismes d’ouverture, de lecture et de fermeture de recordsets

- [Recordset : Architecture (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Recordset : Déclaration de la classe d’une Table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Recordset : Création et fermeture de Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Recordset : Défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Recordset : Signets et Positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Recordset : Filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Recordset : Tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Recordset : Paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Rubriques relatives aux mécanismes de modification des recordsets

- [Recordset : Ajout, la mise à jour et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Recordset : Verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Recordset : Actualisation d’un jeu d’enregistrements (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Rubriques relatives des techniques plus avancées

- [Recordset : Création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Recordset : Déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Recordset : Liaison dynamique des colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Recordset : Extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Recordset : Utilisation des éléments de données volumineux (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Recordset : Calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Rubriques sur le fonctionne des jeux d’enregistrements

- [Recordset : La sélection de jeux d’enregistrements d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Recordset : Modification des enregistrements par mise à jour des jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[MFC ODBC, consommation](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transaction (ODBC)](../../data/odbc/transaction-odbc.md)