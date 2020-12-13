---
description: 'En savoir plus sur : vsscanf_s, vswscanf_s'
title: vsscanf_s, vswscanf_s
ms.date: 11/04/2016
api_name:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: 3be22d5ea1399c426159bcd006e89585128cee55
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342099"
---
# <a name="vsscanf_s-vswscanf_s"></a>vsscanf_s, vswscanf_s

Lit les données mises en forme d’une chaîne. Ces versions de [vsscanf, vswscanf](vsscanf-vswscanf.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vsscanf_s(
   const char *buffer,
   const char *format,
   va_list argptr
);
int vswscanf_s(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Données stockées

*format*<br/>
Chaîne de contrôle de format. Pour plus d’informations, consultez [Champs de spécification de format : fonctions scanf et wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Liste d’arguments de variable.

## <a name="return-value"></a>Valeur renvoyée

Chacune de ces fonctions retourne le nombre de champs correctement convertis et assignés. La valeur de retour n’inclut pas les champs qui ont été lus, mais pas assignés. La valeur de retour 0 indique qu'aucun champ n'a été assigné. La valeur de retour est **EOF** pour une erreur ou si la fin de la chaîne est atteinte avant la première conversion.

Si la *mémoire tampon* ou le *format* est un pointeur **null** , le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **vsscanf_s** lit les données de la *mémoire tampon* dans les emplacements fournis par chaque argument dans la liste d’arguments *arglist* . Les arguments de la liste d’arguments spécifient des pointeurs vers des variables dont le type correspond à un spécificateur de type au *format*. Contrairement à la version moins sécurisée **vsscanf**, un paramètre de taille de mémoire tampon est requis lorsque vous utilisez les jeux de champs de type **c**, **c**, **s**, **s** ou String-Control qui sont placés dans **[]**. La taille de mémoire tampon des caractères doit être fournie comme paramètre supplémentaire de suite après chaque paramètre de mémoire tampon qui le nécessite.

La taille de la mémoire tampon inclut le caractère Null de fin. Un champ de spécification de largeur peut être utilisé pour faire en sorte que le jeton lu tiendra dans la mémoire tampon. Si aucun champ de spécification de largeur n'est utilisé, et si le jeton lu est trop grand pour la mémoire tampon, aucune valeur n'est écrite dans cette mémoire tampon.

Pour plus d’informations, consultez [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) et [Caractères du champ de type scanf](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Le paramètre de taille est de type **`unsigned`** , et non **size_t**.

L’argument *format* contrôle l’interprétation des champs d’entrée et a les mêmes forme et fonction que l’argument *format* pour la fonction **scanf_s** . Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

**vswscanf_s** est une version à caractères larges de **vsscanf_s**; les arguments de **vswscanf_s** sont des chaînes à caractères larges. **vsscanf_s** ne gère pas les caractères hexadécimaux multioctets. **vswscanf_s** ne gère pas les caractères hexadécimaux ou « zone de compatibilité » Unicode à pleine chasse. Dans le cas contraire, **vswscanf_s** et **vsscanf_s** se comportent de la même façon.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_vsscanf_s.c
// compile with: /W3
// This program uses vsscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vsscanf_s(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf_s(tokenstring, format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    char  tokenstring[] = "15 12 14...";
    char  s[81];
    char  c;
    int   i;
    float fp;

    // Input various data from tokenstring:
    // max 80 character string:
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));
    call_vsscanf_s(tokenstring, "%d", &i);
    call_vsscanf_s(tokenstring, "%f", &fp);

    // Output the data read
    printf("String    = %s\n", s);
    printf("Character = %c\n", c);
    printf("Integer:  = %d\n", i);
    printf("Real:     = %f\n", fp);
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf, vswscanf](vsscanf-vswscanf.md)<br/>
