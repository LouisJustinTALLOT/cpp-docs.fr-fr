---
title: Erreur du compilateur C2803 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7885735ebad1ff90afaf4ba8eaf6dfca9f3e0ab3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46027035"
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