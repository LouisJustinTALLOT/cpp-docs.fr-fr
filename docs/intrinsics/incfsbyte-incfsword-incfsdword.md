---
title: __incfsbyte, __incfsword, __incfsdword
ms.date: 09/02/2019
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: 43824829043304f5762d049b5c75a72b57e2102c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222127"
---
# <a name="__incfsbyte-__incfsword-__incfsdword"></a>__incfsbyte, __incfsword, __incfsdword

**Section spécifique à Microsoft**

Ajoutez un à la valeur à un emplacement de mémoire spécifié par un décalage par rapport au début du `FS` segment.

## <a name="syntax"></a>Syntaxe

```C
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Paramètres

*Décalage*\
dans Offset à partir du début de `FS`.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques sont disponibles uniquement en mode noyau et les routines sont uniquement disponibles en tant qu’intrinsèques.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[\__addfsbyte, \__addfsword, \__addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)\
[\__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[\__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
