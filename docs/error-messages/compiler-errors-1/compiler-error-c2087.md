---
description: 'En savoir plus sur : erreur du compilateur C2087'
title: Erreur du compilateur C2087
ms.date: 11/04/2016
f1_keywords:
- C2087
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
ms.openlocfilehash: 98e54a8df8f06230f1adca1cb6d2f23f80acff8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252036"
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
