---
description: 'En savoir plus sur : opérateur alignof'
title: Opérateur alignof
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
ms.openlocfilehash: b7e053b932ed631d8b03dc1b89f6857905740e5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288300"
---
# <a name="alignof-operator"></a>Opérateur alignof

L' **`alignof`** opérateur retourne l’alignement, en octets, du type spécifié en tant que valeur de type **`size_t`** .

## <a name="syntax"></a>Syntaxe

```cpp
alignof( type )
```

## <a name="remarks"></a>Notes

Par exemple :

| Expression | Valeur |
|--|--|
| **`alignof( char )`** | 1 |
| **`alignof( short )`** | 2 |
| **`alignof( int )`** | 4 |
| **`alignof( long long )`** | 8 |
| **`alignof( float )`** | 4 |
| **`alignof( double )`** | 8 |

La **`alignof`** valeur est la même que pour pour les **`sizeof`** types de base. Observons toutefois l'exemple suivant :

```cpp
typedef struct { int a; double b; } S;
// alignof(S) == 8
```

Dans ce cas, la **`alignof`** valeur est l’exigence d’alignement du plus grand élément de la structure.

De même, pour

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`alignof(S)` est égal à `32`.

Une utilisation de **`alignof`** est en tant que paramètre pour l’une de vos propres routines d’allocation de mémoire. Par exemple, dans la structure définie `S`suivante, vous pouvez appeler une routine d'allocation de mémoire nommée `aligned_malloc` pour allouer la mémoire sur une limite d'alignement particulière.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), alignof(S));
```

Pour plus d'informations sur la modification de l'alignement, consultez :

- [pack](../preprocessor/pack.md)

- [droite](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/ZP (alignement des membres de la structure)](../build/reference/zp-struct-member-alignment.md)

- [Exemples d’alignement de structure](../build/x64-software-conventions.md#examples-of-structure-alignment) (spécifique à x64)

Pour plus d'informations sur les différences d'alignement dans le code pour x86 et x64, consultez :

- [Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

### <a name="microsoft-specific"></a>Spécifique à Microsoft

**`alignof`** et **`__alignof`** sont des synonymes dans le compilateur Microsoft. Avant de devenir partie intégrante de la norme C++ 11, l’opérateur spécifique à Microsoft **`__alignof`** fournissait cette fonctionnalité. Pour une portabilité maximale, vous devez utiliser l' **`alignof`** opérateur au lieu de l’opérateur spécifique à Microsoft **`__alignof`** .

Pour la compatibilité avec les versions précédentes, **`_alignof`** est un synonyme de, **`__alignof`** sauf si l’option de compilateur [ `/Za` \( désactive les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)
