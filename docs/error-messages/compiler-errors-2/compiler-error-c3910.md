---
title: Erreur du compilateur C3910 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3910
dev_langs:
- C++
helpviewer_keywords:
- C3910
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc5a719cac97a16ef6b8eaff277a9526a2f135ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073835"
---
# <a name="compiler-error-c3910"></a>Erreur du compilateur C3910

'event' : doit définir 'méthode' membre

Un événement a été défini, mais il ne contenait pas la méthode d’accesseur spécifiée requise.

Pour plus d’informations, consultez [événement](../../windows/event-cpp-component-extensions.md).

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