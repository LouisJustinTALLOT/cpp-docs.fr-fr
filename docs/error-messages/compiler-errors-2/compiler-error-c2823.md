---
title: Erreur du compilateur C2823
ms.date: 11/04/2016
f1_keywords:
- C2823
helpviewer_keywords:
- C2823
ms.assetid: 982b1b35-1a7c-456e-b711-f80cfe2d571e
ms.openlocfilehash: 5f9b60499fd3c3bd5f06834e3c4f6482031066d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406962"
---
# <a name="compiler-error-c2823"></a>Erreur du compilateur C2823

> un modèle de typedef n’est pas conforme

Modèles ne sont pas autorisés dans `typedef` définitions.

## <a name="example"></a>Exemple

L’exemple suivant génère C2823 et montre une façon de résoudre le problème :

```cpp
// C2823.cpp
template<class T>
typedef struct x {
   T i;   // C2823 can't use T, specify data type and delete template
   int i;   // OK
} x1;
```