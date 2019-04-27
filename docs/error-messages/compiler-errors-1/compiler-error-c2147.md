---
title: Erreur du compilateur C2147
ms.date: 11/04/2016
f1_keywords:
- C2147
helpviewer_keywords:
- C2147
ms.assetid: d1adb3bf-7ece-4815-922c-ad7492fb6670
ms.openlocfilehash: 0a093bbbaf9cf9f72625226f949a27b681005c35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175392"
---
# <a name="compiler-error-c2147"></a>Erreur du compilateur C2147

Erreur de syntaxe : 'identifier' est un nouveau mot clé

Un identificateur a été utilisé qui est désormais un mot clé réservé dans le langage.

L’exemple suivant génère l’erreur C2147 :

```
// C2147.cpp
// compile with: /clr
int main() {
   int gcnew = 0;   // C2147
   int i = 0;   // OK
}
```