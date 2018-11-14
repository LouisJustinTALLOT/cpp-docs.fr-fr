---
title: _putch, _putwch
ms.date: 11/04/2016
apiname:
- _putwch
- _putch
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
- api-ms-win-crt-conio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _putch
- putwch
- _putwch
helpviewer_keywords:
- _putch function
- characters, writing
- putwch function
- _putwch function
- putch function
- console, writing characters to
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
ms.openlocfilehash: da45744fe56c198cc97228cae8043abbb5436fbd
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326990"
---
# <a name="putch-putwch"></a>_putch, _putwch

Écrit un caractère dans la console.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _putch(
   int c
);

wint_t _putwch(
   wchar_t c
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à sortir.

## <a name="return-value"></a>Valeur de retour

Retourne *c* en cas de réussite. Si **_putch** échoue, elle retourne **EOF**; si **_putwch** échoue, elle retourne **WEOF**.

## <a name="remarks"></a>Notes

Ces fonctions écrivent le caractère *c* directement, sans mise en mémoire tampon, à la console. Dans Windows NT, **_putwch** écrit des caractères Unicode en utilisant les paramètres régionaux actifs de la console.

Les versions avec suffixe **_nolock** sont identiques, à ceci près qu’elles ne sont pas protégées contre les interférences avec d’autres threads. Pour plus d’informations, consultez **_putch_nolock**, **_putwch_nolock**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttch**|**_putch**|**_putch**|**_putwch**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_putch**|\<conio.h>|
|**_putwch**|\<conio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_getch](getch-getwch.md).

## <a name="see-also"></a>Voir aussi

[E/S de console et de port](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
