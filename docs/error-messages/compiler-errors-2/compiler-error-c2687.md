---
title: Erreur du compilateur C2687
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: f3e728033a3230d628242aab341377be2f6670ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760255"
---
# <a name="compiler-error-c2687"></a>Erreur du compilateur C2687

'type' : la déclaration d’exception ne peut pas être’void’ou désigner un type incomplet ou un pointeur ou une référence à un type incomplet

Pour qu’un type fasse partie d’une déclaration d’exception, il doit être défini et non void.

L’exemple suivant génère l’C2687 :

```cpp
// C2687.cpp
class C;

int main() {
   try {}
   catch (C) {}   // C2687 error
}
```

Solution possible :

```cpp
// C2687b.cpp
// compile with: /EHsc
class C {};

int main() {
   try {}
   catch (C) {}
}
```
