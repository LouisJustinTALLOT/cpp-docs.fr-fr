---
description: 'En savoir plus sur : erreur du compilateur C2181'
title: Erreur du compilateur C2181
ms.date: 11/04/2016
f1_keywords:
- C2181
helpviewer_keywords:
- C2181
ms.assetid: d52b2fe4-566a-40a9-b8e2-8dce1f287668
ms.openlocfilehash: f251575d22c27ca7b0e2339a987f42303546a721
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335192"
---
# <a name="compiler-error-c2181"></a>Erreur du compilateur C2181

instruction else sans if correspondant non conforme

Chaque **`else`** doit avoir un correspondant **`if`** .

L’exemple suivant génère l’erreur C2181 :

```cpp
// C2181.cpp
int main() {
   int i = 0;
   else   // C2181
      i = 1;
}
```

Solution possible :

```cpp
// C2181b.cpp
int main() {
   int i = 0;
   if(i)
      i = 0;
   else
      i = 1;
}
```
