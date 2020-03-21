---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 39708e8cfff7f61c3a3f763f87e1a3da36f0d4b1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077258"
---
# <a name="allocator"></a>allocator

**Section spécifique de Microsoft**

Le spécificateur de déclaration d' **Allocator** peut être appliqué aux fonctions d’allocation de mémoire personnalisées pour rendre les allocations visibles via suivi d’V nements pour Windows (ETW).

## <a name="syntax"></a>Syntaxe

```
   __declspec(allocator)
```

## <a name="remarks"></a>Notes

Le profileur de mémoire native dans Visual Studio fonctionne en collectant des données d’événement ETW d’allocation émises par pendant l’exécution. Les allocateurs dans le CRT et le Kit de développement logiciel (SDK) Windows ont été annotés au niveau de la source afin que leurs données d’allocation puissent être capturées. Si vous écrivez vos propres allocateurs, toutes les fonctions qui retournent un pointeur vers la mémoire du tas nouvellement allouée peuvent être décorées avec `__declspec(allocator)`, comme illustré dans cet exemple pour myMalloc :

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Pour plus d’informations, consultez [mesurer l’utilisation de la mémoire dans Visual Studio](/visualstudio/profiling/memory-usage) et les [événements de tas ETW natifs personnalisés](/visualstudio/profiling/custom-native-etw-heap-events).

**Fin de la section spécifique de Microsoft**
