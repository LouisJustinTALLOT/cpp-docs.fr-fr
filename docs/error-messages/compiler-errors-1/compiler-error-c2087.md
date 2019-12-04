---
title: Erreur du compilateur C2087
ms.date: 11/04/2016
f1_keywords:
- C2087
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
ms.openlocfilehash: 576ac394585b91f7c6ceadcdd07d25c639854990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757902"
---
# <a name="compiler-error-c2087"></a>Erreur du compilateur C2087

'identificateur' : indice manquant

Une valeur d’indice est manquante pour la définition d’un tableau avec plusieurs indices pour une dimension supérieure à un.

L’exemple suivant génère l’C2087 :

```cpp
// C2087.cpp
int main() {
   char a[10][];   // C2087
}
```

Solution possible :

```cpp
// C2087b.cpp
int main() {
   char b[4][5];
}
```
