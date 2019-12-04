---
title: Erreur du compilateur C3798
ms.date: 11/04/2016
f1_keywords:
- C3798
helpviewer_keywords:
- C3798
ms.assetid: b2f8b1d8-8812-49b8-a346-28e48f02ba5c
ms.openlocfilehash: cc21f0bdcc8e2171dd0c87fc31396e6caab9e6fc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755315"
---
# <a name="compiler-error-c3798"></a>Erreur du compilateur C3798

'specifier' : la déclaration de propriété ne peut pas avoir de spécificateur de substitution (doit être placé sur les méthodes Property/Set à la place)

Une propriété n’a pas été correctement déclarée. Pour plus d’informations, voir .

- [propriété](../../extensions/property-cpp-component-extensions.md)

- [abstract](../../extensions/abstract-cpp-component-extensions.md)

- [sealed](../../extensions/sealed-cpp-component-extensions.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3798

```cpp
// C3798.cpp
// compile with: /clr /c
ref struct A {
   property int Prop_1 abstract;   // C3798
   property int Prop_2 sealed;   // C3798

   // OK
   property int Prop_3 {
      virtual int get() abstract;
      virtual void set(int i) abstract;
   }

   property int Prop_4 {
      virtual int get() sealed;
      virtual void set(int i) sealed;
   }
};
```
