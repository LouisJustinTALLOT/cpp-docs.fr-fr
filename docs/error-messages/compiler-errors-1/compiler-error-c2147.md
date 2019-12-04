---
title: Erreur du compilateur C2147
ms.date: 11/04/2016
f1_keywords:
- C2147
helpviewer_keywords:
- C2147
ms.assetid: d1adb3bf-7ece-4815-922c-ad7492fb6670
ms.openlocfilehash: 0af88d89ff264ca9efd02477a62e5bd7532271bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756485"
---
# <a name="compiler-error-c2147"></a>Erreur du compilateur C2147

erreur de syntaxe : 'identifier’est un nouveau mot clé

Un identificateur utilisé est maintenant un mot clé réservé dans le langage.

L’exemple suivant génère l’C2147 :

```cpp
// C2147.cpp
// compile with: /clr
int main() {
   int gcnew = 0;   // C2147
   int i = 0;   // OK
}
```
