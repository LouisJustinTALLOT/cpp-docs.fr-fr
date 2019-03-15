---
title: Expressions utilisées dans le prétraitement d'un makefile
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
ms.openlocfilehash: 3d668492441eb2fc09be378dbebfe2b18c1b5753
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826013"
---
# <a name="expressions-in-makefile-preprocessing"></a>Expressions utilisées dans le prétraitement d'un makefile

Le **! IF** ou **! ELSE IF** `constantexpression` se compose de constantes entières (notation décimale ou en langage C), de constantes de chaîne ou de commandes. Utilisez des parenthèses pour grouper des expressions. Les expressions utiliser C-style entier long signé arithmétique ; nombres se présentent sous forme de 32 bits de complément à 2 dans la plage - 2147483648 et 2147483647.

Les expressions peuvent utiliser des opérateurs qui agissent sur des valeurs constantes, les codes de sortie des commandes, les chaînes, les macros et les chemins d’accès de système de fichiers.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Opérateurs de prétraitement d’un makefile](makefile-preprocessing-operators.md)

[Exécution d’un programme en prétraitement](executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>Voir aussi

[Prétraitement d’un makefile](makefile-preprocessing.md)
