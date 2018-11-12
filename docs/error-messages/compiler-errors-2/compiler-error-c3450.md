---
title: Erreur du compilateur C3450
ms.date: 11/04/2016
f1_keywords:
- C3450
helpviewer_keywords:
- C3450
ms.assetid: 78892cf7-0b82-4589-90d0-e06666247003
ms.openlocfilehash: bedf78ef1cea9f17903fd05f9440c6baa69f7333
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481235"
---
# <a name="compiler-error-c3450"></a>Erreur du compilateur C3450

'type' : n'est pas un attribut ; impossible de spécifier [System::AttributeUsageAttribute] ou [Windows::Foundation::Metadata::AttributeUsageAttribute]

Un attribut managé défini par l’utilisateur doit hériter de <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>. Un attribut Windows Runtime doit être défini dans l'espace de noms `Windows::Foundation::Metadata`.

Pour plus d'informations, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3450 et montre comment la corriger.

```
// C3450.cpp
// compile with: /clr
// C3450 expected
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref struct AtClass {
   AtClass(Type ^) {}
};

[attribute(AttributeTargets::All)]
ref struct AtClass2 {
   AtClass2() {}
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
// Delete the following line to resolve.
ref class B {};
// Uncomment the following line to resolve.
// ref class B : Attribute {};
```