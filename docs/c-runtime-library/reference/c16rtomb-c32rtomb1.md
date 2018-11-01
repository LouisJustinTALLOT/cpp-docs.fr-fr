---
title: c16rtomb, c32rtomb1
ms.date: 11/04/2016
apiname:
- c16rtomb
- c32rtomb
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
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: 0d735363bbb317b06c1ebc73a2b0678479a243ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536589"
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
Un pointeur vers un **mbstate_t** objet.

## <a name="return-value"></a>Valeur de retour

Le nombre d’octets stockés dans un objet tableau *mbchar*, y compris les séquences de décalage. Si *wchar* n’est pas un caractère large valid, la valeur (**size_t**)(-1) est retourné, **errno** a la valeur **EILSEQ**et la valeur de *état* n’est pas spécifié.

## <a name="remarks"></a>Notes

Le **c16rtomb** fonction convertit le caractère UTF-16 *wchar* à la séquence de caractères étroits multioctets équivalente dans les paramètres régionaux actuels. Si *mbchar* n’est pas un pointeur null, la fonction stocke la séquence convertie dans l’objet tableau vers lequel pointe *mbchar*. Jusqu'à **MB_CUR_MAX** octets sont stockés dans *mbchar*, et *état* est défini sur l’état du décalage multioctet qui en résulte.    Si *wchar* est un caractère large null, une séquence nécessaire pour restaurer l’état de décalage initial est stocké, si nécessaire, suivi par le caractère null, et *état* est défini sur l’état de conversion initial. Le **c32rtomb** fonction est identique, mais convertit un caractère UTF-32.

Si *mbchar* est un pointeur null, le comportement équivaut à un appel à la fonction qui substitue un tampon interne pour *mbchar* et un caractère null large pour *wchar*.

Le *état* objet d’état de conversion vous permet de faire des appels ultérieurs à cette fonction et d’autres fonctions redémarrables qui maintiennent l’état du décalage de caractères multioctets de sortie. Résultats ne sont pas définis lorsque vous combinez l’utilisation de fonctions redémarrables et non redémarrables, ou si un appel à **setlocale** est faite entre les appels de fonctions redémarrables.

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
