---
title: 'Comment : surcharger des fonctions avec des pointeurs intérieurs et des pointeurs natifs (C++ / c++ / CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6df6f84e8cb407fe960f639fd2cb9415df6d1082
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071912"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>Comment : surcharger des fonctions avec des pointeurs intérieurs et des pointeurs natifs (C++/CLI)

Fonctions peuvent être surchargées selon que le type de paramètre est un pointeur intérieur ou un pointeur natif.

> [!IMPORTANT]
> Cette fonctionnalité de langage est pris en charge par le `/clr` option du compilateur, mais pas par le `/ZW` option du compilateur.

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

[interior_ptr (C++-CLI)](../windows/interior-ptr-cpp-cli.md)