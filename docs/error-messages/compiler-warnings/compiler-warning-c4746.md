---
title: Avertissement du compilateur C4746
ms.date: 11/04/2016
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 1b79eed2134b8c6310e508e56b3388c6f38fe4b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311106"
---
# <a name="compiler-warning-c4746"></a>Avertissement du compilateur C4746

accès volatile de «\<expression >' volatile : [iso&#124;ms] définition ; envisagez d’utiliser des fonctions intrinsèques __iso_volatile_load/store.

C4746 est émis chaque fois qu’une variable volatile est accessible directement. Il est destiné à aider les développeurs à identifier les emplacements de code qui sont affectés par le modèle de volatil spécifique actuellement spécifié (qui peut être contrôlé avec les [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur). En particulier, il peut être utile à localiser les barrières de mémoire matérielle généré par le compilateur quand /volatile:ms est utilisé.

Les fonctions intrinsèques __iso_volatile_load/store peuvent être utilisés pour accéder explicitement les mémoire volatile sans être affecté par le modèle de volatil. À l’aide de ces fonctions intrinsèques ne déclenche pas C4746.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.