---
title: Erreur du compilateur C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 84b21f20cbc8203a9cd70e487738c34c6ad3a89b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598925"
---
# <a name="compiler-error-c3908"></a>Erreur du compilateur C3908

niveau d’accès moins restrictif que 'construct'

Une méthode d’accesseur de propriété (get ou set) ne peut pas avoir d’accès moins restrictif que l’accès spécifié sur la propriété proprement dite.  De même, pour les méthodes d’accesseur événement.

Pour plus d’informations, consultez [propriété](../../windows/property-cpp-component-extensions.md) et [événement](../../windows/event-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3908 :

```
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```