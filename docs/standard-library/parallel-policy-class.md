---
description: 'En savoir plus sur : classe parallel_policy'
title: Classe parallel_policy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 1cead0bcc44256bf7d41d061d592849a7411b057
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340799"
---
# <a name="parallel_policy-class"></a>Classe parallel_policy

Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et indiquer que l’exécution d’un algorithme parallèle peut être parallélisée.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::parallel_policy;
```

## <a name="remarks"></a>Notes

Lors de l’exécution d’un algorithme parallèle avec la `execution::parallel_policy` stratégie, si l’appel d’une fonction d’accès à un élément se termine par le biais d’une exception non interceptée, `terminate()` doit être appelé.
