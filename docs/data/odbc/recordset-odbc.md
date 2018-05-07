---
title: Jeu d’enregistrements (ODBC) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c59de3c5db2e1ec658a09279cb42e2833a4109e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-odbc"></a>Recordset (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 A [CRecordset](../../mfc/reference/crecordset-class.md) objet représente un ensemble d’enregistrements sélectionnés à partir d’une source de données. Les enregistrements peuvent être à partir de :  
  
-   Une table.  
  
-   Une requête.  
  
-   Une procédure stockée qui accède à une ou plusieurs tables.  
  
 Un exemple d’un jeu d’enregistrements basé sur une table est « all customers », qui accède à une table de clients. Un exemple de requête est « toutes les factures de Joe Smith ». Un exemple d’un jeu d’enregistrements basé sur une procédure stockée (parfois appelée requête prédéfinie) est « tous les comptes impayées, » qui appelle une procédure stockée dans la base de données principale. Un jeu d’enregistrements peut joindre deux ou plusieurs tables de la même source de données, mais pas les tables à partir de différentes sources de données.  
  
> [!NOTE]
>  Pour plus d’informations sur la dérivation des classes de jeu d’enregistrements avec les Assistants, consultez [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) et [prise en charge de la base de données, Assistant Application MFC](../../mfc/reference/database-support-mfc-application-wizard.md).  
  
> [!NOTE]
>  Certains pilotes ODBC prennent en charge les vues de la base de données. Dans ce sens, une vue est une requête créée à l’origine avec le SQL `CREATE VIEW` instruction. Les Assistants ne prennent actuellement pas en charge les vues, mais il est possible d’écrire le code vous-même.  
  
##  <a name="_core_recordset_capabilities"></a> Fonctions de jeu d’enregistrements  
 Tous les objets recordset partagent les capacités suivantes :  
  
-   Si la source de données n’est pas en lecture seule, vous pouvez spécifier que le recordset est [actualisable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [modifiable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), ou en lecture seule. Si le jeu d’enregistrements est modifiable, vous pouvez choisir entre [verrouillage](../../data/odbc/recordset-locking-records-odbc.md) méthodes, fourni le pilote fournit la prise en charge de verrouillage appropriée. Si la source de données est en lecture seule, le jeu d’enregistrements sera en lecture seule.  
  
-   Vous pouvez appeler des fonctions de membres [défilement](../../data/odbc/recordset-scrolling-odbc.md) via les enregistrements sélectionnés.  
  
-   Vous pouvez [filtre](../../data/odbc/recordset-filtering-records-odbc.md) les enregistrements pour limiter les enregistrements qui sont sélectionnés à partir de celles qui sont disponibles.  
  
-   Vous pouvez [tri](../../data/odbc/recordset-sorting-records-odbc.md) les enregistrements dans l’ordre, croissant ou décroissant selon une ou plusieurs colonnes.  
  
-   Vous pouvez [paramétrer](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) le jeu d’enregistrements pour qualifier la sélection du jeu d’enregistrements en cours d’exécution.  
  
##  <a name="_core_snapshots_and_dynasets"></a> Les instantanés et les feuilles de réponse dynamiques  
 Il existe deux principaux types de jeux d’enregistrements : [instantanés](../../data/odbc/snapshot.md) et [les dynasets](../../data/odbc/dynaset.md). Les deux sont pris en charge par la classe `CRecordset`. Chacun partage les caractéristiques communes de tous les jeux d’enregistrements, mais chacun s’étend également les fonctionnalités communes de sa propre manière spécialisé. Les instantanés fournissent une vue statique des données et sont utiles pour les rapports et d’autres situations, dans lequel vous souhaitez un affichage des données telles qu’elles existaient à un moment donné. Feuilles de réponse dynamiques sont utiles lorsque vous souhaitez que les mises à jour effectuées par d’autres utilisateurs soient visibles dans le jeu d’enregistrements sans avoir à actualiser ou actualiser le jeu d’enregistrements. Les instantanés et les feuilles de réponse dynamiques peut être modifiable ou en lecture seule. Pour refléter les enregistrements ajoutés ou supprimés par d’autres utilisateurs, appelez [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).  
  
 `CRecordset` autorise également deux autres types de recordsets : les recordsets dynamiques et les recordsets avant uniquement. Recordsets dynamiques sont semblables aux feuilles de réponse dynamiques ; Toutefois, les recordsets dynamiques reflètent les enregistrements ajoutés ou supprimés sans appeler `CRecordset::Requery`. Pour cette raison, les recordsets dynamiques sont généralement coûteux en temps de traitement sur le SGBD et nombre de pilotes ODBC ne prennent pas en charge les. En revanche, recordsets avant uniquement fournir la méthode la plus efficace de l’accès aux données pour les jeux d’enregistrements qui ne nécessite pas de mises à jour ou défilement arrière. Par exemple, vous pouvez utiliser un jeu d’enregistrements avant uniquement pour migrer des données à partir d’une source de données vers un autre, où vous devez uniquement déplacer les données vers l’avant. Pour utiliser un jeu d’enregistrements de type avant uniquement, vous devez effectuer les actions suivantes :  
  
-   Passer de l’option **CRecordset::forwardOnly** comme le `nOpenType` paramètre de la [ouvrir](../../mfc/reference/crecordset-class.md#open) fonction membre.  
  
-   Spécifiez **CRecordset::readOnly** dans les `dwOptions` paramètre de **ouvrir**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur le pilote ODBC requis pour la prise en charge de la feuille de réponse dynamique, consultez [ODBC](../../data/odbc/odbc-basics.md). Pour obtenir la liste des pilotes ODBC inclus dans cette version de Visual C++ et pour plus d’informations sur l’obtention de pilotes supplémentaires, consultez [liste de pilotes ODBC](../../data/odbc/odbc-driver-list.md).  
  
##  <a name="_core_your_recordsets"></a> Les jeux d’enregistrements  
 Pour chaque table distincte, une vue ou une procédure stockée que vous souhaitez accéder, vous définissez généralement une classe dérivée de `CRecordset`. (L’exception est une jointure de base de données, dans laquelle un jeu d’enregistrements représente des colonnes à partir de deux ou plusieurs tables.) Lorsque vous dérivez une classe de recordset, vous activez le mécanisme de record field exchange (RFX) ou le mécanisme en bloc record field exchange (RFX en bloc), qui sont semblables à la boîte de dialogue (mécanisme DDX data exchange). RFX et RFX en bloc simplifient le transfert de données à partir de la source de données dans le jeu d’enregistrements ; En outre, RFX peut transférer les données à partir de votre jeu d’enregistrements à la source de données. Pour plus d’informations, consultez [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md) et [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Un objet recordset vous donne accès à tous les enregistrements sélectionnés. Vous faites défiler les enregistrements sélectionnés à l’aide de `CRecordset` les fonctions membres, tels que `MoveNext` et `MovePrev`. En même temps, un objet recordset représente un seul des enregistrements sélectionnés, l’enregistrement actif. Vous pouvez examiner les champs de l’enregistrement actif en déclarant des variables de membre de classe qui correspondent aux colonnes de la table ou des enregistrements qui résultent de la requête de base de données de jeu d’enregistrements. Pour plus d’informations sur les membres de données de jeu d’enregistrements, consultez [Recordset : Architecture (ODBC)](../../data/odbc/recordset-architecture-odbc.md).  
  
 Les rubriques suivantes expliquent en détail l’utilisation des objets de jeu d’enregistrements. Les rubriques sont répertoriées dans les catégories fonctionnelles et un ordre naturel pour permettre une lecture séquentielle.  
  
### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Rubriques relatives aux mécanismes d’ouverture, de lecture et de fermeture de recordsets  
  
-   [Recordset : architecture (ODBC)](../../data/odbc/recordset-architecture-odbc.md)  
  
-   [Recordset : déclaration de la classe d’une table (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)  
  
-   [Recordset : création et fermeture de recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)  
  
-   [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)  
  
-   [Recordset : signets et positions absolues (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)  
  
-   [Recordset : filtrage d’enregistrements (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)  
  
-   [Recordset : tri d’enregistrements (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)  
  
-   [Recordset : paramétrage d’un recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Rubriques relatives aux mécanismes de modification des recordsets  
  
-   [Recordset : ajout, modification et suppression d’enregistrements (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)  
  
-   [Recordset : verrouillage d’enregistrements (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)  
  
-   [Recordset : lancement d’une nouvelle requête sur un recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)  
  
### <a name="topics-about-somewhat-more-advanced-techniques"></a>Rubriques relatives des techniques plus avancées  
  
-   [Recordset : création d’une jointure (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)  
  
-   [Recordset : déclaration de la classe d’une requête prédéfinie (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)  
  
-   [Recordset : liaison dynamique de colonnes de données (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)  
  
-   [Recordset : récupération globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)  
  
-   [Recordset : utilisation d’éléments de données volumineux (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)  
  
-   [Recordset : calculs de totaux et autres résultats de regroupement (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)  
  
### <a name="topics-about-how-recordsets-work"></a>Rubriques sur le fonctionnement des recordsets  
  
-   [Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)  
  
-   [Recordset : modification des enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [MFC ODBC, consommation](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Transaction (ODBC)](../../data/odbc/transaction-odbc.md)