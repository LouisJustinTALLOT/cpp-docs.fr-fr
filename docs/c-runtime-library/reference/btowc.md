---
title: btowc
ms.date: 11/04/2016
apiname:
- btowc
apilocation:
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
apitype: DLLExport
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: 399f56fe133a9f67ed457b435ae6c0496e1ecaa5
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740000"
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
