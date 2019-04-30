---
title: Avertissement du compilateur (niveau 3) C4641
ms.date: 11/04/2016
f1_keywords:
- C4641
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
ms.openlocfilehash: 9357088106a45026eae543f8627ea59988e73995
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401668"
---
# <a name="compiler-warning-level-3-c4641"></a>Avertissement du compilateur (niveau 3) C4641

Le commentaire de document XML comporte une référence croisée ambiguë

Le compilateur n’a pas pu résoudre clairement une référence. Pour résoudre cet avertissement, spécifiez les informations de paramètre nécessaires pour rendre la référence non équivoque.

Pour plus d’informations, consultez [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4641.

```
// C4641.cpp
// compile with: /W3 /doc /clr /c

/// <see cref="f" />   // C4641
// try the following line instead
// /// <see cref="f(int)" />
public ref class GR {
public:
   void f( int ) {}
   void f( char ) {}
};
```