---
title: __addfsbyte, __addfsword, __addfsdword
ms.date: 09/02/2019
f1_keywords:
- __addfsbyte_cpp
- __addfsdword
- __addfsword_cpp
- __addfsbyte
- __addfsword
- __addfsdword_cpp
helpviewer_keywords:
- __addfsdword intrinsic
- __addfsword intrinsic
- __addfsbyte intrinsic
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
ms.openlocfilehash: 302e58ed13c144913e7806a0a8b7adc202a67ef6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218522"
---
# <a name="__addfsbyte-__addfsword-__addfsdword"></a>__addfsbyte, __addfsword, __addfsdword

**Section spécifique à Microsoft**

Ajoute une valeur à un emplacement de mémoire spécifié par un décalage par rapport au début du `FS` segment.

## <a name="syntax"></a>Syntaxe

```C
void __addfsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __addfsword(
   unsigned long Offset,
   unsigned short Data
);
void __addfsdword(
   unsigned long Offset,
   unsigned long Data
);
```

### <a name="parameters"></a>Paramètres

*Décalage*\
dans Offset à partir du début de `FS`.

*Métadonnée*\
dans Valeur à ajouter à l’emplacement de mémoire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__addfsbyte`|x86|
|`__addfsword`|x86|
|`__addfsdword`|x86|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement comme intrinsèques.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__incfsbyte, \__incfsword, \__incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)\
[__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
