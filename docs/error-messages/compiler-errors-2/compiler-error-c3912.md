---
title: Erreur du compilateur C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: bd66196c35715304577b8f6785261be8bdcdafec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775854"
---
# <a name="compiler-error-c3912"></a>Erreur du compilateur C3912

'event' : type d’événement doit être un type délégué

Un événement a été déclaré mais n’était pas du type approprié.

Pour plus d’informations, consultez [événement](../../extensions/event-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3912 :

```
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```