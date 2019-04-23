---
title: 'ODBC : La bibliothèque de curseurs ODBC'
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
ms.openlocfilehash: 862303a0dc66fbd49bfcba83336ab29dfc7145c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032230"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC : La bibliothèque de curseurs ODBC

Cette rubrique décrit la bibliothèque de curseurs ODBC et explique comment l’utiliser. Pour plus d'informations, voir :

- [Bibliothèque de curseurs et de niveau 1 les pilotes ODBC](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Mises à jour positionnées et des colonnes Timestamp](#_core_positioned_updates_and_timestamp_columns)

- [À l’aide de la bibliothèque de curseurs](#_core_using_the_cursor_library)

La bibliothèque de curseurs ODBC est une bibliothèque de liens dynamiques (DLL) qui réside entre le Gestionnaire de pilotes ODBC et le pilote. En termes d’ODBC, un pilote conserve un curseur pour suivre sa position dans le jeu d’enregistrements. Le curseur marque la position dans le jeu d’enregistrements que vous avez atteint, l’enregistrement actif.

##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> Bibliothèque de curseurs et de niveau 1 les pilotes ODBC

La bibliothèque de curseurs ODBC donne des pilotes de niveau 1 les nouvelles fonctionnalités suivantes :

- Le défilement vers l’avant et vers l’arrière. Les pilotes de niveau 2 n’avez pas besoin de la bibliothèque de curseurs, car ils peuvent déjà défiler.

- Prise en charge pour les captures instantanées. La bibliothèque de curseurs gère une mémoire tampon contenant les enregistrements de l’instantané. Cette mémoire tampon reflète les suppressions et les modifications apportées aux enregistrements, mais pas les ajouts, suppressions ou les modifications des autres utilisateurs de votre programme. Par conséquent, l’instantané est uniquement aussi actuel que la mémoire tampon de la bibliothèque de curseurs. La mémoire tampon ne reflète vos propres ajouts jusqu'à ce que vous appeliez `Requery`. Feuilles de réponse dynamiques n’utilisent pas la bibliothèque de curseurs.

La bibliothèque de curseurs vous donne des instantanés (curseurs statiques) même si elles ne sont normalement pas pris en charge par votre pilote. Si votre pilote prend déjà en charge les curseurs statiques, il est inutile de charger la bibliothèque de curseurs pour obtenir un support technique de capture instantanée. Si vous n’utilisez pas la bibliothèque de curseurs, vous pouvez utiliser uniquement les instantanés et recordsets avant uniquement. Si votre pilote prend en charge les feuilles de réponse dynamiques (curseurs KEYSET_DRIVEN) et que vous souhaitez les utiliser, vous ne devez pas utiliser la bibliothèque de curseurs. Si vous souhaitez utiliser les instantanés et les feuilles de réponse dynamiques, vous devez les baser sur deux différents `CDatabase` objets (deux connexions différentes), sauf si votre pilote prend en charge les deux.

##  <a name="_core_positioned_updates_and_timestamp_columns"></a> Mises à jour positionnées et des colonnes Timestamp

> [!NOTE]
>  Sources de données ODBC sont accessibles via les classes ODBC MFC, comme décrit dans cette rubrique, ou via les classes de données Access objet DAO (MFC).

> [!NOTE]
>  Si votre pilote ODBC prend en charge `SQLSetPos`, le MFC utilise le cas échéant, cette rubrique ne s’applique pas à vous.

La plupart des pilotes de niveau 1 ne prennent pas en charge les mises à jour positionnées. Ces pilotes reposent sur la bibliothèque de curseurs pour émuler les capacités des pilotes de niveau 2 à cet égard. La bibliothèque de curseurs émule la prise en charge de la mise à jour positionnée en effectuant une mise à jour recherchée sur les champs qui ne changent pas.

Dans certains cas, un jeu d’enregistrements peut contenir une colonne timestamp en tant qu’un de ces champs inchangés. À l’aide de jeux d’enregistrements MFC avec des tables qui contiennent des colonnes d’horodatage soulève deux problèmes.

Le premier concerne les instantanés sur des tables avec colonnes timestamp. Si la table à laquelle votre instantané est lié contient une colonne timestamp, vous devez appeler `Requery` après avoir appelé `Edit` et `Update`. Si ce n’est pas le cas, vous n’êtes peut-être pas en mesure de modifier à nouveau le même enregistrement. Lorsque vous appelez `Edit` , puis `Update`, l’enregistrement est écrit dans la source de données et la colonne d’horodatage est mis à jour. Si vous n’appelez pas `Requery`, la valeur d’horodatage pour l’enregistrement de votre instantané ne correspond plus à l’horodatage correspondant sur la source de données. Lorsque vous essayez de mettre à jour l’enregistrement à nouveau, la source de données peut ne pas autoriser la mise à jour en raison de l’incompatibilité.

Le deuxième problème concerne les limites de la classe [CTime](../../atl-mfc-shared/reference/ctime-class.md) lorsqu’il est utilisé avec le `RFX_Date` (fonction) pour transférer des informations de date et heure vers ou à partir d’une table. Traitement de la `CTime` objet nécessite une certaine charge sous la forme d’un traitement supplémentaire intermédiaire pendant le transfert de données. La plage de dates `CTime` objets peuvent également être trop limitée pour certaines applications. Une nouvelle version de la `RFX_Date` fonction prend une ODBC *TIMESTAMP_STRUCT* paramètre au lieu d’un `CTime` objet. Pour plus d’informations, consultez `RFX_Date` dans [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md) dans le *référence MFC*.

##  <a name="_core_using_the_cursor_library"></a> À l’aide de la bibliothèque de curseurs

Lorsque vous vous connectez à une source de données, en appelant [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) — vous pouvez spécifier s’il faut utiliser la bibliothèque de curseurs pour la source de données. Si vous allez créer des captures instantanées sur cette source de données, spécifiez la `CDatabase::useCursorLib` option dans le `dwOptions` paramètre `OpenEx` ou spécifiez la valeur TRUE pour le *bUseCursorLib* paramètre à `Open` (la valeur par défaut est VALEUR TRUE). Si votre pilote ODBC prend en charge les feuilles de réponse dynamiques et que vous souhaitez ouvrir des feuilles de réponse dynamiques sur la source de données, n’utilisez pas la bibliothèque de curseurs (il masque certaines fonctionnalités de pilote nécessaires pour les dynasets). Dans ce cas, ne spécifiez pas `CDatabase::useCursorLib` dans `OpenEx` ou spécifiez FALSE pour le *bUseCursorLib* paramètre dans `Open`.

## <a name="see-also"></a>Voir aussi

[Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)