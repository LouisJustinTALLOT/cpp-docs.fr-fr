---
title: Instantané | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 309c81e8d370b61ba3a44d9253cda4fa9b84b6cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094762"
---
# <a name="snapshot"></a>Instantané
Un instantané est un jeu d’enregistrements qui reflète une vue statique des données telles qu’elles existaient au moment de que l’instantané a été créé. Lorsque vous ouvrez l’instantané et déplacez tous les enregistrements, le jeu d’enregistrements et leurs valeurs ne changent pas jusqu'à ce que vous reconstruisiez l’instantané en appelant **Requery**.  
  
> [!NOTE]
>  Cette rubrique s’applique aux classes ODBC MFC. Si vous utilisez les classes DAO MFC plutôt que les classes ODBC MFC, consultez [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) pour obtenir une description des jeux d’enregistrements de type instantané.  
  
 Vous pouvez créer des instantanés en lecture seule ou être mis à jour avec les classes de base de données. Contrairement à une feuille de réponse dynamique, un instantané modifiable ne reflète pas les modifications apportées par d’autres utilisateurs des valeurs d’enregistrement, mais il ne reflète pas les mises à jour et suppressions effectuées par votre programme. Les enregistrements ajoutés à un instantané ne sont pas visibles dans l’instantané avant l’appel de **Requery**.  
  
> [!TIP]
>  Un instantané est un curseur statique ODBC. Les curseurs statiques n’obtiennent pas réellement une ligne de données jusqu'à ce que vous faites défiler à cet enregistrement. Pour vous assurer que tous les enregistrements sont immédiatement extraits, vous pouvez faire défiler jusqu'à la fin de votre jeu d’enregistrements et puis faites défiler vers le premier enregistrement que vous souhaitez afficher. Toutefois, notez que le défilement à la fin implique une charge supplémentaire et peut diminuer la performance.  
  
 Les instantanés sont plus utiles lorsque les données doivent rester fixes lors de vos opérations, comme lors de la génération d’un rapport ou de calculs. Même dans ce cas, la source de données peut différer considérablement de votre instantané, donc vous souhaiterez peut-être régénérer, de temps à autre.  
  
 Prise en charge de l’instantané est basée sur la bibliothèque de curseurs ODBC, qui procure des curseurs statiques et positionné mises à jour (nécessaires pour la mise à jour) pour un pilote de niveau 1. La DLL de bibliothèque de curseurs doit être chargée en mémoire pour cette prise en charge. Lorsque vous construisez un `CDatabase` objet et appeler ses `OpenEx` fonction membre, vous devez spécifier le **CDatabase::useCursorLib** option de le `dwOptions` paramètre. Si vous appelez le **ouvrir** fonction membre, la bibliothèque de curseurs est chargée par défaut. Si vous utilisez des feuilles de réponse dynamiques à la place d’instantanés, vous ne souhaitez pas que la bibliothèque de curseurs doit être chargé.  
  
 Les instantanés sont disponibles uniquement si la bibliothèque de curseurs ODBC était chargée lors la `CDatabase` objet a été construit, ou le pilote ODBC que vous utilisez prend en charge les curseurs statiques.  
  
> [!NOTE]
>  Pour certains pilotes ODBC, les instantanés (curseurs statiques) n’est peut-être pas être mis à jour. Vérifiez la documentation du pilote pour les types de curseurs pris en charge et les types d’accès concurrentiel que pris en charge. Pour garantir les instantanés, assurez-vous de charger la bibliothèque de curseurs en mémoire lorsque vous créez un `CDatabase` objet. Pour plus d’informations, consultez [ODBC : bibliothèque de curseurs ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!NOTE]
>  Si vous souhaitez utiliser les instantanés et les feuilles de réponse dynamiques, vous devez les baser sur deux `CDatabase` objets (deux connexions différentes).  
  
 Pour plus d’informations sur le partage d’instantanés de propriétés avec tous les jeux d’enregistrements, consultez [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Pour plus d’informations sur ODBC et les instantanés, y compris la bibliothèque de curseurs ODBC, consultez [ODBC](../../data/odbc/odbc-basics.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)