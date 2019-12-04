---
title: Erreur du compilateur C2005
ms.date: 11/04/2016
f1_keywords:
- C2005
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
ms.openlocfilehash: ff998beaa1d954f05a07d8ccf1b59cec0f4e3958
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737476"
---
# <a name="compiler-error-c2005"></a>Erreur du compilateur C2005

\#ligne attendait un numéro de ligne, 'Token’trouvé

La directive `#line` doit être suivie d’un numéro de ligne.

L’exemple suivant génère l’C2005 :

```cpp
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

Solution possible :

```cpp
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```
