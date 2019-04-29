---
title: Erreur du compilateur C2094
ms.date: 11/04/2016
f1_keywords:
- C2094
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
ms.openlocfilehash: 072c51ca4ae25c6f51b1841ea129a7b4fb495bdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377096"
---
# <a name="compiler-error-c2094"></a>Erreur du compilateur C2094

Étiquette 'identifier' non définie

L’étiquette utilisée par une instruction [goto](../../cpp/goto-statement-cpp.md) ne se trouve pas dans la fonction.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2094 :

```cpp
// C2094.c
int main() {
   goto test;
}   // C2094
```

Solution possible :

```cpp
// C2094b.c
int main() {
   goto test;
   test:
   {
   }
}
```