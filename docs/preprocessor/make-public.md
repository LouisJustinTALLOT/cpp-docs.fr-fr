---
title: make_public, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: d12fab685e0088993cb43073c3603bda12edd2f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218817"
---
# <a name="make_public-pragma"></a>make_public, pragma

Indique qu'un type natif doit disposer d'une accessibilité d'assembly public.

## <a name="syntax"></a>Syntaxe

> **#pragma make_public (** *type* **)**

### <a name="parameters"></a>Paramètres

*type*\
Nom du type pour lequel vous souhaitez disposer d’une accessibilité d’assembly public.

## <a name="remarks"></a>Notes

**make_public** est utile lorsque le type natif que vous souhaitez référencer provient d’un fichier d’en-tête que vous ne pouvez pas modifier. Si vous souhaitez utiliser le type natif dans la signature d’une fonction publique dans un type avec une visibilité d’assembly public, le type natif doit également avoir une accessibilité d’assembly public, sinon le compilateur émet un avertissement.

**make_public** doit être spécifié au niveau de la portée globale. Elle est appliquée uniquement à partir du point auquel elle est déclarée jusqu’à la fin du fichier de code source.

Le type natif peut être implicitement ou explicitement privé. Pour plus d’informations, consultez [type Visibility](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).

## <a name="examples"></a>Exemples

L’exemple suivant est le contenu d’un fichier d’en-tête qui contient les définitions de deux structs natifs.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

L’exemple de code suivant utilise le fichier d’en-tête. Il montre que, sauf si vous marquez explicitement les structs natifs comme publics à l’aide de **make_public**, le compilateur génère un avertissement quand vous tentez d’utiliser les structs natifs dans la signature de la fonction publique dans un type managé public.

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

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
