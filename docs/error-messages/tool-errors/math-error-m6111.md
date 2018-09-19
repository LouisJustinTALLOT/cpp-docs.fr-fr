---
title: Erreur mathématique M6111 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a55ec6b7cdf0b6e4c15bd283dde77c610698fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074823"
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