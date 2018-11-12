---
title: Avertissement du compilateur (niveaux 1 et 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 20e44eba3b6f6079e6f37b7cf33fa530a996e829
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462957"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Avertissement du compilateur (niveaux 1 et 4) C4115

'type' : définition d’un type nommé dans les parenthèses

Le symbole donné est utilisé pour définir une structure, une union ou un type énuméré dans une expression entre parenthèses. La portée de la définition peut être inattendue.

Dans un appel de fonction C, la définition a une portée globale. Dans un appel C++, la définition a la même portée que la fonction appelée.

Cet avertissement peut également être dû à des déclarateurs entre parenthèses (tels que des prototypes) qui ne sont pas des expressions entre parenthèses.

Il s’agit d’un avertissement de niveau 1 avec les programmes C++ et les programmes C compilés sous compatibilité ANSI (/Za). Sinon, il s’agit d’un avertissement de niveau 3.