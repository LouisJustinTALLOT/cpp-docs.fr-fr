---
title: _matherr
ms.date: 04/05/2018
apiname:
- _matherr
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
- _matherr
- matherr
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: 980bf8a14ceace82a76562cc47d353f78dbca582
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445719"
---
# <a name="matherr"></a>_matherr

Gère les erreurs mathématiques.

## <a name="syntax"></a>Syntaxe

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>Paramètres

*except*<br/>
Pointeur vers la structure contenant des informations sur l’erreur.

## <a name="return-value"></a>Valeur de retour

**_matherr** retourne 0 pour indiquer une erreur ou une valeur différente de zéro pour indiquer la réussite. Si **_matherr** retourne 0, un message d’erreur peut être affichés et **errno** est définie sur une valeur d’erreur approprié. Si **_matherr** renvoie une valeur différente de zéro, aucun message d’erreur s’affiche et **errno** reste inchangé.

Pour plus d’informations sur ces codes de retour, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_matherr** fonction traite les erreurs générées par les fonctions à virgule flottante de la bibliothèque mathématique. Ces fonctions appellent **_matherr** quand une erreur est détectée.

Pour une gestion particulière des erreurs, vous pouvez fournir une autre définition de **_matherr**. Si vous utilisez la version liée dynamiquement de la bibliothèque d’exécution C (CRT), vous pouvez remplacer la valeur par défaut **_matherr** routine dans un fichier exécutable avec une version défini par l’utilisateur du client. Toutefois, vous ne pouvez pas remplacer la valeur par défaut **_matherr** routine dans un client de la DLL de la DLL CRT.

Lorsqu’une erreur se produit dans une routine mathématique, **_matherr** est appelée avec un pointeur vers un **_exception** structure de type (défini dans \<math.h >) en tant qu’argument. La structure **_exception** contient les éléments suivants.

```C
struct _exception
{
    int    type;   // exception type - see below
    char*  name;   // name of function where error occurred
    double arg1;   // first argument to function
    double arg2;   // second argument (if any) to function
    double retval; // value to be returned by function
};
```

Le **type** membre spécifie le type d’erreur mathématique. C’est une des valeurs suivantes, définies dans \<math.h > :

|Macro|Signification|
|-|-|
**_DOMAINE**|Erreur de domaine d’argument
**_SING**|Singularité de l’argument
**_OVERFLOW**|Erreur de plage avec dépassement
**_PLOSS**|Perte partielle de précision
**_TLOSS**|Perte totale de précision
**_UNDERFLOW**|Le résultat est trop petit pour être représenté. (Cette condition n’est pas prise en charge.)

Le membre de structure **name** est un pointeur désignant une chaîne terminée par le caractère Null qui contient le nom de la fonction ayant provoqué l’erreur. Les membres de structure **arg1** et **arg2** spécifient les valeurs qui ont provoqué l’erreur. Si seul un seul argument est fourni, il est stocké dans **arg1**.

La valeur de retour par défaut pour l’erreur donnée est **retval**. Si vous modifiez la valeur de retour, elle doit spécifier si une erreur s’est effectivement produite.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_matherr**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_matherr.c
/* illustrates writing an error routine for math
* functions. The error function must be:
*      _matherr
*/

#include <math.h>
#include <string.h>
#include <stdio.h>

int main()
{
    /* Do several math operations that cause errors. The _matherr
     * routine handles _DOMAIN errors, but lets the system handle
     * other errors normally.
     */
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );
}

/* Handle several math errors caused by passing a negative argument
* to log or log10 (_DOMAIN errors). When this happens, _matherr
* returns the natural or base-10 logarithm of the absolute value
* of the argument and suppresses the usual error message.
*/
int _matherr( struct _exception *except )
{
    /* Handle _DOMAIN errors for log or log10. */
    if( except->type == _DOMAIN )
    {
        if( strcmp( except->name, "log" ) == 0 )
        {
            except->retval = log( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
        else if( strcmp( except->name, "log10" ) == 0 )
        {
            except->retval = log10( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
    }
    printf( "Normal: " );
    return 0;    /* Else use the default actions */
}
```

```Output
Special: using absolute value: log: _DOMAIN error
log( -2.0 ) = 6.931472e-01
Special: using absolute value: log10: _DOMAIN error
log10( -5.0 ) = 6.989700e-01
Normal: log( 0.0 ) = -inf
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
