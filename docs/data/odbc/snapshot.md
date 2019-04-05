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
ms.openlocfilehash: 5999f89156d895ff0c87c892be892c6a614a0132
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037644"
---
# <a name="snapshot"></a>Instantané

Un instantané est un jeu d’enregistrements qui reflète une vue statique des données telles qu’elles existaient au moment de que l’instantané a été créé. Lorsque vous ouvrez l’instantané et déplacez tous les enregistrements, le jeu d’enregistrements qu’il contient et leurs valeurs ne changent pas jusqu'à ce que vous reconstruisez l’instantané en appelant `Requery`.

> [!NOTE]
>  Cette rubrique s’applique aux classes ODBC MFC. Si vous utilisez les classes DAO MFC plutôt que des classes ODBC MFC, consultez [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) pour obtenir une description des jeux d’enregistrements de type instantané.

Vous pouvez créer des instantanés modifiables ou en lecture seule avec les classes de base de données. Contrairement à une feuille de réponse dynamique, un instantané modifiable ne reflète pas les modifications apportées par d’autres utilisateurs des valeurs d’enregistrement, mais il ne reflète pas les mises à jour et suppressions effectuées par votre programme. Les enregistrements ajoutés à un instantané ne sont pas visibles dans l’instantané jusqu'à ce que vous appeliez `Requery`.

> [!TIP]
>  Un instantané est un curseur statique ODBC. En fait, les curseurs statiques n’obtiennent pas d’une ligne de données jusqu'à ce que vous faites défiler vers cet enregistrement. Pour vous assurer que tous les enregistrements sont immédiatement extraits, vous pouvez faire défiler jusqu'à la fin de votre jeu d’enregistrements et puis faites défiler vers le premier enregistrement que vous souhaitez afficher. Notez, cependant, que le défilement vers la fin implique une charge supplémentaire et peut diminuer les performances.

Les instantanés sont plus utiles lorsque vous avez besoin des données de rester fixe pendant vos opérations, comme lorsque vous êtes génération d’un rapport ou effectuer des calculs. Même dans ce cas, la source de données peut différer considérablement de votre instantané, donc vous souhaiterez peut-être régénérer, de temps à autre.

Prise en charge de l’instantané est basée sur la bibliothèque de curseurs ODBC, qui fournit des curseurs statiques et de mises à jour (nécessaires pour la mise à jour) pour n’importe quel pilote de niveau 1 positionnées. La DLL de bibliothèque de curseurs doit être chargée en mémoire pour cette prise en charge. Lorsque vous construisez un `CDatabase` objet et appelez sa `OpenEx` fonction membre, vous devez spécifier le `CDatabase::useCursorLib` option de le *dwOptions* paramètre. Si vous appelez le `Open` fonction membre, la bibliothèque de curseurs est chargée par défaut. Si vous utilisez des feuilles de réponse dynamiques au lieu de captures instantanées, vous ne souhaitez pas que la bibliothèque de curseurs à charger.

Les instantanés sont disponibles uniquement si la bibliothèque de curseurs ODBC a été chargée lorsque le `CDatabase` objet a été construit, ou le pilote ODBC que vous utilisez prend en charge les curseurs statiques.

> [!NOTE]
>  Pour certains pilotes ODBC, instantanés (curseurs statiques) n’est peut-être pas modifiables. Vérifiez la documentation de votre pilote pour les types de curseurs pris en charge et les types d’accès concurrentiel que pris en charge. Pour garantir les instantanés, assurez-vous de charger la bibliothèque de curseurs en mémoire lorsque vous créez un `CDatabase` objet. Pour plus d’informations, consultez [ODBC : La bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
>  Si vous souhaitez utiliser les instantanés et les feuilles de réponse dynamiques, vous devez les baser sur deux différents `CDatabase` objets (deux connexions différentes).

Pour plus d’informations sur le partage de captures instantanées de propriétés avec tous les jeux d’enregistrements, consultez [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations sur ODBC et les captures instantanées, y compris la bibliothèque de curseurs ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Voir aussi

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)