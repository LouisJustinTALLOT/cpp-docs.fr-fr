---
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: b5aa20804099af4d75dcc62a5e62ccc0d4a09566
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219758"
---
# <a name="__ud2"></a>__ud2

**Section spécifique à Microsoft**

Génère une instruction non définie.

## <a name="syntax"></a>Syntaxe

```C
void __ud2();
```

## <a name="remarks"></a>Notes

Le processeur déclenche une exception opcode non valide si vous exécutez une instruction non définie.

La `__ud2` fonction est équivalente à `UD2` l’instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez le document «Guide du développeur de logiciels d’architecture Intel, volume 2: Référence du jeu d’instructions, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__ud2`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

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
