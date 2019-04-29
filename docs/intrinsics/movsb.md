---
title: __movsb
ms.date: 11/04/2016
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: 42124743c27b297c723780c1bc19038fb54e638d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62263813"
---
# <a name="movsb"></a>__movsb

**Section spécifique à Microsoft**

Génère une chaîne de déplacer (`rep movsb`) instruction.

## <a name="syntax"></a>Syntaxe

```
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

#### <a name="parameters"></a>Paramètres

*Destination*<br/>
[out] Pointeur vers la destination de la copie.

*Source*<br/>
[in] Pointeur vers la source de la copie.

*Nombre*<br/>
[in] Le nombre d’octets à copier.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__movsb`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Le résultat est que la première `Count` octets vers lequel pointe `Source` sont copiés vers le `Destination` chaîne.

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="example"></a>Exemple

```
// movsb.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsb)

int main()
{
    unsigned char s1[100];
    unsigned char s2[100] = "A big black dog.";
    __movsb(s1, s2, 100);

    printf_s("%s %s", s1, s2);
}
```

```Output
A big black dog. A big black dog.
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)