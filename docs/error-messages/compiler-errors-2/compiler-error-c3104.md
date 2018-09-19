---
title: Erreur du compilateur C3104 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3104
dev_langs:
- C++
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db9bce4d47658b012824087f62eb55ccd7ddf669
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111145"
---
# <a name="compiler-error-c3104"></a>Erreur du compilateur C3104

argument d’attribut non conforme

Vous avez spécifié un argument non valide pour un attribut.

Consultez [Types de paramètre d’attribut](../../windows/attribute-parameter-types-cpp-component-extensions.md) pour plus d’informations.

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
