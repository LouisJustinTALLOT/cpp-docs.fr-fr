---
description: 'En savoir plus sur : classe sequenced_policy'
title: Classe sequenced_policy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: e4d19e3649e3c768e8efc062baaf735e28a8fc22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250411"
---
# <a name="sequenced_policy-class"></a>Classe sequenced_policy

Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et exiger que l’exécution d’un algorithme parallèle ne soit pas parallélisée.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Notes

Lors de l’exécution d’un algorithme parallèle avec la `execution::sequenced_policy` stratégie, si l’appel d’une fonction d’accès à un élément se termine par le biais d’une exception non interceptée, `terminate()` doit être appelé.
