---
title: Avertissement du compilateur C4746 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e6abce7ebbcdc41effed05ccf54337e3976c34e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054861"
---
# <a name="compiler-warning-c4746"></a>Avertissement du compilateur C4746

accès volatile de «\<expression >' volatile : [iso&#124;ms] définition ; envisagez d’utiliser des fonctions intrinsèques __iso_volatile_load/store.

C4746 est émis chaque fois qu’une variable volatile est accessible directement. Il est destiné à aider les développeurs à identifier les emplacements de code qui sont affectés par le modèle de volatil spécifique actuellement spécifié (qui peut être contrôlé avec les [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) option du compilateur). En particulier, il peut être utile à localiser les barrières de mémoire matérielle généré par le compilateur quand /volatile:ms est utilisé.

Les fonctions intrinsèques __iso_volatile_load/store peuvent être utilisés pour accéder explicitement les mémoire volatile sans être affecté par le modèle de volatil. À l’aide de ces fonctions intrinsèques ne déclenche pas C4746.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.