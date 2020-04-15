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
ms.openlocfilehash: 13640dd2a8593057bef708a45dfc8471ba212563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367183"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC : bibliothèque de curseurs ODBC

Ce sujet décrit la Bibliothèque des curseurs de l’ODBC et explique comment l’utiliser. Pour plus d'informations, consultez les pages suivantes :

- [Bibliothèque Cursor et pilotes ODBC de niveau 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Mises à jour positionnées et colonnes Timestamp](#_core_positioned_updates_and_timestamp_columns)

- [Utilisation de la bibliothèque cursor](#_core_using_the_cursor_library)

La Bibliothèque des curseurs de l’ODBC est une bibliothèque à liaison dynamique (DLL) qui se trouve entre le gestionnaire de chauffeur de l’ODBC et le conducteur. En termes ODBC, un conducteur maintient un curseur pour garder une trace de sa position dans le dossier. Le curseur marque la position dans l’enregistrement auquel vous avez déjà fait défiler — le record actuel.

## <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Bibliothèque Cursor et pilotes ODBC de niveau 1

La bibliothèque ODBC Cursor offre aux conducteurs de niveau 1 les nouvelles capacités suivantes :

- Défilement vers l’avant et vers l’arrière. Les conducteurs de niveau 2 n’ont pas besoin de la bibliothèque de curseurs parce qu’ils sont déjà défilants.

- Prise en charge des instantanés. La bibliothèque de curseurs gère un tampon contenant les enregistrements de l’instantané. Ce tampon reflète les suppressions et les modifications de votre programme aux enregistrements, mais pas les ajouts, suppressions ou modifications d’autres utilisateurs. Par conséquent, l’instantané n’est aussi actuel que le tampon de la bibliothèque de curseurs. Le tampon ne reflète pas non plus `Requery`vos propres ajouts jusqu’à ce que vous appelez . Les dynasets n’utilisent pas la bibliothèque de curseurs.

La bibliothèque de curseurs vous donne des instantanés (curseurs statiques) même s’ils ne sont pas normalement pris en charge par votre chauffeur. Si votre pilote prend déjà en charge les curseurs statiques, vous n’avez pas besoin de charger la bibliothèque de curseurs pour obtenir un support instantané. Si vous utilisez la bibliothèque de curseurs, vous ne pouvez utiliser que des instantanés et des enregistrements avant seulement. Si votre chauffeur prend en charge les dynasets (KEYSET_DRIVEN curseurs) et que vous souhaitez les utiliser, vous ne devez pas utiliser la bibliothèque de curseurs. Si vous souhaitez utiliser les deux instantanés et les dynasets, vous devez les baser sur deux objets différents `CDatabase` (deux connexions différentes) à moins que votre pilote ne supporte les deux.

## <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Mises à jour positionnées et colonnes Timestamp

> [!NOTE]
> Les sources de données de l’ODBC sont accessibles par l’intermédiaire des classes MFC ODBC, telles que décrites dans ce sujet, ou par l’intermédiaire des classes MFC Data Access Object (DAO).

> [!NOTE]
> Si votre pilote ODBC prend en charge `SQLSetPos`, ce que MFC utilise s’il est disponible, ce sujet ne s’applique pas à vous.

La plupart des pilotes de niveau 1 ne prennent pas en charge les mises à jour positionnées. Ces conducteurs comptent sur la bibliothèque de curseurs pour imiter les capacités des conducteurs de niveau 2 à cet égard. La bibliothèque de curseurs imite le support de mise à jour positionné en faisant une mise à jour recherchée sur les champs immuables.

Dans certains cas, un jeu d’enregistrement peut contenir une colonne de temps comme l’un de ces champs immuables. Deux problèmes se posent à l’aide d’enregistrements MFC avec des tableaux qui contiennent des colonnes de timestamp.

Le premier numéro concerne des instantanés actualisables sur les tableaux avec des colonnes de timestamp. Si le tableau auquel votre instantané est lié contient une `Requery` colonne `Edit` de `Update`timestamp, vous devriez appeler après votre appel et . Si ce n’est pas le cas, vous pourriez ne pas être en mesure de modifier le même enregistrement à nouveau. Lorsque vous `Edit` appelez `Update`et puis, l’enregistrement est écrit à la source de données et la colonne de timestamp est mise à jour. Si vous n’appelez `Requery`pas, la valeur de l’enregistrement pour l’enregistrement dans votre instantané ne correspond plus à l’humidité de temps correspondante sur la source de données. Lorsque vous essayez de mettre à jour l’enregistrement à nouveau, la source de données peut interdire la mise à jour en raison de l’inadéquation.

La deuxième question concerne les limitations de `RFX_Date` la classe [CTime](../../atl-mfc-shared/reference/ctime-class.md) lorsqu’il est utilisé avec la fonction de transférer des informations d’heure et de date à ou à partir d’une table. Le `CTime` traitement de l’objet impose des frais généraux sous forme de traitement intermédiaire supplémentaire pendant le transfert de données. La plage `CTime` de dates d’objets peut également être trop limitante pour certaines applications. Une nouvelle version `RFX_Date` de la fonction prend un paramètre `CTime` *ODBC TIMESTAMP_STRUCT* au lieu d’un objet. Pour plus d’informations, voir `RFX_Date` dans [Macros et Globals](../../mfc/reference/mfc-macros-and-globals.md) dans la référence *MFC*.

## <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Utilisation de la bibliothèque cursor

Lorsque vous vous connectez à une source de données — en appelant [CDatabase : : OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [CDatabase : : : Ouvert](../../mfc/reference/cdatabase-class.md#open) — vous pouvez spécifier s’il faut utiliser la bibliothèque de curseurs pour la source de données. Si vous créez des instantanés sur cette `CDatabase::useCursorLib` source `dwOptions` de `OpenEx` données, spécifiez l’option `Open` dans le paramètre ou spécifiez VRAI pour le paramètre *bUseCursorLib* (la valeur par défaut est VRAI). Si votre chauffeur ODBC prend en charge les dynasets et que vous souhaitez ouvrir des dynasets sur la source de données, n’utilisez pas la bibliothèque de curseurs (elle masque certaines fonctionnalités du conducteur nécessaires pour les dynasets). Dans ce cas, `CDatabase::useCursorLib` ne `OpenEx` pas spécifier ou spécifier FALSE pour le paramètre *bUseCursorLib* dans `Open`.

## <a name="see-also"></a>Voir aussi

[ODBC Basics](../../data/odbc/odbc-basics.md)
