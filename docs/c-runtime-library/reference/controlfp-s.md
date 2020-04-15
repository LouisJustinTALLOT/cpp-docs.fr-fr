---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 4b36cc9f5ed83b68cb15c39be91165ed7aa86d7b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348531"
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

*nouveauControl*<br/>
Nouvelles valeurs en bits du mot de contrôle.

*masque*<br/>
Masque des bits du nouveau mot de contrôle à définir.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de succès, ou un code **d’erreur de valeur errno.**

## <a name="remarks"></a>Notes

La fonction **_controlfp_s** est une version indépendante et plus sécurisée de **_control87**, qui obtient le mot de contrôle de point flottant dans l’adresse qui est stockée dans *CurrentControl* et le définit en utilisant *newControl*. Les bits contenus dans les valeurs indiquent l’état de contrôle à virgule flottante. L’état de contrôle à virgule flottante permet au programme de modifier les modes de précision, d’arrondi et d’infini dans le package mathématique à virgule flottante, selon la plateforme. Vous pouvez également utiliser **_controlfp_s** pour masquer ou démasquer les exceptions au point flottant.

Si la valeur pour le *masque* est égale à 0, **_controlfp_s** obtient le mot de contrôle de point flottant et stocke la valeur récupérée dans *le courantControl*.

Si *le masque* n’est paszero, une nouvelle valeur pour le mot de contrôle est définie: Pour tout bit qui est réglé (c’est-à-dire, égal à 1) dans le *masque*, le bit correspondant dans le *nouveau* est utilisé pour mettre à jour le mot de contrôle. En d’autres termes, *fpcntrl* ((fpcntrl & -*masque*) &#124; (nouveau*masque**de contrôle))* & où *fpcntrl* est le mot de contrôle de point flottant.*fpcntrl* Dans ce scénario, *currentControl* est réglé à la valeur après la fin du changement; ce n’est pas l’ancienne valeur de jeu de contrôle-mot.

> [!NOTE]
> Par défaut, les bibliothèques d’exécution masquent toutes les exceptions de virgule flottante.

**_controlfp_s** est presque identique à la fonction **_control87** sur les plateformes Intel (x86), x64 et ARM. Si vous ciblez les plateformes x86, x64 ou ARM, vous pouvez utiliser **_control87** ou **_controlfp_s**.

La différence entre **_control87** et **_controlfp_s** réside dans la façon dont ils traitent les valeurs dénommales. Pour les plateformes Intel (x86), x64 et ARM, **_control87** peuvent définir et effacer le masque d’exception DENORMAL OPERAND. **_controlfp_s** ne modifie pas le masque d’exception DENORMAL OPERAND. Cet exemple illustre la différence :

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Les valeurs possibles pour la constante de masque (*masque*) et les nouvelles valeurs de contrôle *(newControl*) sont montrées dans le tableau suivant des valeurs hexadecimales. Utilisez les constantes portables énumérées ci-dessous **(_MCW_EM**, **_EM_INVALID**, et ainsi de suite) comme arguments à ces fonctions, plutôt que de fournir les valeurs hexadecimal explicitement.

Les plateformes dérivées d’Intel (x86) prennent en charge les valeurs d’entrée et de sortie DENORMAL dans le matériel. Le comportement x86 consiste à conserver les valeurs DENORMAL. La plate-forme ARM et les plates-formes x64 qui ont le support SSE2 permettent de rincer les opérandes et les résultats DENORMAL, ou contraints à zéro. Les **fonctions _controlfp_s**, **_controlfp**et **_control87** fournissent un masque pour changer ce comportement. L’exemple suivant illustre l’utilisation de ce masque :

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Sur les plateformes ARM, la fonction **_controlfp_s** s’applique au registre FPSCR. Sur les architectures x64, seul le mot de contrôle SSE2 stocké dans le registre MXCSR est affecté. Sur les plateformes Intel (x86), **_controlfp_s** affecte les mots de contrôle pour le x87 et le SSE2, s’il est présent. Il est possible que les deux mots de contrôle soient incompatibles les uns avec les autres (en raison d’un appel précédent à [__control87_2](control87-controlfp-control87-2.md), par exemple); s’il y a une incohérence entre les deux mots de contrôle, **_controlfp_s** fixe le **drapeau EM_AMBIGUOUS** dans *currentControl*. Il s’agit d’un message d’avertissement selon lequel le mot de contrôle retourné peut ne pas représenter l’état des deux mots de contrôle à virgule flottante avec précision.

Sur les architectures ARM et x64, le changement du mode infini ou la précision du point flottant n’est pas pris en charge. Si le masque de commande de précision est utilisé sur la plate-forme x64, la fonction soulève une affirmation et le gestionnaire de paramètres invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md).

Si le masque n’est défini correctement, cette fonction génère une exception de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction renvoie **EINVAL** et définit **errno** à **EINVAL**.

Cette fonction est ignorée lorsque vous utilisez [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) pour compiler parce que l’heure courante de fonctionnement de la langue (CLR) ne prend en charge que la précision flottante par défaut.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="mask-constants-and-values"></a>Masquer les constantes et les valeurs

Pour le masque **_MCW_EM,** l’effacer définit l’exception, ce qui permet l’exception matérielle; le réglage cache l’exception. Si un **_EM_UNDERFLOW** ou **_EM_OVERFLOW** se produit, aucune exception matérielle n’est lancée jusqu’à ce que la prochaine instruction de point flottant soit exécutée. Pour générer une exception matérielle immédiatement après **_EM_UNDERFLOW** ou **_EM_OVERFLOW,** appelez l’instruction FWAIT MASM.

|Mask|Valeur hexadécimale|Constant|Valeur hexadécimale|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (contrôle normal)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (Interrupt exception masque)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (contrôle de l’infini)<br /><br /> (Non pris en charge sur les plates-formes ARM ou x64.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (contrôle de l’arrondissement)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (contrôle de précision)<br /><br /> (Non pris en charge sur les plates-formes ARM ou x64.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

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

[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
