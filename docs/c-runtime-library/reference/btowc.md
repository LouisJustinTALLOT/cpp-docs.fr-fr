---
title: btowc
ms.date: 4/2/2020
api_name:
- btowc
- _o_btowc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: cbeff70674a257217c66d39475a2c809c9bd9559
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913365"
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

*symbole*<br/>
Entier à tester.

## <a name="return-value"></a>Valeur de retour

Retourne la représentation sous forme de caractères larges du caractère si l’entier représente un caractère sur un octet valide dans l’état de décalage initial. Retourne WEOF si l’entier est EOF ou n’est pas un caractère sur un octet valide dans l’état de décalage initial. La sortie de cette fonction est affectée par les paramètres régionaux actuels **LC_TYPE** .

## <a name="remarks"></a>Notes 

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**btowc**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
