---
title: Erreur du compilateur C3451
ms.date: 11/04/2016
f1_keywords:
- C3451
helpviewer_keywords:
- C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
ms.openlocfilehash: d6a0d1234d8f25c6a55fffa7170f37aae27f5817
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501323"
---
# <a name="compiler-error-c3451"></a>Erreur du compilateur C3451

'Attribute' : impossible d’appliquer l’attribut non managé à’type'

Un attribut C++ ne peut pas être appliqué à un type CLR. Pour plus d’informations, consultez informations de référence sur les [attributs C++](../../windows/attributes/attributes-alphabetical-reference.md) .

Pour plus d'informations, consultez [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

Cette erreur peut être générée en raison du travail de mise en conformité du compilateur pour Visual Studio 2005 : l’attribut [UUID](../../windows/attributes/uuid-cpp-attributes.md) n’est plus autorisé sur un attribut défini par l’utilisateur à l’aide de la programmation CLR. Utilisez <xref:System.Runtime.InteropServices.GuidAttribute> à la place.

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
