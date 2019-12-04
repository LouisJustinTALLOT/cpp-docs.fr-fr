---
title: Erreur du compilateur C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: e4952f4702d871ecf1c818b1fc7394e54a1a295f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743885"
---
# <a name="compiler-error-c2464"></a>Erreur du compilateur C2464

'identificateur' : impossible d’utiliser’New’pour allouer une référence

Un identificateur de référence a été alloué avec l’opérateur `new`. Les références ne sont pas des objets mémoire, donc `new` ne peut pas retourner un pointeur vers ces objets. Utilisez la syntaxe de déclaration de variable standard pour déclarer une référence.

L’exemple suivant génère l’C2464 :

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
