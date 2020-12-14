---
description: 'En savoir plus sur : erreur du compilateur C3755'
title: Erreur du compilateur C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 24d6af223b6a15cbf1740bf67144250007c2091d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253583"
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
