---
title: Utilisation de plusieurs jeux de résultats à partir d'une seule procédure stockée
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 6163eb8bf18edfc3d205f1d012de0c64c5570693
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209285"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Utilisation de plusieurs jeux de résultats à partir d'une seule procédure stockée

La plupart des procédures stockées retournent plusieurs jeux de résultats. Une telle procédure stockée comprend généralement une ou plusieurs instructions SELECT. Le consommateur doit prendre en compte cette inclusion pour gérer tous les jeux de résultats.

## <a name="to-handle-multiple-result-sets"></a>Pour gérer plusieurs jeux de résultats

1. Créez une classe `CCommand` avec `CMultipleResults` comme argument template et avec l’accesseur de votre choix, généralement un accesseur dynamique ou manuel. Si vous utilisez un autre type d’accesseur, vous ne pourrez peut-être pas déterminer les colonnes de sortie pour chaque ensemble de lignes.

1. Exécutez la procédure stockée comme d’habitude et liez les colonnes (consultez [comment extraire des données ?](../../data/oledb/fetching-data.md)).

1. Utilisez les données.

1. Appelez `GetNextResult` sur la classe `CCommand`. Si un autre ensemble de lignes de résultats est disponible, `GetNextResult` retourne S_OK et vous devez relier vos colonnes si vous utilisez un accesseur manuel. Si `GetNextResult` retourne une erreur, aucun autre jeu de résultats n’est disponible.

## <a name="see-also"></a>Voir aussi

[Utilisation des procédures stockées](../../data/oledb/using-stored-procedures.md)
