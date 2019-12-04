---
title: Erreur du compilateur C2861
ms.date: 11/04/2016
f1_keywords:
- C2861
helpviewer_keywords:
- C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
ms.openlocfilehash: 3d6cab186d4acf229a32620f33c9c86e807459dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751987"
---
# <a name="compiler-error-c2861"></a>Erreur du compilateur C2861

'Function name' : une fonction membre d’interface ne peut pas être définie

Le compilateur a rencontré le mot clé interface ou a déduit un struct en tant qu’interface, mais une définition de fonction membre a été trouvée.  Une interface ne peut pas contenir une définition pour une fonction membre.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2861 :

```cpp
// C2861.cpp
// compile with: /c
#include <objbase.h>   // required for IUnknown definition
[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IMyInterface : IUnknown {
   HRESULT mf(int a);
};

HRESULT IMyInterface::mf(int a) {}   // C2861
```
