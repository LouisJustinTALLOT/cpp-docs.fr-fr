---
title: Erreur du compilateur C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: a6d75ca671e22203cb40ca18de21606834eeefa8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188089"
---
# <a name="compiler-error-c2346"></a>Erreur du compilateur C2346

'fonction' ne peut pas être compilée comme code natif : raison

Le compilateur n’a pas pu compiler une fonction en langage MSIL.

Pour plus d’informations, consultez [managed, unmanaged](../../preprocessor/managed-unmanaged.md) et [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Supprimer le code dans la fonction qui ne peuvent pas être compilée en langage MSIL.

1. Ne compilez pas le module avec **/CLR**, ou marquez la fonction comme non gérés avec le pragma non managé.

## <a name="example"></a>Exemple

L’exemple suivant génère C2346.

```
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