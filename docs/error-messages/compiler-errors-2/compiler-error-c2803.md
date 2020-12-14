---
description: 'En savoir plus sur : erreur du compilateur C2803'
title: Erreur du compilateur C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: 405c14d05bad4c505d847b8ab2648a7ace3b9a4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297432"
---
# <a name="compiler-error-c2803"></a>Erreur du compilateur C2803

'operator opérateur’doit avoir au moins un paramètre formel de type classe

L’opérateur surchargé n’a pas de paramètre de type classe.

Vous devez passer au moins un paramètre par référence (à l’exception des pointeurs, mais des références) ou par valeur pour pouvoir écrire « a < b » (a et b étant de type classe A).

Si les deux paramètres sont des pointeurs, il s’agit d’une comparaison pure des adresses de pointeur et n’utilise pas la conversion définie par l’utilisateur.

L’exemple suivant génère l’C2803 :

```cpp
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```
