---
title: Erreur du compilateur C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: 2e0122dd53ba5318077dd33f22a07492c52db26b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756212"
---
# <a name="compiler-error-c3451"></a>Erreur du compilateur C3451

'Attribute' : impossible d’appliquer l’attribut non managé à’type'

Un C++ attribut ne peut pas être appliqué à un type CLR. Pour plus d’informations, consultez [ C++ référence des attributs](../../windows/attributes/attributes-alphabetical-reference.md) .

Pour plus d'informations, consultez [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Cette erreur peut être générée en raison du travail de mise en conformité du compilateur pour Visual Studio 2005 : l’attribut [UUID](../../windows/uuid-cpp-attributes.md) n’est plus autorisé sur un attribut défini par l’utilisateur à l’aide de la programmation CLR. Utilisez plutôt <xref:System.Runtime.InteropServices.GuidAttribute>.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3451.

```cpp
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
