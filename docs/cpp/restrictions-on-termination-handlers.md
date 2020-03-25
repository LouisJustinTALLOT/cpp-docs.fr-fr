---
title: Restrictions sur les gestionnaires de terminaison
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: befe181a41ed418a4a824b131e741a9f02f90e38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179066"
---
# <a name="restrictions-on-termination-handlers"></a>Restrictions sur les gestionnaires de terminaison

Vous ne pouvez pas utiliser une instruction **goto** pour accéder à un bloc d’instructions **__try** ou à un bloc d’instructions **__finally** . À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. (Vous pouvez toutefois passer d’un bloc d’instructions **__try** .) En outre, vous ne pouvez pas imbriquer un gestionnaire d’exceptions ou un gestionnaire de terminaisons à l’intérieur d’un bloc de **__finally** .

Certains types de code autorisés dans un gestionnaire de terminaisons produisent des résultats incertains. Si vous en utilisez, faites-le avec précaution. L’une d’elles est une instruction **goto** qui saute hors d’un bloc d’instructions **__finally** . Si le bloc s'exécute dans le cadre de l'arrêt normal, rien d'inhabituel ne se produit. Mais si le système est en train de dérouler la pile, ce déroulement s'arrête, et la fonction actuelle prend le contrôle comme s'il n'y avait pas eu d'arrêt anormal.

Une instruction **Return** à l’intérieur d’un bloc d’instructions **__finally** présente à peu près la même situation. Le contrôle retourne à l'appelant immédiat de la fonction contenant le gestionnaire de terminaisons. Si le système était en train de dérouler la pile, ce processus est désactivé, et le programme continue comme si aucune exception n'était levée.

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire de terminaisons](../cpp/writing-a-termination-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
