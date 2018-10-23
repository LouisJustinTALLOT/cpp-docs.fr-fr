---
title: À l’aide de plusieurs jeux de résultats à partir d’une procédure stockée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 70fab2751e216ca90dbe09e31c88f9aa80aa7b90
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808262"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Utilisation de plusieurs jeux de résultats à partir d'une seule procédure stockée

La plupart des procédures stockées retournent plusieurs jeux de résultats. Une telle procédure stockée inclut généralement une ou plusieurs instructions select. Le consommateur doit prendre en compte cette inscription pour gérer tous les jeux de résultats.  
  
## <a name="to-handle-multiple-result-sets"></a>Pour gérer les résultats multiples définit  
  
1. Créer un `CCommand` classe avec `CMultipleResults` comme argument de modèle et avec l’accesseur de votre choix, généralement un accesseur dynamique ou manuel. Si vous utilisez un autre type d’accesseur, vous ne serez peut-être pas en mesure de déterminer les colonnes de sortie pour chaque ensemble de lignes.  
  
1. Exécutez la procédure stockée comme d’habitude et liez les colonnes (consultez [comment extraire des données ?](../../data/oledb/fetching-data.md)).  
  
1. Utiliser les données.  
  
1. Appelez `GetNextResult` sur la `CCommand` classe. Si un autre ensemble de lignes de résultat n’est disponible, `GetNextResult` retourne S_OK et vous devez lier de nouveau vos colonnes si vous utilisez un accesseur manuel. Si `GetNextResult` retourne une erreur, il en existe aucun résultat supplémentaire ne jeux disponible.  
  
## <a name="see-also"></a>Voir aussi  

[Utilisation des procédures stockées](../../data/oledb/using-stored-procedures.md)