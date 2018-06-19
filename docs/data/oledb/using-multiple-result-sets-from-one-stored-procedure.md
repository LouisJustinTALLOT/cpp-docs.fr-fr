---
title: À l’aide de plusieurs jeux de résultats d’une procédure stockée | Documents Microsoft
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
ms.openlocfilehash: 6393901839e8450ebc45b11f1d4bd2250da2ca56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106308"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Utilisation de plusieurs jeux de résultats à partir d'une seule procédure stockée
La plupart des procédures stockées retournent plusieurs jeux de résultats. Ce type de procédure stockée inclut généralement une ou plusieurs instructions select. Le consommateur doit en tenir compte pour gérer tous les jeux de résultats.  
  
### <a name="to-handle-multiple-result-sets"></a>Pour gérer les résultats multiples définit  
  
1.  Créer un `CCommand` classe avec `CMultipleResults` comme argument de modèle et avec l’accesseur de votre choix. En règle générale, il s’agit d’un accesseur dynamique ou manuel. Si vous utilisez un autre type d’accesseur, vous ne serez peut-être pas en mesure de déterminer les colonnes de sortie pour chaque ensemble de lignes.  
  
2.  Exécutez la procédure stockée comme d’habitude et liez les colonnes (consultez [comment faire pour extraire des données ?](../../data/oledb/fetching-data.md)).  
  
3.  Utiliser les données.  
  
4.  Appelez `GetNextResult` sur la `CCommand` classe. Si un autre ensemble de lignes de résultats est disponible, `GetNextResult` retourne S_OK et vous devez lier de nouveau vos colonnes si vous utilisez un accesseur manuel. Si `GetNextResult` retourne une erreur, il en existe aucun résultat supplémentaire ne jeux disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des procédures stockées](../../data/oledb/using-stored-procedures.md)