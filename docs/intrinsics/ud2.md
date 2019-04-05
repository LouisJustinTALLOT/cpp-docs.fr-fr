---
title: __ud2
ms.date: 11/04/2016
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: a36ab5c25ac9138b2a4d6810cc2a339e534f1695
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029406"
---
# <a name="ud2"></a>__ud2

**Section spécifique à Microsoft**

Génère une instruction non définie.

## <a name="syntax"></a>Syntaxe

```
void __ud2();
```

## <a name="remarks"></a>Notes

Le processeur génère une exception de l’opcode non valide si vous exécutez une instruction non définie.

Le `__ud2` fonction est équivalente à la `UD2` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez dans le document, « manuel du développeur de logiciels Architecture Intel, Volume 2 : Instruction Set Reference, » à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__ud2`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="example"></a>Exemple

L’exemple suivant exécute une instruction non définie, qui lève une exception. Le Gestionnaire d’exceptions modifie ensuite le code de retour de zéro à un.

```
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

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)