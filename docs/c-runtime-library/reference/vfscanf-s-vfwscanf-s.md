---
description: 'En savoir plus sur : vfscanf_s, vfwscanf_s'
title: vfscanf_s, vfwscanf_s
ms.date: 11/04/2016
api_name:
- vfscanf_s
- vfwscanf_s
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
- vfscanf_s
- vfwscanf_s
- _vftscanf_s
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
ms.openlocfilehash: 99d822ef2425c44f4339c1102eda9924f46f54c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268884"
---
# <a name="vfscanf_s-vfwscanf_s"></a>vfscanf_s, vfwscanf_s

Lit les données mises en forme d’un flux. Ces versions de vfscanf, vfwscanf intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vfscanf_s(
   FILE *stream,
   const char *format,
   va_list arglist
);
int vfwscanf_s(
   FILE *stream,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Paramètres

*train*<br/>
Pointeur désignant la structure **FILE**.

*format*<br/>
Chaîne de contrôle de format.

*arglist*<br/>
Liste d’arguments de variable.

## <a name="return-value"></a>Valeur renvoyée

Chacune de ces fonctions retourne le nombre de champs correctement convertis et assignés. La valeur de retour n’inclut pas les champs qui ont été lus, mais pas assignés. La valeur de retour 0 indique qu'aucun champ n'a été assigné. Si une erreur se produit ou si la fin du flux de fichier est atteinte avant la première conversion, la valeur de retour est **EOF** pour **vfscanf_s** et **vfwscanf_s**.

Ces fonctions valident leurs paramètres. Si *Stream* est un pointeur de fichier non valide ou que le *format* est un pointeur null, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EOF** et attribuent à **errno** la valeur **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **vfscanf_s** lit les données à partir de la position actuelle du *flux* dans les emplacements fournis par la liste d’arguments *arglist* (le cas échéant). Chaque argument de la liste doit être un pointeur vers une variable d’un type qui correspond à un spécificateur de type au *format*. le *format* contrôle l’interprétation des champs d’entrée et a les mêmes forme et fonction que l’argument *format* pour **scanf_s**; consultez [champs de spécification de format : fonctions scanf et wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md) pour obtenir une description du *format*. **vfwscanf_s** est une version à caractères larges de **vfscanf_s**; l’argument de format de **vfwscanf_s** est une chaîne de caractères larges. Ces fonctions se comportent de la même façon si le flux est ouvert en mode ANSI. **vfscanf_s** ne prend pas actuellement en charge l’entrée d’un flux Unicode.

La principale différence entre les fonctions les plus sécurisées (qui ont le suffixe **_s** ) et les autres versions est que les fonctions plus sécurisées requièrent que la taille en caractères de chaque champ **c**, **c**, **s**, **s** et **[** type soit passée comme argument immédiatement après la variable. Pour plus d’informations, consultez [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) et [Spécification de largeur scanf](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Le paramètre de taille est de type **`unsigned`** , et non **size_t**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf_s**|**vfscanf_s**|**vfscanf_s**|**vfwscanf_s**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**vfscanf_s**|\<stdio.h>|
|**vfwscanf_s**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_vfscanf_s.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses vfscanf_s to
// read the various data back from the file.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

FILE *stream;

int call_vfscanf_s(FILE * istream, char * format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vfscanf_s(istream, format, arglist);
    va_end(arglist);
    return result;
}

int main(void)
{
    long l;
    float fp;
    char s[81];
    char c;

    if (fopen_s(&stream, "vfscanf_s.out", "w+") != 0)
    {
        printf("The file vfscanf_s.out was not opened\n");
    }
    else
    {
        fprintf(stream, "%s %ld %f%c", "a-string",
            65000, 3.14159, 'x');
        // Security caution!
        // Beware loading data from a file without confirming its size,
        // as it may lead to a buffer overrun situation.

        // Set pointer to beginning of file:
        fseek(stream, 0L, SEEK_SET);

        // Read data back from file:
        call_vfscanf_s(stream, "%s %ld %f%c", s, _countof(s), &l, &fp, &c, 1);

        // Output data read:
        printf("%s\n", s);
        printf("%ld\n", l);
        printf("%f\n", fp);
        printf("%c\n", c);

        fclose(stream);
    }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)<br/>
[fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[vfscanf, vfwscanf](vfscanf-vfwscanf.md)<br/>
