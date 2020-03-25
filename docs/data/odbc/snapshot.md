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
ms.openlocfilehash: 62b5952f3052a3248175ce7892b1cf4615f1dd17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212691"
---
# <a name="snapshot"></a>Instantané

Un instantané est un jeu d’enregistrements qui reflète une vue statique des données telles qu’elles existaient au moment de la création de l’instantané. Lorsque vous ouvrez l’instantané et passez à tous les enregistrements, le jeu d’enregistrements qu’il contient et leurs valeurs ne changent pas tant que vous ne reconstruisez pas l’instantané en appelant `Requery`.

> [!NOTE]
>  Cette rubrique s’applique aux classes ODBC MFC. Si vous utilisez les classes DAO MFC au lieu des classes ODBC MFC, consultez [CDaoRecordset :: Open](../../mfc/reference/cdaorecordset-class.md#open) pour obtenir une description des jeux d’enregistrements de type instantané.

Vous pouvez créer des captures instantanées modifiables ou en lecture seule avec les classes de base de données. Contrairement à une feuille de réponse dynamique, un instantané actualisable ne reflète pas les modifications apportées aux valeurs d’enregistrement effectuées par d’autres utilisateurs, mais il reflète les mises à jour et les suppressions effectuées par votre programme. Les enregistrements ajoutés à un instantané ne sont pas visibles par l’instantané tant que vous n’appelez pas `Requery`.

> [!TIP]
>  Un instantané est un curseur statique ODBC. Les curseurs statiques n’obtiennent pas réellement une ligne de données tant que vous n’avez pas fait défiler vers cet enregistrement. Pour vous assurer que tous les enregistrements sont immédiatement récupérés, vous pouvez faire défiler jusqu’à la fin de votre Recordset, puis faire défiler jusqu’au premier enregistrement que vous souhaitez afficher. Notez, toutefois, que le défilement jusqu’à la fin entraîne une surcharge supplémentaire et peut réduire les performances.

Les instantanés sont particulièrement utiles lorsque vous avez besoin que les données restent fixes pendant vos opérations, comme lorsque vous générez un rapport ou effectuez des calculs. Même dans ce cas, la source de données peut s’écarter considérablement de votre capture instantanée. il est donc préférable de la régénérer de temps en temps.

La prise en charge des instantanés est basée sur la bibliothèque de curseurs ODBC, qui fournit des curseurs statiques et des mises à jour positionnées (nécessaires à la mise à jour) pour n’importe quel pilote de niveau 1. La DLL de la bibliothèque de curseurs doit être chargée en mémoire pour cette prise en charge. Lorsque vous construisez un objet `CDatabase` et appelez sa fonction membre `OpenEx`, vous devez spécifier l’option `CDatabase::useCursorLib` du paramètre *dwOptions* . Si vous appelez la fonction membre `Open`, la bibliothèque de curseurs est chargée par défaut. Si vous utilisez des feuilles de réponse dynamiques plutôt que des instantanés, vous ne souhaitez pas que la bibliothèque de curseurs soit chargée.

Les instantanés sont disponibles uniquement si la bibliothèque de curseurs ODBC a été chargée lors de la construction de l’objet `CDatabase` ou si le pilote ODBC que vous utilisez prend en charge les curseurs statiques.

> [!NOTE]
>  Pour certains pilotes ODBC, les instantanés (curseurs statiques) peuvent ne pas pouvoir être mis à jour. Consultez la documentation de votre pilote pour les types de curseurs pris en charge et les types d’accès concurrentiel qu’ils prennent en charge. Pour garantir la mise à jour des instantanés, assurez-vous de charger la bibliothèque de curseurs en mémoire lorsque vous créez un objet `CDatabase`. Pour plus d’informations, consultez [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
>  Si vous souhaitez utiliser à la fois des instantanés et des feuilles de réponse dynamiques, vous devez les baser sur deux objets de `CDatabase` différents (deux connexions différentes).

Pour plus d’informations sur les propriétés partage des instantanés avec tous les jeux d’enregistrements, consultez [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations sur ODBC et les instantanés, notamment la bibliothèque de curseurs ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)
