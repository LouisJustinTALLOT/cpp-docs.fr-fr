---
title: c16rtomb, c32rtomb
ms.date: 01/22/2018
api_name:
- c16rtomb
- c32rtomb
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
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: a16effe48442ccbb5144b57ead2fb15c908fe898
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943426"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

Convertir un caractère large UTF-16 ou UTF-32 en caractère multioctet dans les paramètres régionaux actuels.

## <a name="syntax"></a>Syntaxe

```C
size_t c16rtomb(
    char *mbchar,
    char16_t wchar,
    mbstate_t *state
);
size_t c32rtomb(
    char *mbchar,
    char32_t wchar,
    mbstate_t *state
);
```

### <a name="parameters"></a>Paramètres

*mbchar*<br/>
Pointeur vers un tableau pour stocker le caractère multioctet converti.

*wchar*<br/>
Caractère large à convertir.

*state*<br/>
Pointeur vers un objet **mbstate_t** .

## <a name="return-value"></a>Valeur de retour

Nombre d’octets stockés dans le tableau d’objets *mbchar*, y compris les séquences de décalage. Si *WCHAR* n’est pas un caractère élargi valide, la valeur (**size_t**) (-1) est retournée, **errno** a la valeur **EILSEQ**et la valeur de *State* n’est pas spécifiée.

## <a name="remarks"></a>Notes

La fonction **c16rtomb** convertit le caractère UTF-16 *WCHAR* en séquence de caractères étroits multioctets équivalente dans les paramètres régionaux actuels. Si *mbchar* n’est pas un pointeur null, la fonction stocke la séquence convertie dans l’objet tableau pointé par *mbchar*. Jusqu’à **MB_CUR_MAX** octets sont stockés dans *mbchar* *, et l’État est* défini sur l’état de décalage multioctet résultant.    Si *WCHAR* est un caractère élargi null, une séquence nécessaire pour restaurer l’état de décalage initial est stockée, si nécessaire, suivie du caractère null, *et l’État est* défini sur l’état de conversion initial. La fonction **c32rtomb** est identique, mais convertit un caractère UTF-32.

Si *mbchar* est un pointeur null, le comportement est équivalent à un appel à la fonction qui substitue une mémoire tampon interne pour *mbchar* et un caractère null étendu pour *WCHAR*.

L’objet d’état de conversion d' *État* vous permet d’effectuer des appels ultérieurs à cette fonction et à d’autres fonctions redémarrables qui maintiennent l’état de décalage des caractères multioctets de sortie. Les résultats ne sont pas définis lorsque vous combinez l’utilisation de fonctions redémarrables et non redémarrables, ou si un appel à **setlocale** est effectué entre des appels de fonctions redémarrables.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++ : \<uchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
