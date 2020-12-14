---
description: 'En savoir plus sur : feuille de réponse dynamique'
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
ms.openlocfilehash: 3c4a8edf1d0058045affc436bb8c9ee1c7e8bf4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239673"
---
# <a name="dynaset"></a>Feuille de réponse dynamique

Cette rubrique décrit les feuilles de réponse dynamiques et présente leur [disponibilité](#_core_availability_of_dynasets).

> [!NOTE]
> Cette rubrique s’applique aux classes ODBC MFC, y compris [CRecordset](../../mfc/reference/crecordset-class.md). Pour plus d’informations sur les feuilles de réponse dynamiques dans les classes DAO, consultez [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Avec DAO, vous pouvez ouvrir des jeux d’enregistrements de type feuille de réponse dynamique.

Une feuille de réponse dynamique est un jeu d’enregistrements avec des propriétés dynamiques. Pendant sa durée de vie, un objet Recordset en mode feuille de réponse dynamique (généralement appelé Dynaset) reste synchronisé avec la source de données de la façon suivante. Dans un environnement multi-utilisateur, d’autres utilisateurs peuvent modifier ou supprimer des enregistrements qui se trouvent dans votre feuille de réponse dynamique ou ajouter des enregistrements à la table que votre feuille de réponse dynamique représente. Enregistre l’ajout ou la suppression de votre application dans le jeu d’enregistrements dans votre feuille de réponse dynamique. Les enregistrements que d’autres utilisateurs ajoutent à la table ne sont pas reflétés dans votre feuille de réponse dynamique tant que vous ne reconstruisez pas la feuille de réponse dynamique en appelant sa `Requery` fonction membre. Quand d’autres utilisateurs suppriment des enregistrements, le code MFC ignore les suppressions de votre Recordset. Les modifications apportées par les autres utilisateurs aux enregistrements existants sont répercutées dans votre feuille de réponse dynamique dès que vous accédez à l’enregistrement affecté.

De même, les modifications apportées aux enregistrements dans une feuille de réponse dynamique sont reflétées dans les feuilles de réponse dynamiques utilisées par d’autres utilisateurs. Les enregistrements que vous ajoutez ne sont pas reflétés dans les feuilles de réponse dynamiques des autres utilisateurs tant qu’ils n’ont pas interrogé leurs feuilles de réponse dynamiques Les enregistrements que vous supprimez sont marqués comme « supprimés » dans les jeux d’enregistrements des autres utilisateurs. Si vous disposez de plusieurs connexions à la même base de données (plusieurs `CDatabase` objets), les recordsets associés à ces connexions ont le même État que les jeux d’enregistrements d’autres utilisateurs.

Les feuilles de réponse dynamiques sont plus précieuses lorsque les données doivent être dynamiques, comme (par exemple) dans un système de réservation d’une compagnie aérienne.

> [!NOTE]
> Pour utiliser les feuilles de réponse dynamiques, vous devez disposer d’un pilote ODBC pour votre source de données qui prend en charge les feuilles de réponse dynamiques et la bibliothèque de curseurs ODBC ne doit pas être chargée. Pour plus d’informations, consultez [disponibilité des feuilles de réponse dynamiques](#_core_availability_of_dynasets).

Pour spécifier qu’un Recordset est une feuille de réponse dynamique, transmettez `CRecordset::dynaset` en tant que premier paramètre à la `Open` fonction membre de votre objet Recordset.

> [!NOTE]
> Pour les feuilles de réponse dynamiques pouvant être mises à jour, votre pilote ODBC doit prendre en charge les instructions de mise à jour positionnée ou la `::SQLSetPos` fonction API ODBC. Si les deux sont pris en charge, MFC les utilise `::SQLSetPos` pour des performances optimales.

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a> Disponibilité des feuilles de réponse dynamiques

Les classes de base de données MFC prennent en charge les feuilles de réponse dynamiques si les conditions suivantes sont remplies :

- La DLL de la bibliothèque de curseurs ODBC ne doit pas être utilisée pour cette source de données.

   Si la bibliothèque de curseurs est utilisée, elle masque certaines fonctionnalités du pilote ODBC sous-jacent, qui sont nécessaires à la prise en charge des feuille de réponse dynamique. Si vous souhaitez utiliser des feuilles de réponse dynamiques (et que votre pilote ODBC dispose des fonctionnalités requises pour les feuilles de réponse dynamiques, comme décrit dans le reste de cette section), vous pouvez empêcher MFC de charger la bibliothèque de curseurs quand vous créez un `CDatabase` objet. Pour plus d’informations, consultez [ODBC](../../data/odbc/odbc-basics.md) et fonction membre [OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [Open](../../mfc/reference/cdatabase-class.md#open) de la classe `CDatabase` .

   Dans la terminologie ODBC, les feuilles de réponse dynamiques et les instantanés sont appelés curseurs. Un curseur est un mécanisme utilisé pour assurer le suivi de sa position dans un jeu d’enregistrements.

- Le pilote ODBC pour votre source de données doit prendre en charge les curseurs de jeu de clés.

   Les curseurs de jeu de clés gèrent les données d’une table en obtenant et en stockant un ensemble de clés. Les clés sont utilisées pour obtenir les données actuelles de la table lorsque l’utilisateur fait défiler vers un enregistrement particulier. Pour déterminer si votre pilote fournit cette prise en charge, appelez la `::SQLGetInfo` fonction API ODBC avec le paramètre *SQL_SCROLL_OPTIONS* .

   Si vous essayez d’ouvrir une feuille de réponse dynamique sans prise en charge des jeux de clés, vous recevez un `CDBException` avec la valeur de code de retour AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- Le pilote ODBC pour votre source de données doit prendre en charge l’extraction étendue.

   L’extraction étendue est la possibilité de faire défiler vers le haut et vers le bas les enregistrements résultants de votre requête SQL. Pour déterminer si votre pilote prend en charge cette fonctionnalité, appelez la `::SQLGetFunctions` fonction API ODBC avec le paramètre *SQL_API_SQLEXTENDEDFETCH* .

Si vous souhaitez des feuilles de réponse dynamiques (ou instantanés) pouvant être mises à jour, votre pilote ODBC doit également prendre en charge la `::SQLSetPos` fonction API ODBC ou les mises à jour positionnées. La `::SQLSetPos` fonction permet à MFC de mettre à jour la source de données sans envoyer d’instructions SQL. Si cette prise en charge est disponible, MFC l’utilise de préférence pour effectuer des mises à jour à l’aide de SQL. Pour déterminer si votre pilote prend en charge `::SQLSetPos` , appelez `::SQLGetInfo` avec le paramètre *SQL_POS_OPERATIONS* .

Les mises à jour positionnées utilisent la syntaxe SQL (sous la forme la plus **récente de** \<cursorname> ) pour identifier une ligne particulière dans la table sur la source de données. Pour déterminer si votre pilote prend en charge les mises à jour positionnées, appelez `::SQLGetInfo` avec le paramètre *SQL_POSITIONED_STATEMENTS* .

En règle générale, les feuilles de réponse dynamiques MFC (mais pas les recordsets avant uniquement) requièrent un pilote ODBC avec la conformité de l’API de niveau 2. Si le pilote de votre source de données est conforme à l’ensemble d’API de niveau 1, vous pouvez toujours utiliser les instantanés mis à jour et en lecture seule et les recordsets avant uniquement, mais pas les feuilles de réponse dynamiques. Toutefois, un pilote de niveau 1 peut prendre en charge les feuilles de réponse dynamiques s’il prend en charge l’extraction étendue et les curseurs pilotés par jeu de clés. Pour plus d’informations sur les niveaux de conformité ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Si vous souhaitez utiliser à la fois des instantanés et des feuilles de réponse dynamiques, vous devez les baser sur deux `CDatabase` objets différents (deux connexions différentes).

Contrairement aux instantanés, qui utilisent le stockage intermédiaire géré par la bibliothèque de curseurs ODBC, les feuilles de réponse dynamiques extraient un enregistrement directement à partir de la source de données dès que vous y faites défiler. Cela permet de conserver les enregistrements sélectionnés à l’origine par le Dynaset synchronisé avec la source de données.

Pour la liste des pilotes ODBC inclus dans cette version de Visual C++ et pour des informations sur l’obtention de pilotes supplémentaires, consultez la [Liste des pilotes ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Voir aussi

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
