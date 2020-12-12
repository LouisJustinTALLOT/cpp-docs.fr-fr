---
description: 'En savoir plus sur : __movsq'
title: __movsq
ms.date: 09/02/2019
f1_keywords:
- __movsq
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
ms.openlocfilehash: 5bd212e5ebd1b98a853fb782d7e45c1e7e001f44
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133157"
---
# <a name="__movsq"></a>__movsq

**Spécifique à Microsoft**

Génère une instruction Move String ( `rep movsq` ) répétée.

## <a name="syntax"></a>Syntaxe

```C
void __movsq(
   unsigned char* Destination,
   unsigned char* Source,
   size_t Count
);
```

### <a name="parameters"></a>Paramètres

*Destination*\
à Destination de l’opération.

*Code*\
dans Source de l’opération.

*Saut*\
dans Nombre de mots quadruples à copier.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__movsq`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Le résultat est que le premier *nombre* d’mots quadruples pointé vers la *source* est copié dans la chaîne de *destination* .

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```cpp
// movsq.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsq)

int main()
{
    unsigned __int64 a1[10];
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,
                               150, 50};
    __movsq(a1, a2, 10);

    for (int i = 0; i < 10; i++)
       printf_s("%d ", a1[i]);
    printf_s("\n");
}
```

```Output
950 850 750 650 550 450 350 250 150 50
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
