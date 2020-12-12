---
description: 'En savoir plus sur : erreur du compilateur C2094'
title: Erreur du compilateur C2094
ms.date: 11/04/2016
f1_keywords:
- C2094
helpviewer_keywords:
- C2094
ms.assetid: 9e4f8f88-f189-46e7-91c9-481bacc7af87
ms.openlocfilehash: 35f67da3259b93eb4ef280d45c8e364df07e9889
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251828"
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
