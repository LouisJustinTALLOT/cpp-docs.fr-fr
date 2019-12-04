---
title: Erreur du compilateur C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 0150693ae84b45dc62c11cfdc59369eb25a819cd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757278"
---
# <a name="compiler-error-c3755"></a>Erreur du compilateur C3755

'Delegate' : un délégué ne peut pas être défini

Un [délégué (C++ extensions de composant)](../../extensions/delegate-cpp-component-extensions.md) peut être déclaré mais pas défini.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3755.

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Exemple

C3755 peut également se produire si vous tentez de créer un modèle de délégué. L’exemple suivant génère l’C3755.

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
