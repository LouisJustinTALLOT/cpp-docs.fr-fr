---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: f9c8de7c8686b89a2ab9570a2558e3f649e545b5
ms.sourcegitcommit: 0064d37467f958dd6a5111f20d7660eaccd53ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58419083"
---
# <a name="allocator"></a>allocator

**Section spécifique à Microsoft**

Le **allocateur** spécificateur de déclaration peut être appliqué aux fonctions d’allocation de mémoire personnalisé pour afficher les allocations via Event Tracing for Windows (ETW).

## <a name="syntax"></a>Syntaxe

```
   __declspec(allocator) 
```

## <a name="remarks"></a>Notes

Le profileur de mémoire native dans Visual Studio fonctionne en collectant des données d’événement ETW émises pendant l’exécution de répartition. Les allocateurs dans le CRT et le Kit de développement logiciel (SDK) Windows ont été annotés au niveau de la source afin que leurs données d’allocation puissent être capturées. Si vous écrivez vos propres allocateurs, toutes les fonctions qui retournent un pointeur vers la mémoire de tas nouvellement allouée peuvent être décorées avec `__declspec(allocator)`, comme illustré dans cet exemple pour myMalloc :

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

Pour plus d’informations, consultez [mesurer l’utilisation de mémoire dans Visual Studio](/visualstudio/profiling/memory-usage) et [événements de tas ETW natifs personnalisés](/visualstudio/profiling/custom-native-etw-heap-events).