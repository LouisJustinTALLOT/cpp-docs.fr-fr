---
description: 'En savoir plus sur : erreur du compilateur C2687'
title: Erreur du compilateur C2687
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: 38996f2f31998ef96dd848915686adb1bf46c987
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220758"
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
