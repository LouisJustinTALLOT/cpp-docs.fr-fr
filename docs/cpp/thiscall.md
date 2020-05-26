---
title: __thiscall
ms.date: 05/22/2020
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: b9edc2cd8caa5fd5458f6a53c5fdb1f8a5e69914
ms.sourcegitcommit: 5bb421fdf61d290cac93a03e16a6a80959accf6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83854812"
---
# `__thiscall`

La **Microsoft-specific** **`__thiscall`** Convention d’appel spécifique à Microsoft est utilisée sur les fonctions membres de classe C++ sur l’architecture x86. Il s’agit de la Convention d’appel par défaut utilisée par les fonctions membres qui n’utilisent pas d’arguments de variables ( `vararg` fonctions).

Sous **`__thiscall`** , l’appelé nettoie la pile, ce qui est impossible pour les `vararg` fonctions. Les arguments font l’objet d’un push sur la pile de droite à gauche. Le **`this`** pointeur est passé via le registre ECX et non pas sur la pile.

Sur les machines ARM, ARM64 et x64, **`__thiscall`** est accepté et ignoré par le compilateur. Cela est dû au fait qu’ils utilisent par défaut une convention d’appel basée sur un registre.

L’une des raisons d’utiliser **`__thiscall`** est dans les classes dont les fonctions membres utilisent **`__clrcall`** par défaut. Dans ce cas, vous pouvez utiliser **`__thiscall`** pour que les fonctions membres individuelles puissent être appelées à partir du code natif.

Lors de la compilation avec [**`/clr:pure`**](../build/reference/clr-common-language-runtime-compilation.md) , toutes les fonctions et les pointeurs fonction sont **`__clrcall`** sauf indication contraire. Les **`/clr:pure`** **`/clr:safe`** Options du compilateur et sont dépréciées dans visual studio 2015 et ne sont pas prises en charge dans visual studio 2017.

`vararg`les fonctions membres utilisent la **`__cdecl`** Convention d’appel. Tous les arguments de fonction font l’objet d’un push sur la pile, avec le **`this`** pointeur placé sur la pile en dernier.

Étant donné que cette Convention d’appel s’applique uniquement à C++, elle n’a pas de schéma de décoration de nom C.

Quand vous définissez une fonction membre de classe non statique hors ligne, spécifiez le modificateur de convention d’appel uniquement dans la déclaration. Vous n’êtes pas obligé de le spécifier à nouveau sur la définition hors ligne. Le compilateur utilise la Convention d’appel spécifiée pendant la déclaration au point de définition.

## <a name="see-also"></a>Voir aussi

[Passage des arguments et conventions de nommage](../cpp/argument-passing-and-naming-conventions.md)
