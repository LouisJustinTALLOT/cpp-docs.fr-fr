---
title: Erreur du compilateur C2474
ms.date: 11/04/2016
f1_keywords:
- C2474
helpviewer_keywords:
- C2474
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
ms.openlocfilehash: c49f38b828a41c72135ba9182d4d0f5eee4df1de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475307"
---
# <a name="compiler-error-c2474"></a>Erreur du compilateur C2474

'keyword' : point-virgule adjacent manquant ; il peut s’agir d’un mot clé ou d’un identificateur.

Le compilateur attendait un point-virgule et n’a pas pu identifier ce que vous souhaitiez faire. Ajoutez le point-virgule pour résoudre cette erreur.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2474.

```
// C2474.cpp
// compile with: /clr /c

ref class A {
   ref class B {}
   property int i;   // C2474 error
};

// OK
ref class B {
   ref class D {};
   property int i;
};

ref class E {
   ref class F {} property;
   int i;
};
```