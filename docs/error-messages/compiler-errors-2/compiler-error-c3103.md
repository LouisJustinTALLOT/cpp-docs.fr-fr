---
title: Erreur du compilateur C3103
ms.date: 11/04/2016
f1_keywords:
- C3103
helpviewer_keywords:
- C3103
ms.assetid: 7984bd3e-d51d-43e4-b6f4-08c1e9fb9704
ms.openlocfilehash: 8dae731e36177dc199554615f74e92ebc5f6f5dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531942"
---
# <a name="compiler-error-c3103"></a>Erreur du compilateur C3103

'argument' : argument nommé répété

Un attribut ne peut pas répéter les arguments nommés.

Pour plus d'informations, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3103.

```
// C3103.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref class Attr : public Attribute {
public:
   int m_t;
};

[Attr(m_t = 10, m_t = 1)]   // C3103
// try the following line instead
// [Attr(m_t = 10)]
ref class A {};
```