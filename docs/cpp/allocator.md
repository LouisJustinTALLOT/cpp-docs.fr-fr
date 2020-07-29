---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: a26cf4d2b79d64ddc9f0b60982d778e33d0f200a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216646"
---
# `allocator`

**Spécifique à Microsoft**

Le **`allocator`** spécificateur de déclaration peut être appliqué aux fonctions d’allocation de mémoire personnalisées pour rendre les allocations visibles via suivi d’v nements pour Windows (ETW).

## <a name="syntax"></a>Syntaxe

> **`__declspec(allocator)`**

## <a name="remarks"></a>Notes

Le profileur de mémoire native dans Visual Studio fonctionne en collectant des données d’événement ETW d’allocation émises par pendant l’exécution. Les allocateurs dans le CRT et le Kit de développement logiciel (SDK) Windows ont été annotés au niveau de la source afin que leurs données d’allocation puissent être capturées. Si vous écrivez vos propres allocateurs, toutes les fonctions qui retournent un pointeur vers la mémoire du tas nouvellement allouée peuvent être décorées avec `__declspec(allocator)` , comme illustré dans cet exemple pour myMalloc :

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Pour plus d’informations, consultez [mesurer l’utilisation de la mémoire dans Visual Studio](/visualstudio/profiling/memory-usage) et les [événements de tas ETW natifs personnalisés](/visualstudio/profiling/custom-native-etw-heap-events).

**FIN spécifique à Microsoft**
