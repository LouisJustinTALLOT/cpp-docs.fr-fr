---
title: Avertissement du compilateur (niveau 4) C4634
ms.date: 11/04/2016
f1_keywords:
- C4634
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
ms.openlocfilehash: 0a84773f80e15b4e6d3851de768751d1d6dc4b4e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990603"
---
# <a name="compiler-warning-level-4-c4634"></a>Avertissement du compilateur (niveau 4) C4634

Commentaire de document XML : application impossible : raison

Les balises de documentation XML ne peuvent pas être appliquées à toutes les constructions C++.  Par exemple, vous ne pouvez pas ajouter un commentaire de documentation à un espace de noms ou à un modèle.

Pour plus d’informations, consultez [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4634.

```cpp
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4634.

```cpp
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```
