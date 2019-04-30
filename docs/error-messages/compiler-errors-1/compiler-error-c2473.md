---
title: Erreur du compilateur C2473
ms.date: 11/04/2016
f1_keywords:
- C2473
helpviewer_keywords:
- C2473
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
ms.openlocfilehash: 232f89a714d70c6914b73a370c5f658ff4283ab4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345631"
---
# <a name="compiler-error-c2473"></a>Erreur du compilateur C2473

'identifier' : similaire à une définition de fonction, mais aucune liste de paramètres n’existe.

Le compilateur a détecté un élément qui ressemble à une fonction, sans liste de paramètres.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2473.

```
// C2473.cpp
// compile with: /clr /c
class A {
   int i {}   // C2473
};

class B {
   int i() {}   // OK
};
```