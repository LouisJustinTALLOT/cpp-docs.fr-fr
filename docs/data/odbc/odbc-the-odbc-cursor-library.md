---
title: 'ODBC : bibliothèque de curseurs ODBC'
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 51524604cad34ace18ffda2b5f48cc3c5fd89ad7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213094"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC : bibliothèque de curseurs ODBC

Cette rubrique décrit la bibliothèque de curseurs ODBC et explique comment l’utiliser. Pour plus d'informations, consultez les pages suivantes :

- [Bibliothèque de curseurs et pilotes ODBC de niveau 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Mises à jour positionnées et colonnes timestamp](#_core_positioned_updates_and_timestamp_columns)

- [Utilisation de la bibliothèque de curseurs](#_core_using_the_cursor_library)

La bibliothèque de curseurs ODBC est une bibliothèque de liens dynamiques (DLL) qui se trouve entre le gestionnaire de pilotes ODBC et le pilote. En termes ODBC, un pilote gère un curseur pour assurer le suivi de sa position dans le jeu d’enregistrements. Le curseur marque la position dans le jeu d’enregistrements vers lequel vous avez déjà fait l’objet d’un défilement, c’est-à-dire l’enregistrement en cours.

##  <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Bibliothèque de curseurs et pilotes ODBC de niveau 1

La bibliothèque de curseurs ODBC donne aux pilotes de niveau 1 les nouvelles fonctionnalités suivantes :

- Défilement vers l’avant et vers l’arrière. Les pilotes de niveau 2 n’ont pas besoin de la bibliothèque de curseurs, car ils sont déjà défilant.

- Prise en charge des instantanés. La bibliothèque de curseurs gère une mémoire tampon contenant les enregistrements de l’instantané. Cette mémoire tampon reflète les suppressions de votre programme et les modifications apportées aux enregistrements, mais pas les ajouts, les suppressions ou les modifications apportées aux autres utilisateurs. Par conséquent, l’instantané est le plus récent que la mémoire tampon de la bibliothèque de curseurs. La mémoire tampon ne reflète pas non plus vos propres ajouts tant que vous n’appelez pas `Requery`. Les feuilles de réponse dynamiques n’utilisent pas la bibliothèque de curseurs.

La bibliothèque de curseurs vous fournit des instantanés (curseurs statiques), même s’ils ne sont normalement pas pris en charge par votre pilote. Si votre pilote prend déjà en charge les curseurs statiques, vous n’avez pas besoin de charger la bibliothèque de curseurs pour bénéficier de la prise en charge des instantanés. Si vous utilisez la bibliothèque de curseurs, vous ne pouvez utiliser que des instantanés et des recordsets avant uniquement. Si votre pilote prend en charge les feuilles de réponse dynamiques (KEYSET_DRIVEN les curseurs) et que vous souhaitez les utiliser, vous ne devez pas utiliser la bibliothèque de curseurs. Si vous souhaitez utiliser à la fois des instantanés et des feuilles de réponse dynamiques, vous devez les baser sur deux objets de `CDatabase` différents (deux connexions différentes), à moins que votre pilote ne prenne en charge les deux.

##  <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Mises à jour positionnées et colonnes timestamp

> [!NOTE]
>  Les sources de données ODBC sont accessibles par le biais des classes ODBC MFC, comme décrit dans cette rubrique, ou par le biais des classes d’objets d’accès aux données (DAO) MFC.

> [!NOTE]
>  Si votre pilote ODBC prend en charge `SQLSetPos`, que MFC utilise s’il est disponible, cette rubrique ne s’applique pas à vous.

La plupart des pilotes de niveau 1 ne prennent pas en charge les mises à jour positionnées. Ces pilotes s’appuient sur la bibliothèque de curseurs pour émuler les capacités des pilotes de niveau 2 à cet égard. La bibliothèque de curseurs émule la prise en charge des mises à jour positionnées en effectuant une mise à jour avec recherche sur les champs immuables.

Dans certains cas, un jeu d’enregistrements peut contenir une colonne timestamp comme l’un de ces champs immuables. Deux problèmes se posent lors de l’utilisation des recordsets MFC avec des tables qui contiennent des colonnes timestamp.

Le premier problème concerne les instantanés modifiables sur les tables avec des colonnes timestamp. Si la table à laquelle votre instantané est lié contient une colonne timestamp, vous devez appeler `Requery` après avoir appelé `Edit` et `Update`. Si ce n’est pas le cas, vous ne pourrez peut-être pas modifier à nouveau le même enregistrement. Lorsque vous appelez `Edit` puis `Update`, l’enregistrement est écrit dans la source de données et la colonne timestamp est mise à jour. Si vous n’appelez pas `Requery`, la valeur d’horodatage de l’enregistrement dans votre instantané ne correspond plus à l’horodatage correspondant sur la source de données. Lorsque vous essayez de mettre à jour l’enregistrement, la source de données peut interdire la mise à jour en raison de l’incompatibilité.

Le deuxième problème concerne les limitations de la classe [ctime](../../atl-mfc-shared/reference/ctime-class.md) lorsqu’elle est utilisée avec la fonction `RFX_Date` pour transférer des informations de date et d’heure vers ou à partir d’une table. Le traitement de l’objet `CTime` impose une certaine surcharge sous la forme d’un traitement intermédiaire supplémentaire pendant le transfert de données. La plage de dates des objets `CTime` peut également être trop restrictive pour certaines applications. Une nouvelle version de la fonction `RFX_Date` prend un paramètre ODBC *TIMESTAMP_STRUCT* au lieu d’un objet `CTime`. Pour plus d’informations, consultez `RFX_Date` dans les [macros et les champs globaux](../../mfc/reference/mfc-macros-and-globals.md) dans la *référence MFC*.

##  <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Utilisation de la bibliothèque de curseurs

Quand vous vous connectez à une source de données, en appelant [CDatabase :: OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [CDatabase :: Open](../../mfc/reference/cdatabase-class.md#open) , vous pouvez spécifier s’il faut utiliser la bibliothèque de curseurs pour la source de données. Si vous souhaitez créer des instantanés sur cette source de données, spécifiez l’option `CDatabase::useCursorLib` dans le paramètre `dwOptions` pour `OpenEx` ou spécifiez TRUE pour le paramètre *bUseCursorLib* à `Open` (la valeur par défaut est true). Si votre pilote ODBC prend en charge les feuilles de réponse dynamiques et que vous souhaitez ouvrir les feuilles de réponse dynamiques sur la source de données, n’utilisez pas la bibliothèque de curseurs (elle masque certaines fonctionnalités de pilote nécessaires pour les feuilles de réponse dynamiques). Dans ce cas, ne spécifiez pas `CDatabase::useCursorLib` dans `OpenEx` ou spécifiez FALSe pour le paramètre *bUseCursorLib* dans `Open`.

## <a name="see-also"></a>Voir aussi

[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)
