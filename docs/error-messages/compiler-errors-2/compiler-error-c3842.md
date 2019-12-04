---
title: Erreur du compilateur C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: 881165a1100d1c8791ecd5f50eda6a2e9f1650eb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754912"
---
# <a name="compiler-error-c3842"></a>Erreur du compilateur C3842

'fonction' : les qualificateurs 'const' et 'volatile' ne sont pas pris en charge pour les fonctions membres des types WinRT ou managés

[const](../../cpp/const-cpp.md) et [volatile](../../cpp/volatile-cpp.md) ne sont pas prises en charge sur les fonctions membres de Windows Runtime ou de types managés.

L'exemple suivant génère l'erreur C3842 :

```cpp
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```
