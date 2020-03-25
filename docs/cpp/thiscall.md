---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 8772159dca71bb7605af5e5919425065423d503d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188153"
---
# <a name="__thiscall"></a>__thiscall

**Section spécifique de Microsoft**

La Convention d’appel **__thiscall** est utilisée sur les fonctions membres et est la Convention d’appel C++ par défaut utilisée par les fonctions membres qui n’utilisent pas d’arguments de variables. Sous **__thiscall**, l’appelé nettoie la pile, ce qui est impossible pour les fonctions `vararg`. Les arguments font l’objet d’un push sur la pile de droite à gauche, avec le pointeur **This** passé via le registre ECX et non sur la pile, sur l’architecture x86.

L’une des raisons d’utiliser **__thiscall** se trouve dans les classes dont les fonctions membres utilisent `__clrcall` par défaut. Dans ce cas, vous pouvez utiliser **__thiscall** pour que les fonctions membres puissent être appelées à partir du code natif.

Lors de la compilation avec [/clr : pure](../build/reference/clr-common-language-runtime-compilation.md), toutes les fonctions et les pointeurs fonction sont `__clrcall`, sauf indication contraire. Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Dans les versions antérieures à Visual Studio 2005, la Convention d’appel **__thiscall** n’a pas pu être spécifiée explicitement dans un programme, car **__thiscall** n’était pas un mot clé.

`vararg` fonctions membres utilisent la Convention d’appel **__cdecl** . Tous les arguments de fonction font l’objet d’un push sur la pile, avec le pointeur **This** placé sur la pile en dernier

Étant donné que cette Convention d’appel C++s’applique uniquement à, il n’existe aucun schéma de décoration de nom C.

Sur les ordinateurs ARM et x64, **__thiscall** est accepté et ignoré par le compilateur.

Pour les fonctions de classe non statiques, si la fonction est définie hors ligne, il n’est pas nécessaire de spécifier le modificateur de convention d’appel dans la définition hors ligne. En d’autres termes, pour les méthodes membres non statiques de classe, la convention d’appel spécifiée dans le cadre de la déclaration est utilisée par défaut au stade de la définition.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)
