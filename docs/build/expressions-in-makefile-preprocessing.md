---
title: Expressions de prétraitement d’un Makefile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1070eb01802bd4b39f62ae24519ad6dabca7eb90
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719003"
---
# <a name="expressions-in-makefile-preprocessing"></a>Expressions utilisées dans le prétraitement d'un makefile

Le **! IF** ou **! ELSE IF** `constantexpression` se compose de constantes entières (notation décimale ou en langage C), de constantes de chaîne ou de commandes. Utilisez des parenthèses pour grouper des expressions. Les expressions utiliser C-style entier long signé arithmétique ; nombres se présentent sous forme de 32 bits de complément à 2 dans la plage - 2147483648 et 2147483647.

Les expressions peuvent utiliser des opérateurs qui agissent sur des valeurs constantes, les codes de sortie des commandes, les chaînes, les macros et les chemins d’accès de système de fichiers.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Opérateurs de prétraitement d’un makefile](../build/makefile-preprocessing-operators.md)

[Exécution d’un programme en prétraitement](../build/executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>Voir aussi

[Prétraitement d’un makefile](../build/makefile-preprocessing.md)