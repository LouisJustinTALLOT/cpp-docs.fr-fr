---
title: Feuille de réponse dynamique
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: 2eb2447d1f984b7734d5e9c45087023e5a6f003f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371841"
---
# <a name="dynaset"></a>Feuille de réponse dynamique

Ce sujet décrit les dynasets et discute de leur [disponibilité](#_core_availability_of_dynasets).

> [!NOTE]
> Ce sujet s’applique aux classes MFC ODBC, y compris [CRecordset](../../mfc/reference/crecordset-class.md). Pour plus d’informations sur les dynasets dans les classes DAO, voir [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Avec DAO, vous pouvez ouvrir des enregistrements de type dynaset.

Un dynaset est un jeu d’enregistrement avec des propriétés dynamiques. Au cours de sa vie, un objet de recordet en mode dynaset (généralement appelé dynaset) reste synchronisé avec la source de données de la manière suivante. Dans un environnement multiusage, d’autres utilisateurs peuvent modifier ou supprimer des enregistrements qui se trouvent dans votre dynaset ou ajouter des enregistrements à la table que représente votre dynaset. Les enregistrements que votre application ajoute ou supprime de l’ensemble d’enregistrements sont reflétés dans votre dynaset. Les enregistrements que les autres utilisateurs ajoutent à la table ne seront pas reflétés dans `Requery` votre dynaset jusqu’à ce que vous reconstruisez le dynaset en appelant sa fonction de membre. Lorsque d’autres utilisateurs suppriment des enregistrements, le code MFC saute sur les suppressions dans votre dossier. Les modifications d’édition apportées par d’autres utilisateurs aux enregistrements existants sont reflétées dans votre dynaset dès que vous faites défiler vers l’enregistrement affecté.

De même, les modifications que vous effectuez aux enregistrements dans un dynaset sont reflétées dans des dynasets utilisés par d’autres utilisateurs. Les enregistrements que vous ajoutez ne sont pas reflétés dans les dynasets des autres utilisateurs jusqu’à ce qu’ils requiy leurs dynasets. Les enregistrements que vous supprimez sont marqués comme « supprimés » dans les enregistrements d’autres utilisateurs. Si vous avez plusieurs connexions `CDatabase` à la même base de données (plusieurs objets), les enregistrements associés à ces connexions ont le même statut que les enregistrements d’autres utilisateurs.

Les dynasets sont plus précieux lorsque les données doivent être dynamiques, comme (par exemple) dans un système de réservation de compagnies aériennes.

> [!NOTE]
> Pour utiliser des dynasets, vous devez avoir un chauffeur ODBC pour votre source de données qui prend en charge les dynasets et la bibliothèque de curseurs ODBC ne doit pas être chargée. Pour plus d’informations, voir [Disponibilité des Dynasets](#_core_availability_of_dynasets).

Pour spécifier qu’un enregistrement est `CRecordset::dynaset` un dynaset, passez comme premier paramètre à la `Open` fonction membre de votre objet de dossier.

> [!NOTE]
> Pour les dynasets updatables, votre pilote ODBC `::SQLSetPos` doit prendre en charge soit les instructions de mise à jour positionnées ou la fonction API ODBC. Si les deux sont `::SQLSetPos` pris en charge, MFC utilise pour l’efficacité.

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Disponibilité des Dynasets

Les classes de base de données MFC prennent en charge les dynasets si les exigences suivantes sont remplies :

- La bibliothèque de curseurs DLL d’ODBC ne doit pas être utilisée pour cette source de données.

   Si la bibliothèque de curseurs est utilisée, elle masque certaines fonctionnalités du pilote ODBC sous-jacent qui est nécessaire pour le support dynaset. Si vous souhaitez utiliser des dynasets (et votre pilote ODBC a la fonctionnalité requise pour les dynasets, comme décrit dans le reste `CDatabase` de cette section), vous pouvez faire charger MFC de ne pas charger la bibliothèque de curseur lorsque vous créez un objet. Pour plus d’informations, voir [ODBC](../../data/odbc/odbc-basics.md) et la `CDatabase`fonction membre [OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [Open](../../mfc/reference/cdatabase-class.md#open) de la classe .

   Dans la terminologie de l’ODBC, les dynasets et les instantanés sont appelés curseurs. Un curseur est un mécanisme utilisé pour garder une trace de sa position dans un jeu d’enregistrement.

- Le pilote ODBC pour votre source de données doit prendre en charge les curseurs à clé.

   Les curseurs pilotés par Keyset gèrent les données à partir d’une table en obtenant et en stockant un ensemble de clés. Les clés sont utilisées pour obtenir des données actuelles à partir de la table lorsque l’utilisateur fait défiler sur un enregistrement particulier. Pour déterminer si votre chauffeur fournit `::SQLGetInfo` ce support, appelez la fonction API ODBC avec le *SQL_SCROLL_OPTIONS* paramètre.

   Si vous essayez d’ouvrir un dynaset sans `CDBException` support keyset, vous obtenez un avec la valeur de code de retour AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- Le pilote ODBC pour votre source de données doit prendre en charge l’aller à l’aide prolongée.

   L’aller chercher étendu est la capacité de faire défiler vers l’arrière ainsi que vers l’avant sur les enregistrements résultant de votre requête SQL. Pour déterminer si votre pilote prend `::SQLGetFunctions` en charge cette capacité, appelez la fonction API ODBC avec le *SQL_API_SQLEXTENDEDFETCH* paramètre.

Si vous voulez des dynasets (ou des instantanés à jour, d’ailleurs), votre pilote ODBC doit également prendre en charge la fonction API ODBC ou les `::SQLSetPos` mises à jour positionnées. La `::SQLSetPos` fonction permet à MFC de mettre à jour la source de données sans envoyer de relevés SQL. Si ce support est disponible, MFC l’utilise de préférence pour faire des mises à jour à l’aide de SQL. Pour déterminer si `::SQLSetPos`votre `::SQLGetInfo` pilote prend en charge, appelez avec le *SQL_POS_OPERATIONS* paramètre.

Les mises à jour positionnées utilisent la syntaxe SQL (du formulaire **WHERE CURRENT OF** \<cursorname>) pour identifier une ligne particulière dans la table sur la source de données. Pour déterminer si votre pilote prend `::SQLGetInfo` en charge les mises à jour positionnées, composez le *paramètre SQL_POSITIONED_STATEMENTS.*

En général, les dynasets MFC (mais pas les enregistrements avant seulement) nécessitent un pilote ODBC avec une conformité API de niveau 2. Si le pilote de votre source de données est conforme à l’ensemble API de niveau 1, vous pouvez toujours utiliser des instantanés mis à jour et lus uniquement et des enregistrements avant seulement, mais pas des colorants. Cependant, un pilote de niveau 1 peut prendre en charge les dynasets s’il prend en charge les curseurs de récupération et de clé. Pour plus d’informations sur les niveaux de conformité ODBC, voir [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Si vous souhaitez utiliser à la fois des instantanés et des `CDatabase` dynasets, vous devez les baser sur deux objets différents (deux connexions différentes).

Contrairement aux instantanés, qui utilisent le stockage intermédiaire maintenu par la bibliothèque de curseurs ODBC, les dynasets récupèrent un enregistrement directement à partir de la source de données dès que vous faites défiler vers elle. Cela conserve les enregistrements initialement sélectionnés par le dynaset synchronisé avec la source de données.

Pour la liste des pilotes ODBC inclus dans cette version de Visual C++ et pour des informations sur l’obtention de pilotes supplémentaires, consultez la [Liste des pilotes ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Voir aussi

[Connectivité open Database (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
