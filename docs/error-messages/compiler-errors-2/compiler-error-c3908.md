---
title: Erreur du compilateur C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 2b57f3346427ff548d11fe776e909eca99433a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749033"
---
# <a name="compiler-error-c3908"></a>Erreur du compilateur C3908

niveau d’accès moins restrictif que « Construct »

Une méthode d’accesseur de propriété (Get ou Set) ne peut pas avoir un accès moins restrictif que l’accès spécifié sur la propriété elle-même.  De même, pour les méthodes d’accesseur d’événement.

Pour plus d’informations, consultez [propriété](../../extensions/property-cpp-component-extensions.md) et [événement](../../extensions/event-cpp-component-extensions.md).

L’exemple suivant génère l’C3908 :

```cpp
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
