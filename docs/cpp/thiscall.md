---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: fc5a32fedf52377889b61103856e2125733cd696
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448839"
---
# <a name="thiscall"></a>__thiscall

**Section spécifique à Microsoft**

Le **__thiscall** convention d’appel est utilisée sur les fonctions membres et est la convention d’appel par défaut utilisée par les fonctions membres C++ qui n’utilisent pas d’arguments variables. Sous **__thiscall**, l’appelé nettoie la pile, ce qui est impossible pour `vararg` fonctions. Arguments sont transmis sur la pile de droite à gauche, avec le **cela** pointeur transmis via le Registre ECX et non sur la pile, sur le x86 architecture.

Une des raisons d’utiliser **__thiscall** est dans les classes dont le membre fonctions utilisent `__clrcall` par défaut. Dans ce cas, vous pouvez utiliser **__thiscall** pour rendre les fonctions membres individuelles pouvant être appelé à partir du code natif.

Lors de la compilation avec [/CLR : pure](../build/reference/clr-common-language-runtime-compilation.md), toutes les fonctions et les pointeurs de fonction sont `__clrcall` , sauf indication contraire. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Dans les versions antérieures à Visual C++ 2005, le **__thiscall** convention d’appel pas pu être explicitement spécifiée dans un programme, car **__thiscall** n’était pas un mot clé.

`vararg` utilisation de fonctions membres le **__cdecl** convention d’appel. Tous les arguments de fonction sont envoyées sur la pile, avec le **cela** pointeur placées en dernier sur la pile

Comme cette convention d’appel s’applique uniquement à C++, il n’y a aucun schéma de décoration de nom C.

Sur ARM et x64 machines, **__thiscall** est accepté et ignoré par le compilateur.

Pour les fonctions de classe non statiques, si la fonction est définie hors ligne, il n’est pas nécessaire de spécifier le modificateur de convention d’appel dans la définition hors ligne. En d’autres termes, pour les méthodes membres non statiques de classe, la convention d’appel spécifiée dans le cadre de la déclaration est utilisée par défaut au stade de la définition.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)