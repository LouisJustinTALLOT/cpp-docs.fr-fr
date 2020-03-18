---
title: __alignof, opérateur
ms.date: 12/17/2018
f1_keywords:
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: b3764e95846d48d293991d69d04bc71c6b3aed90
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443605"
---
# <a name="__alignof-operator"></a>__alignof, opérateur

C++ 11 introduit l’opérateur **alignof** qui retourne l’alignement, en octets, du type spécifié. Pour une portabilité maximale, vous devez utiliser l'opérateur alignof au lieu de l'opérateur __alignof spécifique à Microsoft.

**Section spécifique de Microsoft**

Retourne une valeur de type `size_t` qui correspond à l’exigence d’alignement du type.

## <a name="syntax"></a>Syntaxe

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Notes

Par exemple :

|Expression|Valeur|
|----------------|-----------|
|**__alignof (Char)**|1|
|**__alignof (short)**|2|
|**__alignof (int)**|4|
|**__alignof (\__int64)**|8|
|**__alignof (float)**|4|
|**__alignof (double)**|8|
|**__alignof (char\*)**|4|

La valeur **__alignof** est identique à la valeur de `sizeof` pour les types de base. Observons toutefois l'exemple suivant :

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

Dans ce cas, la valeur **__alignof** est l’exigence d’alignement du plus grand élément de la structure.

De même, pour

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` est égal à `32`.

Une utilisation de **__alignof** serait en tant que paramètre pour l’une de vos propres routines d’allocation de mémoire. Par exemple, dans la structure définie `S`suivante, vous pouvez appeler une routine d'allocation de mémoire nommée `aligned_malloc` pour allouer la mémoire sur une limite d'alignement particulière.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

Pour la compatibilité avec les versions précédentes, **_alignof** est un synonyme de **__alignof** sauf si l’option de compilateur [/za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Pour plus d'informations sur la modification de l'alignement, consultez :

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (Alignement des membres de la structure)](../build/reference/zp-struct-member-alignment.md)

- [Exemples d’alignement de structure](../build/x64-software-conventions.md#examples-of-structure-alignment) (spécifique à x64)

Pour plus d'informations sur les différences d'alignement dans le code pour x86 et x64, consultez :

- [Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)