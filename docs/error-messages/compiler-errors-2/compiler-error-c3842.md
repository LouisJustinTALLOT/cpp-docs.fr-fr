---
description: 'En savoir plus sur : erreur du compilateur C3842'
title: Erreur du compilateur C3842
ms.date: 11/04/2016
f1_keywords:
- C3842
helpviewer_keywords:
- C3842
ms.assetid: 41a1a44a-c618-40a2-8d26-7da27d14095d
ms.openlocfilehash: dd5cff7b4a381ca976138720d8af192d594c7836
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255416"
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
