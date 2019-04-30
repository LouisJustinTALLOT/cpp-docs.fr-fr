---
title: Erreur mathématique M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 44f406881d64d13e23ca2c0911ee278c864a2c11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393406"
---
# <a name="math-error-m6111"></a>Erreur mathématique M6111

dépassement de capacité négatif de pile

Une opération à virgule flottante a provoqué un dépassement de précision de pile sur l’émulateur ou le coprocesseur 8087/287/387.

Cette erreur est souvent due à un appel à une `long double` fonction qui ne retourne pas de valeur. Par exemple, ce qui suit génère cette erreur lorsque compilé et exécuté :

```
long double ld() {};
main ()
{
  ld();
}
```

Programme se termine par le code de sortie 139.