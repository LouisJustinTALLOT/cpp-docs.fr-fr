---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4580'
title: Avertissement du compilateur (niveau 3) C4580
ms.date: 11/04/2016
f1_keywords:
- C4580
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
ms.openlocfilehash: 0bda682526081023c9208d548023f7c8b7316db9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294715"
---
# <a name="compiler-warning-level-3-c4580"></a>Avertissement du compilateur (niveau 3) C4580

[attribute] est déconseillé ; spécifiez System::Attribute ou Platform::Metadata comme classe de base à la place

[[attribute](../../windows/attributes/attribute.md)] n’est plus la syntaxe préférée pour la création d’attributs définis par l’utilisateur. Pour plus d'informations, consultez [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md). Pour le code CLR, dérivez les attributs à partir de `System::Attribute`. Pour le code Windows Runtime, dérivez les attributs à partir de `Platform::Metadata`.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C3454 et montre comment la corriger.

```cpp
// C4580.cpp
// compile with: /W3 /c /clr
[attribute]   // C4580
public ref class Attr {
public:
   int m_t;
};

public ref class Attr2 : System::Attribute {
public:
   int m_t;
};
```
