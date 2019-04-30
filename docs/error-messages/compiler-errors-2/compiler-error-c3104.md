---
title: Erreur du compilateur C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: 3b2737bd67798fd467649be175d581ca551e1331
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404167"
---
# <a name="compiler-error-c3104"></a>Erreur du compilateur C3104

argument d’attribut non conforme

Vous avez spécifié un argument non valide pour un attribut.

Consultez [Types de paramètre d’attribut](../../extensions/attribute-parameter-types-cpp-component-extensions.md) pour plus d’informations.

Cette erreur peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : lors du passage de tableaux managés à des attributs personnalisés, le type du tableau n’est plus déduit à partir de la liste d’initialisation d’agrégats. Le compilateur requiert désormais vous permettent de spécifier le type de tableau ainsi que la liste d’initialiseurs.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3104.

```
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3104.

```
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
