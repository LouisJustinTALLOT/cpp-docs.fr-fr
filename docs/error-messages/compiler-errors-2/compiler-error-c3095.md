---
description: 'En savoir plus sur : erreur du compilateur C3095'
title: Erreur du compilateur C3095
ms.date: 11/04/2016
f1_keywords:
- C3095
helpviewer_keywords:
- C3095
ms.assetid: cde725be-0936-40f6-9e57-e1d7d0710f83
ms.openlocfilehash: 9dab36b01b60ee1c78731c4bb12f22a249e094b6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116325"
---
# <a name="compiler-error-c3095"></a>Erreur du compilateur C3095

'attribute' : impossible de répéter l’attribut

Certains attributs sont déclarés de sorte que plusieurs occurrences d’eux mêmes ne peuvent pas être appliquées à une cible.

Pour plus d'informations, consultez [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3095.

```cpp
// C3095.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All, AllowMultiple=false)]
public ref class Attr : public Attribute {
public:
   Attr(int t) : m_t(t) {}
   const int m_t;
};

[AttributeUsage(AttributeTargets::All, AllowMultiple=true)]
public ref class Attr2 : public Attribute {
public:
   Attr2(int t) : m_t(t) {}
   const int m_t;
};

[Attr(10)]   // C3095
[Attr(11)]
ref class A {};

[Attr2(10)]   // OK
[Attr2(11)]
ref class B {};
```
