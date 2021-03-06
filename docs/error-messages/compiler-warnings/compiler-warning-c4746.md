---
description: 'En savoir plus sur : avertissement du compilateur C4746'
title: Avertissement du compilateur C4746
ms.date: 11/04/2016
f1_keywords:
- C4746
helpviewer_keywords:
- C4746
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 09c6b6968e7180e19955d84fdb69c9113509c39c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315034"
---
# <a name="compiler-warning-c4746"></a>Avertissement du compilateur C4746

l’accès volatile de' \<expression> 'est soumis au paramètre/volatile : [iso&#124;MS]; envisagez d’utiliser __iso_volatile_load fonctions intrinsèques/Store.

C4746 est émis chaque fois qu’une variable volatile est accédée directement. Elle est destinée à aider les développeurs à identifier les emplacements de code qui sont affectés par le modèle volatil spécifique actuellement spécifié (qui peut être contrôlé avec l’option de compilateur [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) ). En particulier, il peut être utile pour localiser les barrières de mémoire matérielle générées par le compilateur lorsque/volatile : ms est utilisé.

Les intrinsèques __iso_volatile_load/Store peuvent être utilisés pour accéder explicitement à la mémoire volatile sans être affectés par le modèle volatile. L’utilisation de ces fonctions intrinsèques ne déclenche pas C4746.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.
