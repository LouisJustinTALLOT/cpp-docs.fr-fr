---
title: Avertissement du compilateur (niveau 3) C4580
ms.date: 11/04/2016
f1_keywords:
- C4580
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
ms.openlocfilehash: e215dc98f62a90325e83068a640b0503a612c434
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427805"
---
# <a name="compiler-warning-level-3-c4580"></a>Avertissement du compilateur (niveau 3) C4580

[attribute] est déconseillé ; spécifiez System::Attribute ou Platform::Metadata comme classe de base à la place

[[attribut](../../windows/attributes/attribute.md)] n’est plus la syntaxe par défaut pour la création d’attributs définis par l’utilisateur. Pour plus d'informations, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md). Pour le code CLR, dérivez les attributs à partir de `System::Attribute`. Pour le code Windows Runtime, dérivez les attributs à partir de `Platform::Metadata`.

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