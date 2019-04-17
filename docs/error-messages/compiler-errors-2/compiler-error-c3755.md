---
title: Erreur du compilateur C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 5d1260138bfdbc318817c336077eef326b62f8b8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767429"
---
# <a name="compiler-error-c3755"></a>Erreur du compilateur C3755

'délégué' : un délégué ne peut pas être défini.

Un [delegate (Extensions du composant C++)](../../extensions/delegate-cpp-component-extensions.md) peut être déclaré mais pas défini.

## <a name="example"></a>Exemple

L’exemple suivant génère C3755.

```
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Exemple

C3755 peut également se produire si vous essayez de créer un modèle de délégué. L’exemple suivant génère C3755.

```
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```