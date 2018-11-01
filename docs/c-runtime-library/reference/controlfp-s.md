---
title: _controlfp_s
ms.date: 04/05/2018
apiname:
- _controlfp_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 0624cbfb4870ca87efebac01a8de682b588a4ca3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506676"
---
# <a name="controlfps"></a>_controlfp_s

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

*Masque*<br/>
Masque des bits du nouveau mot de contrôle à définir.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, ou une **errno** code d’erreur de valeur.

## <a name="remarks"></a>Notes

Le **_controlfp_s** (fonction) est une version indépendante de la plateforme et plus sûre de **_control87**, qui obtient le mot de contrôle à virgule flottante dans l’adresse qui est stocké dans  *currentControl* et lui affecte à l’aide de *newControl*. Les bits contenus dans les valeurs indiquent l’état de contrôle à virgule flottante. L’état de contrôle à virgule flottante permet au programme de modifier les modes de précision, d’arrondi et d’infini dans le package mathématique à virgule flottante, selon la plateforme. Vous pouvez également utiliser **_controlfp_s** pour masquer ou démasquer les exceptions de virgule flottante.

Si la valeur de *masque* est égal à 0, **_controlfp_s** Obtient le mot de contrôle à virgule flottante et stocke la valeur récupérée dans *currentControl*.

Si *masque* est différent de zéro, une nouvelle valeur pour le mot de contrôle est définie : pour tout bit est défini (autrement dit, égal à 1) dans *masque*, le bit correspondant dans *nouveau* est utilisé pour mettre à jour le contrôle Word. En d’autres termes, *fpcntrl* = ((*fpcntrl* & ~*masque*) &#124; (*newControl* & *masque* )) où *fpcntrl* est le mot de contrôle à virgule flottante. Dans ce scénario, *currentControl* est définie sur la valeur après la modification effectuée ; il n’est pas l’ancienne valeur de bit du mot de contrôle.

> [!NOTE]
> Par défaut, les bibliothèques d’exécution masquent toutes les exceptions de virgule flottante.

**_controlfp_s** est presque identique à la **_control87** fonctionnent sur Intel (x86) x64, plates-formes et ARM. Si vous ciblez x86, x64 ou les plateformes ARM, vous pouvez utiliser **_control87** ou **_controlfp_s**.

La différence entre **_control87** et **_controlfp_s** est dans la manière dont elles traitent les valeurs denormal. Pour Intel (x86), x 64 et les plateformes ARM, **_control87** pouvez activer et désactiver le masque d’exception DENORMAL OPERAND. **_controlfp_s** ne modifie pas le masque d’exception DENORMAL OPERAND. Cet exemple illustre la différence :

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Les valeurs possibles pour la constante du masque (*masque*) et les nouvelles valeurs de contrôle (*newControl*) sont affichés dans le tableau de valeurs hexadécimales suivant. Utilisez l’une des constantes portables répertoriées ci-dessous (**_MCW_EM**, **_EM_INVALID**, et ainsi de suite) en tant qu’arguments de ces fonctions, au lieu de fournir la valeur hexadécimale valeurs explicitement.

Les plateformes dérivées d’Intel (x86) prennent en charge les valeurs d’entrée et de sortie DENORMAL dans le matériel. Le comportement x86 consiste à conserver les valeurs DENORMAL. La plateforme ARM et le x64 prennent en charge des plateformes qui ont SSE2 activer DENORMAL opérandes et les résultats afin d’être vidés ou définis à zéro. Le **_controlfp_s**, **_controlfp**, et **_control87** fonctions fournissent un masque pour modifier ce comportement. L’exemple suivant illustre l’utilisation de ce masque :

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Sur les plateformes ARM, le **_controlfp_s** fonction s’applique au Registre fpscr. Sur x64 architectures, seul le mot de contrôle SSE2 stocké dans le Registre MXCSR est affecté. Sur les plateformes Intel (x86), **_controlfp_s** affecte les mots de contrôle pour x87 et SSE2, le cas échéant. Il est possible pour les deux mots de contrôle sont incompatibles entre eux (en raison d’un appel précédent à [__control87_2](control87-controlfp-control87-2.md), par exemple) ; s’il existe une incohérence entre les deux mots de contrôle, **_controlfp_s** définit le **indicateur em_ambiguous prend** indicateur dans *currentControl*. Il s’agit d’un message d’avertissement selon lequel le mot de contrôle retourné peut ne pas représenter l’état des deux mots de contrôle à virgule flottante avec précision.

Sur la ARM et x64 architectures, en modifiant le mode d’infini ou la précision à virgule flottante ne sont pas pris en charge. Si le masque de contrôle de précision est utilisé sur le x64 plateforme, la fonction génère une assertion et le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Si le masque n’est défini correctement, cette fonction génère une exception de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne **EINVAL** et définit **errno** à **EINVAL**.

Cette fonction est ignorée lorsque vous utilisez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) pour compiler, car le common language runtime (CLR) prend uniquement en charge la précision à virgule flottante par défaut.

### <a name="mask-constants-and-values"></a>Constantes de masque et de valeurs

Pour le **_MCW_EM** masque, désactiver ce dernier définit l’exception, ce qui permet à l’exception de matériel ; définir masque l’exception. Si un **_EM_UNDERFLOW** ou **_EM_OVERFLOW** se produit, aucune exception de matériel n’est levée jusqu'à ce que la prochaine instruction à virgule flottante est exécutée. Pour générer une exception matérielle immédiatement après **_EM_UNDERFLOW** ou **_EM_OVERFLOW**, appelez l’instruction MASM FWAIT.

|Masque|Valeur hexadécimale|Constante|Valeur hexadécimale|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (contrôle de la dénormalisation)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (masque d’exception d’interruption)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (contrôle de l’infini)<br /><br /> (Pas plateformes prises en charge sur ARM ou x64.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (en arrondissant contrôle)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (contrôle de précision)<br /><br /> (Pas plateformes prises en charge sur ARM ou x64.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
