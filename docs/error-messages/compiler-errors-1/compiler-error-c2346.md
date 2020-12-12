---
description: 'En savoir plus sur : erreur du compilateur C2346'
title: Erreur du compilateur C2346
ms.date: 11/04/2016
f1_keywords:
- C2346
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
ms.openlocfilehash: eb2bbda6c7f7e0c9213b35a794b915967d03321f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298368"
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

int main()
{
   S s;
}
```
