---
title: parallel_policy, classe
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 7bb2b095a50e664dfc585e0bd4aaa608a6ad8e95
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268961"
---
# <a name="parallelpolicy-class"></a>parallel_policy, classe

Utilisé comme un type unique pour lever l’ambiguïté de surcharge de l’algorithme parallèle et d’indiquer que l’exécution d’un algorithme parallèle peut être parallélisée.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::parallel_policy;
```

## <a name="remarks"></a>Notes

Pendant l’exécution d’un algorithme parallèle avec le `execution::parallel_policy` stratégie, si l’appel d’une fonction d’accès élément se termine par une exception non interceptée, `terminate()` doit être appelée.
