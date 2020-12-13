---
description: 'En savoir plus sur : _controlfp_s'
title: _controlfp_s
ms.date: 4/2/2020
api_name:
- _controlfp_s
- _o__controlfp_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- controlfp_s
- _controlfp_s
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 2fed3263374df4bdac012c6d41d89adf9232c338
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146469"
---
# <a name="_controlfp_s"></a>_controlfp_s

Obtient et définit le mot de contrôle à virgule flottante. Cette version de [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md) est assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Paramètres

*currentControl*<br/>
Valeur en bits du mot de contrôle actuelle.

*newControl*<br/>
Nouvelles valeurs en bits du mot de contrôle.

*filtrage*<br/>
Masque des bits du nouveau mot de contrôle à définir.

## <a name="return-value"></a>Valeur renvoyée

Zéro en cas de réussite, ou un code d’erreur de valeur **errno** .

## <a name="remarks"></a>Notes

La fonction **_controlfp_s** est une version indépendante de la plateforme et plus sécurisée de **_control87**, qui obtient le mot de contrôle à virgule flottante dans l’adresse stockée dans *currentControl* et la définit à l’aide de *newControl*. Les bits contenus dans les valeurs indiquent l’état de contrôle à virgule flottante. L’état de contrôle à virgule flottante permet au programme de modifier les modes de précision, d’arrondi et d’infini dans le package mathématique à virgule flottante, selon la plateforme. Vous pouvez également utiliser **_controlfp_s** pour masquer ou démasquer les exceptions de virgule flottante.

Si la valeur du *masque* est égale à 0, **_controlfp_s** obtient le mot de contrôle à virgule flottante et stocke la valeur récupérée dans *currentControl*.

Si *Mask* est différent de zéro, une nouvelle valeur pour le mot de contrôle est définie : pour tout bit défini (autrement dit, égal à 1) dans le *masque*, le bit correspondant dans *New* est utilisé pour mettre à jour le mot de contrôle. En d’autres termes, *fpcntrl* = ((*fpcntrl* & ~*Mask*) &#124; (masque *newControl*  &  )) où *fpcntrl* est le mot de contrôle à virgule flottante. Dans ce scénario, *currentControl* est défini sur la valeur après la fin de la modification ; il ne s’agit pas de l’ancienne valeur de bit de mot de passe.

> [!NOTE]
> Par défaut, les bibliothèques d’exécution masquent toutes les exceptions de virgule flottante.

**_controlfp_s** est quasiment identique à la fonction **_control87** sur les plateformes Intel (x86), x64 et ARM. Si vous ciblez des plateformes x86, x64 ou ARM, vous pouvez utiliser **_control87** ou **_controlfp_s**.

La différence entre **_control87** et **_controlfp_s** réside dans la façon dont ils traitent les valeurs Denormal. Pour les plateformes Intel (x86), x64 et ARM, **_control87** pouvez définir et décocher le masque d’exception d’opérande dénormal. **_controlfp_s** ne modifie pas le masque d’exception dénormal d’opérande. Cet exemple illustre la différence :

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Les valeurs possibles pour les constantes de masque (*masque*) et les nouvelles valeurs de contrôle (*newControl*) sont indiquées dans le tableau des valeurs hexadécimales suivant. Utilisez les constantes portables listées ci-dessous (**_MCW_EM**, **_EM_INVALID**, etc.) en tant qu’arguments de ces fonctions, au lieu de fournir les valeurs hexadécimales explicitement.

Les plateformes dérivées d’Intel (x86) prennent en charge les valeurs d’entrée et de sortie DENORMAL dans le matériel. Le comportement x86 consiste à conserver les valeurs DENORMAL. La plateforme ARM et les plateformes x64 qui disposent de la prise en charge de SSE2 autorisent le vidage des opérandes et des résultats dénormalisés, ou la mise à zéro forcée. Les fonctions **_controlfp_s**, **_controlfp** et **_control87** fournissent un masque pour modifier ce comportement. L’exemple suivant illustre l’utilisation de ce masque :

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Sur les plateformes ARM, la fonction **_controlfp_s** s’applique au registre Registre fpscr. Sur les architectures x64, seul le mot de contrôle SSE2 qui est stocké dans le registre MXCSR est affecté. Sur les plateformes Intel (x86), **_controlfp_s** affecte les mots de contrôle pour le X87 et le SSE2, le cas échéant. Il est possible que les deux mots de contrôle soient incohérents entre eux (en raison d’un appel précédent à [__control87_2](control87-controlfp-control87-2.md), par exemple). s’il existe une incohérence entre les deux mots de contrôle, **_controlfp_s** définit l’indicateur **EM_AMBIGUOUS** dans *currentControl*. Il s’agit d’un message d’avertissement selon lequel le mot de contrôle retourné peut ne pas représenter l’état des deux mots de contrôle à virgule flottante avec précision.

Sur les architectures ARM et x64, la modification du mode infini ou de la précision à virgule flottante n’est pas prise en charge. Si le masque de contrôle de précision est utilisé sur la plateforme x64, la fonction déclenche une assertion et le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md).

Si le masque n’est défini correctement, cette fonction génère une exception de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne **EINVAL** et définit **errno** sur **EINVAL**.

Cette fonction est ignorée quand vous utilisez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) à compiler, car le Common Language Runtime (CLR) prend uniquement en charge la précision à virgule flottante par défaut.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="mask-constants-and-values"></a>Constantes et valeurs Mask

Pour le masque de **_MCW_EM** , l’effacement définit l’exception, ce qui permet l’exception matérielle. sa définition masque l’exception. Si une **_EM_UNDERFLOW** ou **_EM_OVERFLOW** se produit, aucune exception matérielle n’est levée tant que l’instruction à virgule flottante suivante n’est pas exécutée. Pour générer une exception matérielle immédiatement après **_EM_UNDERFLOW** ou **_EM_OVERFLOW**, appelez l’instruction MASM FWAIT.

|Mask|Valeur hexadécimale|Constante|Valeur hexadécimale|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (contrôle dénormal)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (masque d’exception d’interruption)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (contrôle infini)<br /><br /> (Non pris en charge sur les plateformes ARM ou x64.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (contrôle d’arrondi)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (contrôle de précision)<br /><br /> (Non pris en charge sur les plateformes ARM ou x64.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_contrlfp_s.c
// processor: x86
// This program uses _controlfp_s to output the FP control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word;
    int err;

    // Show original FP control word and do calculation.
    err = _controlfp_s(&control_word, 0, 0);
    if ( err ) /* handle error here */;

    printf( "Original: 0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "24-bit:   0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "Default:  0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x9001f
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0xa001f
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x9001f
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp \_ _control87_2](control87-controlfp-control87-2.md)<br/>
