---
title: Erreur du compilateur C2674
ms.date: 11/04/2016
f1_keywords:
- C2674
helpviewer_keywords:
- C2674
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
ms.openlocfilehash: 3a43368a840a3ee8720d85d7dacb7249d9188ab6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760385"
---
# <a name="compiler-error-c2674"></a>Erreur du compilateur C2674

une déclaration générique n’est pas autorisée dans ce contexte

Un générique a été déclaré de manière incorrecte. Pour plus d’informations, consultez la page [Génériques](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2674.

```cpp
// C2674.cpp
// compile with: /clr /c
void F(generic <class T> ref class R1);   // C2674
generic <class T> ref class R2 {};   // OK
```
