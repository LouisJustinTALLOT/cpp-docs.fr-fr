---
title: make_public
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: cfc8d13ead28c0b817d7de015b9c507db152de6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508964"
---
# <a name="makepublic"></a>make_public
Indique qu'un type natif doit disposer d'une accessibilité d'assembly public.

## <a name="syntax"></a>Syntaxe

```
#pragma make_public(type)
```

### <a name="parameters"></a>Paramètres

*type* est le nom du type que vous souhaitez avoir une accessibilité d’assembly public.

## <a name="remarks"></a>Notes

**make_public** est utile lorsque le type natif que vous souhaitez référencer est à partir d’un fichier .h que vous ne pouvez pas modifier. Si vous souhaitez utiliser le type natif dans la signature d'une fonction publique dans un type disposant d'une visibilité d'assembly public, le type natif doit également avoir une accessibilité d'assembly public, sinon le compilateur émet un avertissement.

**make_public** doit être spécifié avec une portée globale et n’est en vigueur à partir du point auquel elle est déclarée à la fin du fichier de code source.

Le type natif peut être implicitement ou explicitement privé ; consultez [visibilité du Type](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) pour plus d’informations.

## <a name="examples"></a>Exemples

L'exemple suivant est le contenu d'un fichier .h qui contient les définitions de deux structures natives.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

L’exemple de code suivant utilise le fichier d’en-tête et montre que, sauf si vous marquez explicitement les structures natives comme publiques, à l’aide de **make_public**, le compilateur génère un avertissement lorsque vous essayez d’utiliser les structures natives dans le signature de fonction publique dans un type managé public.

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)