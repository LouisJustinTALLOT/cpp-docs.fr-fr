---
description: 'En savoir plus sur : erreur du compilateur C3908'
title: Erreur du compilateur C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 67258f9f5946d180af9a270b931f88f263238856
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144168"
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
