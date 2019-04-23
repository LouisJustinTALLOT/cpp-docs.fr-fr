---
title: Utilisation de plusieurs jeux de résultats à partir d'une seule procédure stockée
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 69e5c956d897e217501cbac9b9b93db868731221
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028423"
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