---
title: Erreur du compilateur C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: b2d2766b11d15bdb666baa207591cc9ff279a280
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225473"
---
# <a name="compiler-error-c2464"></a>Erreur du compilateur C2464

'identificateur' : impossible d’utiliser’New’pour allouer une référence

Un identificateur de référence a été alloué avec l' **`new`** opérateur. Les références ne sont pas des objets de mémoire **`new`** . par conséquent, ne peut pas retourner un pointeur vers ces objets. Utilisez la syntaxe de déclaration de variable standard pour déclarer une référence.

L’exemple suivant génère l’C2464 :

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
