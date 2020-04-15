---
title: Instantané
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
ms.openlocfilehash: e487b5abcc5eee4e3f4b1941100980eac4a040c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366906"
---
# <a name="snapshot"></a>Instantané

Un instantané est un ensemble d’enregistrements qui reflète une vue statique des données telles qu’elles existaient au moment de la création de l’instantané. Lorsque vous ouvrez l’instantané et passez à tous les enregistrements, l’ensemble d’enregistrements `Requery`qu’il contient et leurs valeurs ne changent pas jusqu’à ce que vous reconstruisez l’instantané en appelant .

> [!NOTE]
> Cette rubrique s’applique aux classes ODBC MFC. Si vous utilisez les classes MFC DAO au lieu des classes MFC ODBC, voir [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) pour une description des enregistrements de type instantané.

Vous pouvez créer des instantanés actualisables ou lus uniquement avec les classes de base de données. Contrairement à un dynaset, un instantané à jour ne reflète pas les changements apportés aux valeurs d’enregistrement des autres utilisateurs, mais il reflète les mises à jour et les suppressions effectuées par votre programme. Les enregistrements ajoutés à un instantané ne `Requery`deviennent pas visibles à l’instantané jusqu’à ce que vous appelez .

> [!TIP]
> Un instantané est un curseur statique ODBC. Les curseurs statiques n’obtiennent pas réellement une rangée de données jusqu’à ce que vous faites défiler à cet enregistrement. Pour vous assurer que tous les enregistrements sont immédiatement récupérés, vous pouvez faire défiler jusqu’à la fin de votre ensemble d’enregistrements, puis faire défiler le premier enregistrement que vous souhaitez voir. Notez, cependant, que le défilement à la fin implique des frais généraux supplémentaires et peut réduire les performances.

Les instantanés sont plus précieux lorsque vous avez besoin que les données restent fixes pendant vos opérations, comme lorsque vous génèrez un rapport ou effectuez des calculs. Malgré cela, la source de données peut diverger considérablement de votre instantané, de sorte que vous voudrez peut-être le reconstruire de temps en temps.

Le support instantané est basé sur la bibliothèque ODBC Cursor, qui fournit des curseurs statiques et des mises à jour positionnées (nécessaires à la mise à jour) pour tout pilote de niveau 1. La bibliothèque de curseurs DLL doit être chargée en mémoire pour ce support. Lorsque vous `CDatabase` construisez un `OpenEx` objet et appelez `CDatabase::useCursorLib` sa fonction de membre, vous devez spécifier l’option du paramètre *dwOptions.* Si vous `Open` appelez la fonction membre, la bibliothèque de curseur est chargée par défaut. Si vous utilisez des dynasets au lieu d’instantanés, vous ne voulez pas charger la bibliothèque de curseurs.

Les instantanés ne sont disponibles que si la `CDatabase` bibliothèque de cursoires ODBC a été chargée lorsque l’objet a été construit ou le conducteur ODBC que vous utilisez prend en charge les curseurs statiques.

> [!NOTE]
> Pour certains conducteurs de l’ODBC, les instantanés (curseurs statiques) peuvent ne pas être mis à jour. Vérifiez la documentation de votre conducteur pour les types de curseurs pris en charge et les types de concurrence qu’ils prennent en charge. Pour garantir des instantanés à jour, assurez-vous de charger `CDatabase` la bibliothèque de curseurs en mémoire lorsque vous créez un objet. Pour plus d’informations, voir [ODBC: The ODBC Cursor Library](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> Si vous souhaitez utiliser à la fois des instantanés et des `CDatabase` dynasets, vous devez les baser sur deux objets différents (deux connexions différentes).

Pour plus d’informations sur les propriétés instantanés partager avec tous les enregistrements, voir [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations sur ODBC et des instantanés, y compris la Bibliothèque des curseurs ODBC, voir [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Voir aussi

[Connectivité open Database (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
