---
title: Erreur du compilateur C2474 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2474
dev_langs:
- C++
helpviewer_keywords:
- C2474
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd33c74a0f5fe179b0dfdd5754d15f24bf0026ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092568"
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