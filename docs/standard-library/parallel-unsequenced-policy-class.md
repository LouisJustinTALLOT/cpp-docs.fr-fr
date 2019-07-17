---
title: parallel_unsequenced_policy, classe
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_unsequenced_policy
ms.openlocfilehash: 92b4e3ce3743fdd3d5ba112a333b2306829b95d4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268781"
---
# <a name="parallelunsequencedpolicy-class"></a>parallel_unsequenced_policy, classe

Utilisé comme un type unique pour lever l’ambiguïté de surcharge de l’algorithme parallèle et d’indiquer que l’exécution d’un algorithme parallèle peut être parallélisée et vectorisée.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::parallel_unsequenced_policy;
```

## <a name="remarks"></a>Notes

Pendant l’exécution d’un algorithme parallèle avec le `execution::parallel_unsequenced_policy` stratégie, si l’appel d’une fonction d’accès élément se termine par une exception non interceptée, `terminate()` doit être appelée.
