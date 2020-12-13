---
description: 'En savoir plus sur : __ud2'
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: 2b5f0b9ffec066baa3eb2fa212dfc7baf3a6cb49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333660"
---
# <a name="__ud2"></a>__ud2

**Spécifique à Microsoft**

Génère une instruction non définie.

## <a name="syntax"></a>Syntaxe

```C
void __ud2();
```

## <a name="remarks"></a>Notes

Le processeur déclenche une exception opcode non valide si vous exécutez une instruction non définie.

La `__ud2` fonction est équivalente à l' `UD2` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez le document « Guide du développeur de logiciels d’architecture Intel, volume 2 : référence de jeu d’instructions » sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__ud2`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="example"></a>Exemple

L’exemple suivant exécute une instruction non définie, qui lève une exception. Le gestionnaire d’exceptions remplace alors le code de retour zéro par un.

```cpp
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
