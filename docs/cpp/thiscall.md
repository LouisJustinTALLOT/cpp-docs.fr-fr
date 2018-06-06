---
title: __thiscall | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __thiscall
- __thiscall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4912628529ae0b47a5a5b938ab8e6d25a9099510
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704401"
---
# <a name="thiscall"></a>__thiscall

**Section spécifique à Microsoft**

Le `__thiscall` convention d’appel est utilisé sur les fonctions membres et est la convention d’appel par défaut utilisé par les fonctions membres C++ qui n’utilisent pas d’arguments variables. Sous `__thiscall`, l’appelé nettoie la pile, qui est impossible pour `vararg` fonctions. Arguments sont insérés dans la pile de droite à gauche, avec le `this` pointeur transmis via le Registre ECX et non sur la pile, dans le x86 architecture.

L’une des raisons d’utiliser `__thiscall` est dans les classes dont le membre fonctions utilisent `__clrcall` par défaut. Dans ce cas, vous pouvez utiliser `__thiscall` pour rendre les fonctions membre individuel peut être appelée à partir du code natif.

Lors de la compilation avec [/CLR : pure](../build/reference/clr-common-language-runtime-compilation.md), tous les pointeurs de fonction et les fonctions sont `__clrcall` , sauf indication contraire. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Dans les versions antérieures de Visual C++ 2005, le `__thiscall` convention d’appel pas pu être explicitement spécifié dans un programme, car `__thiscall` n’était pas un mot clé.

`vararg` Utilisez les fonctions membres le `__cdecl` convention d’appel. Tous les arguments de fonction sont insérés dans la pile, avec le `this` pointeur placées en dernier dans la pile

Étant donné que cette convention d’appel s’applique uniquement à C++, il n’existe aucun schéma de décoration de nom C.

Sur ARM et x64 machines, `__thiscall` est accepté et ignoré par le compilateur.

Pour les fonctions de classe non statiques, si la fonction est définie hors ligne, il n’est pas nécessaire de spécifier le modificateur de convention d’appel dans la définition hors ligne. En d’autres termes, pour les méthodes membres non statiques de classe, la convention d’appel spécifiée dans le cadre de la déclaration est utilisée par défaut au stade de la définition.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

- [Passage des arguments et conventions de dénomination](../cpp/argument-passing-and-naming-conventions.md)
