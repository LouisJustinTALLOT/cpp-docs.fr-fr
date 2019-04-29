---
title: Erreur du compilateur C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: a61a69aca53f7f8996d0261a57b749930ecc01cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385509"
---
# <a name="compiler-error-c3842"></a>Erreur du compilateur C3842

'fonction' : les qualificateurs 'const' et 'volatile' ne sont pas pris en charge pour les fonctions membres des types WinRT ou managés

[const](../../cpp/const-cpp.md) et [volatile](../../cpp/volatile-cpp.md) ne sont pas pris en charge sur les fonctions membres de Windows Runtime ou des types managés.

L'exemple suivant génère l'erreur C3842 :

```
// C3842a.cpp
// compile with: /clr /c
public ref struct A {
   void f() const {}   // C3842
   void f() volatile {}   // C3842

   void f() {}
};
```