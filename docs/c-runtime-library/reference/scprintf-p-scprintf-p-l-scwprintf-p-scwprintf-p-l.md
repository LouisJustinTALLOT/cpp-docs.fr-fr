---
description: 'En savoir plus sur les éléments suivants : _scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l'
title: _scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l
ms.date: 11/04/2016
api_name:
- _scwprintf_p
- _scprintf_p_l
- _scwprintf_p_l
- _scprintf_p
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _scwprintf_p_l
- _sctprintf_p
- scprintf_p_l
- scprintf_p
- _sctprintf_p_l
- scwprintf_p
- _scprintf_p_l
- scwprintf_p_l
- _scprintf_p
- _scwprintf_p
helpviewer_keywords:
- sctprintf_p_l function
- _scwprintf_p_l function
- scprintf_p_l function
- _scprintf_p function
- _scprintf_p_l function
- scprintf_p function
- sctprintf_p function
- _scwprintf_p function
- _sctprintf_p function
- scwprintf_p function
- scwprintf_p_l function
- _sctprintf_p_l function
ms.assetid: 8390d1e1-2826-47a4-851f-6635a88087cc
ms.openlocfilehash: f3f4fa9ffd1a54756fa3dfb274ebeb3e49f0544c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288995"
---
# <a name="_scprintf_p-_scprintf_p_l-_scwprintf_p-_scwprintf_p_l"></a>_scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l

Retourne le nombre de caractères contenus dans la chaîne mise en forme, avec la possibilité de spécifier l’ordre dans lequel les arguments sont utilisés dans la chaîne de format.

## <a name="syntax"></a>Syntaxe

```C
int _scprintf_p(
   const char *format [,
   argument] ...
);
int _scprintf_p_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _scwprintf_p (
   const wchar_t *format [,
   argument] ...
);
int _scwprintf_p _l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Paramètres

*format*<br/>
Chaîne de contrôle de format.

*argument*<br/>
Arguments facultatifs.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de caractères qui seraient générés si la chaîne devait était imprimée ou envoyée vers un fichier ou une mémoire tampon en utilisant les codes de mise en forme spécifiés. La valeur retournée n’inclut pas le caractère Null de fin. **_scwprintf_p** effectue la même fonction pour les caractères larges.

La différence entre **_scprintf_p** et **_scprintf** est que **_scprintf_p** prend en charge les paramètres positionnels, ce qui permet de spécifier l’ordre dans lequel les arguments sont utilisés dans la chaîne de format. Pour plus d’informations, consultez [Paramètres positionnels printf_p](../../c-runtime-library/printf-p-positional-parameters.md).

Si *format* est un pointeur **null** , le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chaque *argument* (le cas échéant) est converti selon la spécification de format correspondante au *format*. Le format se compose de caractères ordinaires et a la même forme et fonction que l’argument *format* pour [printf](printf-printf-l-wprintf-wprintf-l.md).

Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sctprintf_p**|**_scprintf_p**|**_scprintf_p**|**_scwprintf_p**|
|**_sctprintf_p_l**|**_scprintf_p_l**|**_scprintf_p_l**|**_scwprintf_p_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_scprintf_p**, **_scprintf_p_l**|\<stdio.h>|
|**_scwprintf_p**, **_scwprintf_p_l**|\<stdio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_scprintf, _scprintf_l, _scwprintf, _scwprintf_l](scprintf-scprintf-l-scwprintf-scwprintf-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
