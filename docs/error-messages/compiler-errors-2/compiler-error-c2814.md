---
title: Erreur du compilateur C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 5cc22afa29160ce50d658a4a8d4b2a56e5145527
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750856"
---
# <a name="compiler-error-c2814"></a>Erreur du compilateur C2814

'membre' : un type natif ne peut pas être imbriqué dans un type managé ou WinRT 'type'

## <a name="example"></a>Exemple

Un type natif ne peut pas être imbriqué dans un type CLR ou WinRT. L'exemple suivant génère l'erreur C2814 et montre comment la corriger.

```cpp
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
