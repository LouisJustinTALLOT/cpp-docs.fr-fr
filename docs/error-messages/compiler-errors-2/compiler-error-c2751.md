---
title: Erreur du compilateur C2751
ms.date: 11/04/2016
f1_keywords:
- C2751
helpviewer_keywords:
- C2751
ms.assetid: 44a3abdf-8a87-4a09-b34b-532c220c310a
ms.openlocfilehash: 14f458725564d39851ae16b5fd2cd5a79f00420d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360194"
---
# <a name="compiler-error-c2751"></a>Erreur du compilateur C2751

'paramètre' : le nom d’un paramètre de fonction ne peut pas être qualifié.

Vous ne pouvez pas utiliser un nom qualifié comme paramètre de fonction.

L’exemple suivant génère l’erreur C2751 :

```
// C2751.cpp
namespace std {
   template<typename T>
   class list {};
}

#define list std::list
void f(int &list){}   // C2751
```