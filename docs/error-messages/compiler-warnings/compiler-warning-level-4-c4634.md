---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4634'
title: Avertissement du compilateur (niveau 4) C4634
ms.date: 11/04/2016
f1_keywords:
- C4634
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
ms.openlocfilehash: 87144f1a3c95f46159b07dc776707da06a56ff21
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134125"
---
# <a name="compiler-warning-level-4-c4634"></a>Avertissement du compilateur (niveau 4) C4634

Commentaire de document XML : application impossible : raison

Les balises de documentation XML ne peuvent pas être appliquées à toutes les constructions C++.  Par exemple, vous ne pouvez pas ajouter un commentaire de documentation à un espace de noms ou à un modèle.

Pour plus d’informations, consultez [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md).

## <a name="examples"></a>Exemples

L’exemple suivant génère l’avertissement C4634.

```cpp
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

L’exemple suivant génère l’avertissement C4634.

```cpp
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```
