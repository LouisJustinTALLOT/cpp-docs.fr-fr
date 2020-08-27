---
title: Restrictions sur les gestionnaires d’arrêts
description: Restrictions sur les gestionnaires de terminaisons de gestion structurée des exceptions.
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 60fdb4c2a105f2fce4a32f475563a04f8e7bfaf9
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898268"
---
# <a name="restrictions-on-termination-handlers"></a>Restrictions sur les gestionnaires de terminaison

Vous ne pouvez pas utiliser une **`goto`** instruction pour accéder à un **`__try`** bloc d’instructions ou à un **`__finally`** bloc d’instructions. À la place, vous devez entrer dans le bloc d'instruction via le flux de contrôle normal. (Toutefois, vous pouvez sauter hors d’un **`__try`** bloc d’instructions.) En outre, vous ne pouvez pas imbriquer un gestionnaire d’exceptions ou un gestionnaire de terminaisons à l’intérieur d’un **`__finally`** bloc.

Certains types de code autorisés dans un gestionnaire de terminaisons produisent des résultats douteux. vous devez donc les utiliser avec précaution, le cas échéant. L’une d’elles est une **`goto`** instruction qui saute d’un **`__finally`** bloc d’instructions. Si le bloc s’exécute dans le cadre de l’arrêt normal, rien d’inhabituel ne se produit. Toutefois, si le système déroule la pile, le déroulement s’arrête. Ensuite, la fonction active gagne le contrôle comme s’il n’existait aucun arrêt anormal.

Une **`return`** instruction à l’intérieur d’un **`__finally`** bloc d’instructions présente à peu près la même situation. Le contrôle retourne à l’appelant immédiat de la fonction qui contient le gestionnaire de terminaisons. Si le système déroulait la pile, ce processus est interrompu. Ensuite, le programme continue comme si aucune exception n’avait été levée.

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire des arrêts](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
