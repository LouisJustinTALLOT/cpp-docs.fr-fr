---
title: Erreur du compilateur C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: cc4e5423dc8fc53a8f749e2392ff23658a0cb0f1
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685113"
---
# <a name="compiler-error-c3755"></a>Erreur du compilateur C3755

'Delegate' : un délégué ne peut pas être défini

Un [délégué (extensions du composant C++)](../../extensions/delegate-cpp-component-extensions.md) peut être déclaré mais pas défini.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C3755.

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

C3755 peut également se produire si vous tentez de créer un modèle de délégué. L’exemple suivant génère l’C3755.

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
