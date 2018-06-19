---
title: 'ODBC : Bibliothèque de curseurs ODBC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e57251263738d534b7e7e22ff287607fbc5159a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092592"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC : bibliothèque de curseurs ODBC
Cette rubrique décrit la bibliothèque de curseurs ODBC et explique comment l’utiliser. Pour plus d'informations, voir :  
  
-   [Pilotes ODBC niveau 1 et de la bibliothèque de curseurs](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [Mises à jour positionnées et colonnes Timestamp](#_core_positioned_updates_and_timestamp_columns)  
  
-   [À l’aide de la bibliothèque de curseurs](#_core_using_the_cursor_library)  
  
 La bibliothèque de curseurs ODBC est une bibliothèque de liens dynamiques (DLL) qui réside entre le Gestionnaire de pilotes ODBC et le pilote. Dans la terminologie ODBC, un pilote conserve un curseur pour suivre sa position dans le jeu d’enregistrements. Le curseur marque la position dans le jeu d’enregistrements que vous avez atteint, l’enregistrement actif.  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> Pilotes ODBC niveau 1 et de la bibliothèque de curseurs  
 La bibliothèque de curseurs ODBC donne des pilotes de niveau 1 les nouvelles fonctionnalités suivantes :  
  
-   Le défilement vers l’avant et vers l’arrière. Les pilotes de niveau 2 n’avez pas besoin de la bibliothèque de curseurs, car ils sont déjà permettant le défilement.  
  
-   Prise en charge des instantanés. La bibliothèque de curseurs gère une mémoire tampon qui contient des enregistrements de l’instantané. Cette mémoire tampon reflète les suppressions et les modifications apportées aux enregistrements, mais pas les ajouts, suppressions ou les modifications des autres utilisateurs de votre programme. Par conséquent, l’instantané est uniquement comme actuel en tant que tampon de la bibliothèque curseurs. La mémoire tampon ne reflète vos propres ajouts jusqu'à ce que vous appeliez **Requery**. Feuilles de réponse dynamiques n’utilisent pas la bibliothèque de curseurs.  
  
 La bibliothèque de curseurs vous donne les instantanés (curseurs statiques) même si elles ne sont normalement pas prises en charge par le pilote. Si votre pilote prend déjà en charge les curseurs statiques, il est inutile de le charger la bibliothèque de curseurs pour obtenir un support technique de capture instantanée. Si vous n’utilisez pas la bibliothèque de curseurs, vous pouvez utiliser uniquement les instantanés et recordsets avant uniquement. Si votre pilote prend en charge les feuilles de réponse dynamiques (curseurs KEYSET_DRIVEN) et que vous souhaitez les utiliser, vous ne devez pas utiliser la bibliothèque de curseurs. Si vous souhaitez utiliser les instantanés et les feuilles de réponse dynamiques, vous devez les baser sur deux `CDatabase` objets (deux connexions différentes), sauf si votre pilote prend en charge les deux.  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> Mises à jour positionnées et colonnes Timestamp  
  
> [!NOTE]
>  Sources de données ODBC sont accessibles via les classes ODBC MFC, comme décrit dans cette rubrique, ou via les classes MFC DAO Data Access Object ().  
  
> [!NOTE]
>  Si votre pilote ODBC prend en charge **SQLSetPos**, le MFC utilise s’il est disponible, cette rubrique ne s’applique pas à vous.  
  
 La plupart des pilotes de niveau 1 ne prennent pas en charge les mises à jour positionnées. Ces pilotes reposent sur la bibliothèque de curseurs pour émuler les capacités des pilotes de niveau 2 à cet effet. La bibliothèque de curseurs émule la prise en charge de la mise à jour positionnée en effectuant une mise à jour recherchée sur les champs qui ne changent pas.  
  
 Dans certains cas, un jeu d’enregistrements peut contenir une colonne timestamp en tant qu’un de ces champs qui ne changent pas. À l’aide de jeux d’enregistrements MFC avec des tables qui contiennent des colonnes d’horodatage soulève deux problèmes.  
  
 Le premier concerne les instantanés sur des tables avec des colonnes timestamp. Si la table à laquelle votre instantané est lié contient une colonne timestamp, vous devez appeler **Requery** après avoir appelé **modifier** et **mise à jour**. Si ce n’est pas le cas, vous n’êtes peut-être pas en mesure de modifier le même enregistrement à nouveau. Lorsque vous appelez **modifier** , puis **mise à jour**, l’enregistrement est écrit dans la source de données et la colonne horodateur est mise à jour. Si vous n’appelez pas **Requery**, la valeur d’horodatage pour l’enregistrement de votre instantané ne correspond plus à l’horodatage adéquat dans la source de données. Lorsque vous essayez de nouveau à jour l’enregistrement, la source de données peut ne pas autoriser la mise à jour en raison de l’incompatibilité.  
  
 Le second problème concerne les limites de la classe [CTime](../../atl-mfc-shared/reference/ctime-class.md) lorsqu’il est utilisé avec le `RFX_Date` fonction pour transférer des informations de date et heure vers ou à partir d’une table. Le traitement du `CTime` objet nécessite une certaine charge, sous la forme d’un traitement supplémentaire intermédiaire pendant le transfert de données. La plage de dates `CTime` objets peuvent également être trop limitée pour certaines applications. Une nouvelle version de la `RFX_Date` fonction prend une application ODBC **TIMESTAMP_STRUCT** au lieu du paramètre un `CTime` objet. Pour plus d’informations, consultez `RFX_Date` dans [Macros and Globals](../../mfc/reference/mfc-macros-and-globals.md) dans les *référence MFC*.  

  
##  <a name="_core_using_the_cursor_library"></a> À l’aide de la bibliothèque de curseurs  
 Lorsque vous vous connectez à une source de données, en appelant [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) ou [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) — vous pouvez spécifier s’il faut utiliser la bibliothèque de curseurs pour la source de données. Si vous allez créer des captures instantanées sur cette source de données, spécifiez la **CDatabase::useCursorLib** option dans le `dwOptions` paramètre `OpenEx` ou spécifiez **TRUE** pour la  **bUseCursorLib** paramètre **ouvrir** (la valeur par défaut est **TRUE**). Si votre pilote ODBC prend en charge les feuilles de réponse dynamiques et que vous souhaitez ouvrir des feuilles de réponse dynamiques sur la source de données, n’utilisez pas la bibliothèque de curseurs (elle masque certaines fonctionnalités du pilote nécessaire pour les dynasets). Dans ce cas, ne spécifiez pas **CDatabase::useCursorLib** dans `OpenEx` ou spécifiez **FALSE** pour le **bUseCursorLib** paramètre **ouvrir**.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments fondamentaux relatifs à ODBC](../../data/odbc/odbc-basics.md)