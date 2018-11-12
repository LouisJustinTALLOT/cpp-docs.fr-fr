---
title: Erreur du compilateur C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 041c0c22b7ae842073bfd6656d9cbb3b2a20af9c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430054"
---
# <a name="compiler-error-c3451"></a>Erreur du compilateur C3451

'attribute' : Impossible d’appliquer l’attribut non managé à 'type'

Un attribut C++ ne peut pas être appliqué à un type CLR. Consultez [référence des attributs C++](../../windows/cpp-attributes-reference.md) pour plus d’informations.

Pour plus d'informations, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).

Cette erreur peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : le [uuid](../../windows/uuid-cpp-attributes.md) attribut n’est plus autorisé sur un attribut défini par l’utilisateur à l’aide de la programmation CLR. Utilisez plutôt <xref:System.Runtime.InteropServices.GuidAttribute>.

## <a name="example"></a>Exemple

L’exemple suivant génère C3451.

```
// C3451.cpp
// compile with: /clr /c
using namespace System;
[ attribute(AttributeTargets::All) ]
public ref struct MyAttr {};

[ MyAttr, helpstring("test") ]   // C3451
// try the following line instead
// [ MyAttr ]
public ref struct ABC {};
```