---
description: 'En savoir plus sur : utilisation de plusieurs jeux de résultats à partir d’une procédure stockée'
title: Utilisation de plusieurs jeux de résultats à partir d'une seule procédure stockée
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 8e6b7a51635caf9ddfd86dddcad0e2a3f94bb7dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319116"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Utilisation de plusieurs jeux de résultats à partir d'une seule procédure stockée

La plupart des procédures stockées retournent plusieurs jeux de résultats. Une telle procédure stockée comprend généralement une ou plusieurs instructions SELECT. Le consommateur doit prendre en compte cette inclusion pour gérer tous les jeux de résultats.

## <a name="to-handle-multiple-result-sets"></a>Pour gérer plusieurs jeux de résultats

1. Créez une `CCommand` classe avec `CMultipleResults` comme argument de modèle et avec l’accesseur de votre choix, généralement un accesseur dynamique ou manuel. Si vous utilisez un autre type d’accesseur, vous ne pourrez peut-être pas déterminer les colonnes de sortie pour chaque ensemble de lignes.

1. Exécutez la procédure stockée comme d’habitude et liez les colonnes (consultez [comment extraire des données ?](../../data/oledb/fetching-data.md)).

1. Utilisez les données.

1. Appelez `GetNextResult` sur la `CCommand` classe. Si un autre ensemble de lignes de résultats est disponible, `GetNextResult` retourne S_OK et vous devez relier vos colonnes si vous utilisez un accesseur manuel. Si `GetNextResult` retourne une erreur, aucun autre jeu de résultats n’est disponible.

## <a name="see-also"></a>Voir aussi

[Utilisation de procédures stockées](../../data/oledb/using-stored-procedures.md)
