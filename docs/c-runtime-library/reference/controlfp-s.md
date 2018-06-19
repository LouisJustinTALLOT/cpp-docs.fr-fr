---
title: _controlfp_s | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 443b9ee53606bc3075e62e98012edfca79747cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405089"
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

*masque*<br/>
Masque des bits du nouveau mot de contrôle à définir.

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite, ou une **errno** code d’erreur de valeur.

## <a name="remarks"></a>Notes

Le **_controlfp_s** fonction est une version indépendant de la plateforme et plus sécurisée de **_control87**, qui obtient le mot de contrôle à virgule flottante dans l’adresse qui est stocké dans  *currentControl* et lui affecte à l’aide de *newControl*. Les bits contenus dans les valeurs indiquent l’état de contrôle à virgule flottante. L’état de contrôle à virgule flottante permet au programme de modifier les modes de précision, d’arrondi et d’infini dans le package mathématique à virgule flottante, selon la plateforme. Vous pouvez également utiliser **_controlfp_s** pour masquer ou afficher les exceptions de virgule flottante.

Si la valeur de *masque* est égal à 0, **_controlfp_s** Obtient le mot de contrôle à virgule flottante et stocke la valeur récupérée dans *currentControl*.

Si *masque* est différent de zéro, une nouvelle valeur pour le mot de contrôle est définie : pour n’importe quel bit est défini (autrement dit, il est égal à 1) dans *masque*, le bit correspondant dans *nouveau* est utilisé pour mettre à jour le contrôle Word. En d’autres termes, *fpcntrl* = ((*fpcntrl* & ~*masque*) &#124; (*newControl* & *masque* )) où *fpcntrl* est le mot de contrôle à virgule flottante. Dans ce scénario, *currentControl* a la valeur après la modification se termine ; il n’est pas l’ancienne valeur de bit de mot de contrôle.

> [!NOTE]
> Par défaut, les bibliothèques d’exécution masquent toutes les exceptions de virgule flottante.

**_controlfp_s** est presque identique à la **_control87** fonctionnent sur Intel (x86), x64 et les plateformes ARM. Si vous ciblez les plateformes ARM, x64 ou x86, vous pouvez utiliser **_control87** ou **_controlfp_s**.

La différence entre **_control87** et **_controlfp_s** est denormal dans la façon dont ils traitent les valeurs. Pour Intel (x86), x 64 et les plateformes ARM, **_control87** pouvez définir et effacer le masque d’exception DENORMAL l’opérande. **_controlfp_s** ne modifie pas le masque d’exception DENORMAL l’opérande. Cet exemple illustre la différence :

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Les valeurs possibles pour la constante masque (*masque*) et les nouvelles valeurs de contrôle (*newControl*) sont affichés dans le tableau de valeurs hexadécimales suivant. Utilisez l’une des constantes portables répertoriées ci-dessous (**_MCW_EM**, **_EM_INVALID**, et ainsi de suite) en tant qu’arguments à ces fonctions, au lieu de fournir la valeur hexadécimale valeurs explicitement.

Les plateformes dérivées d’Intel (x86) prennent en charge les valeurs d’entrée et de sortie DENORMAL dans le matériel. Le comportement x86 consiste à conserver les valeurs DENORMAL. La plateforme ARM et le x64 prend en charge les plateformes qui ont SSE2 activer DÉNORMALISÉE opérandes et les résultats à être vidées ou forcé à zéro. Le **_controlfp_s**, **_controlfp**, et **_control87** fonctions fournissent un masque pour modifier ce comportement. L’exemple suivant illustre l’utilisation de ce masque :

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Sur les plateformes ARM, le **_controlfp_s** fonction s’applique au Registre fpscr. Sur x64 architectures, seul le mot de contrôle SSE2 est stocké dans le MXCSR register est affecté. Sur les plateformes Intel (x86), **_controlfp_s** affecte les mots de contrôle pour le x87 et le SSE2, le cas échéant. Il est possible que les mots de deux contrôle sont incompatibles entre eux (en raison d’un appel précédent à [__control87_2](control87-controlfp-control87-2.md), par exemple) ; s’il existe une incohérence entre les mots de contrôle de deux, **_controlfp_s** définit le **EM_AMBIGUOUS** indicateur dans *currentControl*. Il s’agit d’un message d’avertissement selon lequel le mot de contrôle retourné peut ne pas représenter l’état des deux mots de contrôle à virgule flottante avec précision.

Sur la ARM et x64 architectures, changer le mode de l’infini ou de la précision en virgule flottante ne sont pas pris en charge. Si le masque de contrôle de précision est utilisé sur le x64 plateforme, la fonction génère une assertion et le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Si le masque n’est défini correctement, cette fonction génère une exception de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne **EINVAL** et définit **errno** à **EINVAL**.

Cette fonction est ignorée lorsque vous utilisez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) de compilation parce que le common language runtime (CLR) prend uniquement en charge la précision en virgule flottante par défaut.

### <a name="mask-constants-and-values"></a>Masque les constantes et valeurs

Pour le **_MCW_EM** masque, désactivant définit l’exception, ce qui permet à l’exception de matériel ; définition masque l’exception. Si un **_EM_UNDERFLOW** ou **_EM_OVERFLOW** se produit, aucune exception matérielle n’est levée tant que la prochaine instruction à virgule flottante est exécutée. Pour générer une exception matérielle immédiatement après **_EM_UNDERFLOW** ou **_EM_OVERFLOW**, appelez l’instruction FWAIT MASM.

|Masque|Valeur hexadécimale|Constante|Valeur hexadécimale|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (denormal contrôle)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (masque d’exception d’interruption)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (contrôle de l’infini)<br /><br /> (Non pris en charge ARM ou x64 plates-formes.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (arrondi contrôle)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (contrôle de précision)<br /><br /> (Non pris en charge ARM ou x64 plates-formes.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Spécifications

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
