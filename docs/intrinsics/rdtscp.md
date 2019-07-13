---
title: __rdtscp
ms.date: 07/11/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: b8a31c6d19cd171cbe909c75a27c2389866bd578
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861108"
---
# <a name="rdtscp"></a>__rdtscp

**Section spécifique à Microsoft**

Génère le `rdtscp` écrit des instructions, `TSC_AUX[31:0`] à la mémoire et retourne le compteur d’horodatage 64 bits (`TSC)` résultat.

## <a name="syntax"></a>Syntaxe

```
unsigned __int64 __rdtscp(
   unsigned int * Aux
);
```

#### <a name="parameters"></a>Paramètres

*Aux*<br/>
[out] Pointeur vers un emplacement qui contiendra le contenu du Registre spécifiques à l’ordinateur `TSC_AUX[31:0]`.

## <a name="return-value"></a>Valeur de retour

Un nombre de cycles d’entier non signé 64 bits.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__rdtscp`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Cet intrinsèque génère le `rdtscp` instruction. Pour déterminer la prise en charge matérielle pour cette instruction, appelez le `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 27 de `CPUInfo[3] (EDX)`. Ce bit est 1 si l’instruction est pris en charge et 0 dans le cas contraire.  Si vous exécutez le code qui utilise cet intrinsèque sur du matériel qui ne prend pas en charge la `rdtscp` instruction, les résultats sont imprévisibles.

Cette instruction attend jusqu'à ce que toutes les instructions précédentes ont exécutées et tous les chargements précédentes sont visibles dans le monde entier. Toutefois, il n’est pas une instruction de sérialisation. Consultez les manuels d’Intel et AMD pour plus d’informations.

La signification de la valeur dans `TSC_AUX[31:0]` dépend du système d’exploitation.

## <a name="example"></a>Exemple

```cpp
#include <intrin.h>
#include <stdio.h>
int main()
{
    unsigned __int64 i;
    unsigned int ui;
    i = __rdtscp(&ui);
    printf_s("%I64d ticks\n", i);
    printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**FIN de la section spécifique à Microsoft**


## <a name="see-also"></a>Voir aussi

[__rdtsc](../intrinsics/rdtsc.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)