---
title: Erreur mathématique M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: e8abedf6a326a826d0c8ac513b15037c8bf89bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173689"
---
# <a name="math-error-m6111"></a>Erreur mathématique M6111

dépassement de capacité négatif de la pile

Une opération à virgule flottante a entraîné un dépassement de capacité négatif de la pile sur le coprocesseur 8087/287/387 ou l’émulateur.

Cette erreur est souvent due à un appel à une fonction `long double` qui ne retourne pas de valeur. Par exemple, le code suivant génère cette erreur lors de la compilation et de l’exécution :

```
long double ld() {};
main ()
{
  ld();
}
```

Le programme se termine avec le code de sortie 139.
