---
description: 'En savoir plus sur : erreur mathématique mathématique M6111'
title: Erreur mathématique M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 9bf2d620a0df18752b74aaacd4d2415510407f0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244340"
---
# <a name="math-error-m6111"></a>Erreur mathématique M6111

dépassement de capacité négatif de la pile

Une opération à virgule flottante a entraîné un dépassement de capacité négatif de la pile sur le coprocesseur 8087/287/387 ou l’émulateur.

Cette erreur est souvent due à un appel à une **`long double`** fonction qui ne retourne pas de valeur. Par exemple, le code suivant génère cette erreur lors de la compilation et de l’exécution :

```
long double ld() {};
main ()
{
  ld();
}
```

Le programme se termine avec le code de sortie 139.
