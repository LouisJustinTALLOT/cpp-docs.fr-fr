---
title: Erreur du compilateur C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d20b8dde9f4134273adcba0f947f685f7ce7d213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447266"
---
# <a name="compiler-error-c2803"></a>Erreur du compilateur C2803

'operator opérateur' doit avoir au moins un paramètre de type de classe

L’opérateur surchargé ne dispose pas d’un paramètre de type de classe.

Vous devez passer au moins un paramètre par référence (sans utiliser de pointeurs, mais des références) ou par valeur pour pouvoir écrire « un < b » (un et b en cours de la classe de type A).

Si les deux paramètres sont des pointeurs, il sera une pure comparaison d’adresses de pointeur et n’utilise pas la conversion définie par l’utilisateur.

L’exemple suivant génère l’erreur C2803 :

```
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```