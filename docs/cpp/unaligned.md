---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 2ab94a44d08165ca6e8f394278e24d7c8d201398
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223497"
---
# <a name="__unaligned"></a>__unaligned

**Spécifique à Microsoft**. Quand vous déclarez un pointeur avec le **`__unaligned`** modificateur, le compilateur suppose que le pointeur adresse des données qui ne sont pas alignées. Par conséquent, le code approprié à la plateforme est généré pour gérer les lectures et écritures non alignées via le pointeur.

## <a name="remarks"></a>Notes

Ce modificateur décrit l’alignement des données adressées par le pointeur ; le pointeur lui-même est supposé être aligné.

La nécessité du **`__unaligned`** mot clé varie selon la plateforme et l’environnement. Si vous ne Marquez pas les données de manière appropriée, vous risquez de provoquer des problèmes de performances et de défaillances matérielles. Le **`__unaligned`** modificateur n’est pas valide pour la plateforme x86.

Pour la compatibilité avec les versions précédentes, **`_unaligned`** est un synonyme de, **`__unaligned`** sauf si l’option de compilateur [ `/Za` \( désactive les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Pour plus d'informations sur l'alignement, consultez :

- [`align`](../cpp/align-cpp.md)

- [`alignof`And](../cpp/alignof-operator.md)

- [`pack`](../preprocessor/pack.md)

- [`/Zp`(Alignement des membres de la structure)](../build/reference/zp-struct-member-alignment.md)

- [Exemples d'alignement de structure](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
