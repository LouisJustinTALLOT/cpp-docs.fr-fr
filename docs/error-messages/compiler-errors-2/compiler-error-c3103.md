---
description: 'En savoir plus sur : erreur du compilateur C3103'
title: Erreur du compilateur C3103
ms.date: 11/04/2016
f1_keywords:
- C3103
helpviewer_keywords:
- C3103
ms.assetid: 7984bd3e-d51d-43e4-b6f4-08c1e9fb9704
ms.openlocfilehash: a1cd6b2116e277b21eec291633ccb8b84196a615
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116117"
---
# <a name="compiler-error-c3103"></a>Erreur du compilateur C3103

'argument' : argument nommé répété

Un attribut ne peut pas répéter des arguments nommés.

Pour plus d'informations, consultez [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3103.

```cpp
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
