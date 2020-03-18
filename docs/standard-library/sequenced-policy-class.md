---
title: Classe sequenced_policy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: 5647f20b560828016231a9bbd38977c51211e6bb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444913"
---
# <a name="sequenced_policy-class"></a>Classe sequenced_policy

Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et exiger que l’exécution d’un algorithme parallèle ne soit pas parallélisée.

## <a name="syntax"></a>Syntaxe

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Notes

Pendant l’exécution d’un algorithme parallèle avec la stratégie de `execution::sequenced_policy`, si l’appel d’une fonction d’accès à un élément se termine par le biais d’une exception non interceptée, `terminate()` doit être appelé.
