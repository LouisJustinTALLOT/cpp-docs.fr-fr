---
title: btowc
ms.date: 11/04/2016
api_name:
- btowc
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: 1f03fce8686f919af85ee3751cb9a0a3fca1ede7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943467"
---
# <a name="btowc"></a>btowc

Déterminer si un entier représente un caractère sur un octet valide dans l’état de décalage initial.

## <a name="syntax"></a>Syntaxe

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Paramètres

*character*<br/>
Entier à tester.

## <a name="return-value"></a>Valeur de retour

Retourne la représentation sous forme de caractères larges du caractère si l’entier représente un caractère sur un octet valide dans l’état de décalage initial. Retourne WEOF si l’entier est EOF ou n’est pas un caractère sur un octet valide dans l’état de décalage initial. La sortie de cette fonction est affectée par les paramètres régionaux **LC_TYPE** actuels.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**btowc**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
