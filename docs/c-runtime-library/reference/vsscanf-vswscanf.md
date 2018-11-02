---
title: vsscanf, vswscanf
ms.date: 11/04/2016
apiname:
- vsscanf
- vswscanf
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
apitype: DLLExport
f1_keywords:
- _vstscanf
- vsscanf
- vswscanf
helpviewer_keywords:
- vswscanf function
- vsscanf function
ms.assetid: e96180f2-df46-423d-b4eb-0a49ab819bde
ms.openlocfilehash: 5bbe80cd2463c5c5b9b4ea55b8d6574675e42054
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478581"
---
# <a name="vsscanf-vswscanf"></a>vsscanf, vswscanf

Lit les données mises en forme d’une chaîne. Il existe des versions plus sécurisées de ces fonctions. Consultez [vsscanf_s, vswscanf_s](vsscanf-s-vswscanf-s.md).

## <a name="syntax"></a>Syntaxe

```C
int vsscanf(
   const char *buffer,
   const char *format,
   va_list arglist
);
int vswscanf(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Données stockées

*format*<br/>
Chaîne de contrôle de format. Pour plus d’informations, consultez [Champs de spécification de format : fonctions scanf et wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Liste d’arguments de variable.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne le nombre de champs correctement convertis et assignés. La valeur de retour n’inclut pas les champs qui ont été lus, mais pas assignés. La valeur de retour 0 indique qu'aucun champ n'a été assigné. La valeur de retour est **EOF** pour une erreur ou si la fin de la chaîne est atteinte avant la première conversion.

Si *tampon* ou *format* est un **NULL** pointeur, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent -1 et la valeur **errno** à **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **vsscanf** fonction lit les données à partir de *tampon* dans les emplacements qui sont fournis par chaque argument dans le *arglist* liste d’arguments. Chaque argument dans la liste doit être un pointeur vers une variable qui a un type qui correspond à un spécificateur de type dans *format*. Le *format* contrôles d’argument des champs de l’interprétation de l’entrée et a les mêmes forme et fonction que le *format* argument pour le **scanf** (fonction). Si la copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

> [!IMPORTANT]
> Lorsque vous utilisez **vsscanf** pour lire une chaîne, spécifiez toujours une largeur pour les **%s** format (par exemple, **« % 32s »** au lieu de **« %s »**) ; Sinon, entrée mal formatée peut provoquer un dépassement de mémoire tampon.

**vswscanf** est une version à caractères larges de **vsscanf**; les arguments de **vswscanf** sont des chaînes à caractères larges. **vsscanf** ne gère pas les caractères hexadécimaux multioctets. **vswscanf** ne gère pas hexadécimaux entiers Unicode ou caractères de « zone de compatibilité ». Sinon, **vswscanf** et **vsscanf** ont un comportement identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf**|**vsscanf**|**vsscanf**|**vswscanf**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**vsscanf**|\<stdio.h>|
|**vswscanf**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_vsscanf.c
// compile with: /W3
// This program uses vsscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>

int call_vsscanf(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf(tokenstring, format, arglist);
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
    call_vsscanf(tokenstring, "%80s", s);
    call_vsscanf(tokenstring, "%c", &c);
    call_vsscanf(tokenstring, "%d", &i);
    call_vsscanf(tokenstring, "%f", &fp);

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
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf_s, vswscanf_s](vsscanf-s-vswscanf-s.md)<br/>
