---
title: Erreur du compilateur C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: fc2aeac02ecc3f29406c2288051ca6cd9d3a4923
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760008"
---
# <a name="compiler-error-c2346"></a>Erreur du compilateur C2346

'Function’ne peut pas être compilé comme Native : Reason

Le compilateur n’a pas pu compiler une fonction en MSIL.

Pour plus d’informations, consultez [managé, non managé](../../preprocessor/managed-unmanaged.md) et [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Supprimez le code de la fonction qui ne peut pas être compilé en MSIL.

1. Ne compilez pas le module avec **/CLR**, ou marquez la fonction comme non managée avec le pragma non managé.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2346.

```cpp
// C2346.cpp
// processor: x86
// compile with: /clr
// C2346 expected
struct S
{
   S()
   {
      { __asm { nop } }
   }
   virtual __clrcall ~S() { }
};

void main()
{
   S s;
}
```
