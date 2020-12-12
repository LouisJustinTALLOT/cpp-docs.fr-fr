---
description: 'En savoir plus sur : __rdtscp'
title: __rdtscp
ms.date: 09/02/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 511d0f1001c218fd838d4bb315fe8c95f10eb3bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257487"
---
# <a name="__rdtscp"></a>__rdtscp

**Spécifique à Microsoft**

Génère l' `rdtscp` instruction, écrit `TSC_AUX[31:0` ] dans la mémoire et retourne le compteur d’horodatage 64 bits ( `TSC)` résultat.

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __rdtscp(
   unsigned int * AUX
);
```

### <a name="parameters"></a>Paramètres

*Coord*\
à Pointeur vers un emplacement qui contiendra le contenu du Registre spécifique à l’ordinateur `TSC_AUX[31:0]` .

## <a name="return-value"></a>Valeur retournée

Nombre de cycles d’entier non signé 64 bits.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__rdtscp`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L' `__rdtscp` intrinsèque génère l' `rdtscp` instruction. Pour déterminer la prise en charge matérielle pour cette instruction, appelez l' `__cpuid` intrinsèque avec `InfoType=0x80000001` et vérifiez le bit 27 de `CPUInfo[3] (EDX)` . Ce bit est égal à 1 si l’instruction est prise en charge et 0 dans le cas contraire.  Si vous exécutez du code qui utilise l’intrinsèque sur du matériel qui ne prend pas en charge l' `rdtscp` instruction, les résultats sont imprévisibles.

Cette instruction attend que toutes les instructions précédentes aient été exécutées et que toutes les chargements précédents soient globalement visibles. Toutefois, il ne s’agit pas d’une instruction de sérialisation. Pour plus d’informations, consultez les manuels Intel et AMD.

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__rdtsc](../intrinsics/rdtsc.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
