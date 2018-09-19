---
title: Erreur du compilateur C2346 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2346
dev_langs:
- C++
helpviewer_keywords:
- C2346
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec916bcdce1a43c597d8cfae10e5393cbeb99ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108610"
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