---
title: Erreur du compilateur C3919
ms.date: 11/04/2016
f1_keywords:
- C3919
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
ms.openlocfilehash: 05ac2fc9258a078f352b6012e64e86fe4b70c3f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386575"
---
# <a name="compiler-error-c3919"></a>Erreur du compilateur C3919

'méthode_événement' : fonction doit avoir le type 'type'

Une méthode d’accesseur événement n’a pas été correctement déclarée.

Pour plus d’informations sur les événements, consultez [événement](../../extensions/event-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3919 :

```
// C3919.cpp
// compile with: /clr /c
using namespace System;
delegate void D(String^);
ref class R {
   event D^ e {
      int add(int);   // C3919
      int remove(int);   // C3919

      void add(D^);   // OK
      void remove(D^);   // OK
   }
};
```