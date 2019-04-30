---
title: Erreur du compilateur C3910
ms.date: 11/04/2016
f1_keywords:
- C3910
helpviewer_keywords:
- C3910
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
ms.openlocfilehash: 186cd67d77e9aafbfe6a7d9dc18afb2bdbd94f0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406624"
---
# <a name="compiler-error-c3910"></a>Erreur du compilateur C3910

'event' : doit définir 'méthode' membre

Un événement a été défini, mais il ne contenait pas la méthode d’accesseur spécifiée requise.

Pour plus d’informations, consultez [événement](../../extensions/event-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3910 :

```
// C3910.cpp
// compile with: /clr /c
delegate void H();
ref class X {
   event H^ E {
      // uncomment the following lines
      // void add(H^) {}
      // void remove( H^ h ) {}
      // void raise( ) {}
   };   // C3910

   event H^ E2; // OK data member
};
```