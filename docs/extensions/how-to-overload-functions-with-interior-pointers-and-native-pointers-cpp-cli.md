---
description: 'En savoir plus sur : Comment : surcharger des fonctions avec des pointeurs intérieurs et des pointeurs natifs (C++/CLI)'
title: 'Comment : surcharger des fonctions avec des pointeurs intérieurs et des pointeurs natifs (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
ms.openlocfilehash: f68861b7140ed3ae7fac84bc9a197f68ddd9b72d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119146"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>Comment : surcharger des fonctions avec des pointeurs intérieurs et des pointeurs natifs (C++/CLI)

Les fonctions peuvent être surchargées selon que le type de paramètre est un pointeur intérieur ou un pointeur natif.

> [!IMPORTANT]
> Cette fonctionnalité de langage est prise en charge par l’option du compilateur `/clr`, mais pas par l’option du compilateur `/ZW`.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```cpp
// interior_ptr_overload.cpp
// compile with: /clr
using namespace System;

// C++ class
struct S {
   int i;
};

// managed class
ref struct G {
   int i;
};

// can update unmanaged storage
void f( int* pi ) {
   *pi = 10;
   Console::WriteLine("in f( int* pi )");
}

// can update managed storage
void f( interior_ptr<int> pi ) {
   *pi = 10;
   Console::WriteLine("in f( interior_ptr<int> pi )");
}

int main() {
   S *pS = new S;   // C++ heap
   G ^pG = gcnew G;   // common language runtime heap
   f( &pS->i );
   f( &pG->i );
};
```

```Output
in f( int* pi )
in f( interior_ptr<int> pi )
```

## <a name="see-also"></a>Voir aussi

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)
