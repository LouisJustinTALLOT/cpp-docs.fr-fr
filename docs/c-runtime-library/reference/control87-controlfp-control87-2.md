---
title: _control87, _controlfp, __control87_2
ms.date: 04/05/2018
apiname:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
ms.openlocfilehash: e2ebfdc80a451ebf02563f78a62dd08618f92bcd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505870"
---
# <a name="control87-controlfp-control872"></a>_control87, _controlfp, __control87_2

Obtient et définit le mot de contrôle à virgule flottante. Une version plus sécurisée de **_controlfp** est disponible ; consultez [_controlfp_s](controlfp-s.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _control87(
   unsigned int new,
   unsigned int mask
);
unsigned int _controlfp(
   unsigned int new,
   unsigned int mask
);
int __control87_2(
   unsigned int new,
   unsigned int mask,
   unsigned int* x86_cw,
   unsigned int* sse2_cw
);
```

### <a name="parameters"></a>Paramètres

*new*<br/>
Nouvelles valeurs en bits du mot de contrôle.

*Masque*<br/>
Masque des bits du nouveau mot de contrôle à définir.

*x86_cw*<br/>
Renseigné avec le mot de contrôle pour l’unité de virgule flottante x87. Passer la valeur 0 (**NULL**) pour définir le mot de contrôle SSE2 uniquement.

*sse2_cw*<br/>
Mot de contrôle pour l’unité de virgule flottante SSE. Passer la valeur 0 (**NULL**) pour définir uniquement les x87 mot de contrôle.

## <a name="return-value"></a>Valeur de retour

Pour **_control87** et **_controlfp**, les bits dans la valeur retournée indiquent l’état de contrôle à virgule flottante. Pour obtenir une définition complète des bits retournés par **_control87**, consultez FLOAT. H.

Pour **__control87_2**, la valeur de retour est 1, ce qui indique la réussite.

## <a name="remarks"></a>Notes

Le **_control87** fonction obtient et définit le mot de contrôle à virgule flottante. Le mot de contrôle à virgule flottante permet au programme de modifier les modes de précision, d’arrondi et d’infini dans le package mathématique à virgule flottante, selon la plateforme. Vous pouvez également utiliser **_control87** pour masquer ou démasquer les exceptions de virgule flottante. Si la valeur de *masque* est égal à 0, **_control87** Obtient le mot de contrôle à virgule flottante. Si *masque* est différent de zéro, une nouvelle valeur pour le mot de contrôle est définie : pour tout bit activé (autrement dit, égal à 1) dans *masque*, le bit correspondant dans *nouvelle* est utilisé pour mettre à jour le contrôle Word. En d’autres termes, **fpcntrl** = ((**fpcntrl** & ~*masque*) &#124; (*nouveau* & *masque*)) où **fpcntrl** est le mot de contrôle à virgule flottante.

> [!NOTE]
> Par défaut, les bibliothèques d’exécution masquent toutes les exceptions de virgule flottante.

**_controlfp** est une version portable indépendante de la plateforme de **_control87**. Il est presque identique à la **_control87** fonction sur x86 x64, plates-formes et ARM. Si vous ciblez x86, x64 ou les plateformes ARM, utilisez **_control87** ou **_controlfp**.

La différence entre **_control87** et **_controlfp** est dans la manière dont elles traitent les valeurs DENORMAL. Pour les plateformes ARM, x86 et x64 **_control87** pouvez activer et désactiver le masque d’exception DENORMAL OPERAND. **_controlfp** ne modifie pas le masque d’exception DENORMAL OPERAND. Cet exemple illustre la différence :

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Les valeurs possibles pour la constante du masque (*masque*) et les nouvelles valeurs de contrôle (*nouveau*) sont affichés dans le tableau de valeurs hexadécimales suivant. Utilisez l’une des constantes portables répertoriées ci-dessous (**_MCW_EM**, **_EM_INVALID**, et ainsi de suite) en tant qu’arguments de ces fonctions, au lieu de fournir la valeur hexadécimale valeurs explicitement.

Les plateformes x86 dérivées d’Intel prennent en charge l’entrée DENORMAL et de sortie des valeurs dans le matériel. Le comportement x86 consiste à conserver les valeurs DENORMAL. La plateforme ARM et le x64 prennent en charge des plateformes qui ont SSE2 activer DENORMAL opérandes et les résultats afin d’être vidés ou définis à zéro. Le **_controlfp** et **_control87** fonctions fournissent un masque pour modifier ce comportement. L’exemple suivant illustre l’utilisation de ce masque.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Sur les plateformes ARM, le **_control87** et **_controlfp** fonctions s’appliquent au Registre fpscr. Sur x64 architectures, seul le mot de contrôle SSE2 stocké dans le Registre MXCSR est affecté. Sur x86 plateformes, **_control87** et **_controlfp** affectent les mots de contrôle pour x87 et SSE2, le cas échéant. La fonction **__control87_2** permet x87 et unités de virgule flottante SSE2 pour l’ensemble ou séparément. Si vous souhaitez affecter les deux unités, passez les adresses des deux entiers à **x86_cw** et **sse2_cw**. Si vous souhaitez uniquement affecter une unité, passez une adresse pour ce paramètre, mais passer la valeur 0 (**NULL**) pour l’autre. Si 0 est passé pour l’un de ces paramètres, la fonction n’a aucun effet sur cette unité de virgule flottante. Cette fonctionnalité peut être utile dans les cas où une partie du code utilise l’unité de virgule flottante x87 et une autre partie l’unité de virgule flottante SSE2. Si vous utilisez **__control87_2** dans une partie d’un programme et définissez des valeurs différentes pour les mots de contrôle à virgule flottante, puis utiliser **_control87** ou **_controlfp** pour en savoir plus manipuler le mot de contrôle, puis **_control87** et **_controlfp** peut être incapable de renvoyer un mot de contrôle unique pour représenter l’état de ces deux unités de virgule flottante. Dans ce cas, ces fonctions définissent le **indicateur em_ambiguous prend** indicateur dans la valeur entière retournée pour indiquer qu’il existe une incohérence entre les deux mots de contrôle. Il s’agit d’un message d’avertissement selon lequel le mot de contrôle retourné peut ne pas représenter l’état des deux mots de contrôle à virgule flottante avec précision.

Sur la ARM et x64 architectures, en modifiant le mode d’infini ou la précision à virgule flottante ne sont pas pris en charge. Si le masque de contrôle de précision est utilisé sur le x64 plateforme, la fonction génère une assertion et le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2** n’est pas pris en charge sur le ARM ou x64 architectures. Si vous utilisez **__control87_2** et compiler votre programme pour le ARM ou x64 architectures, le compilateur génère une erreur.

Ces fonctions sont ignorées lorsque vous utilisez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) pour compiler, car le common language runtime (CLR) prend uniquement en charge la précision à virgule flottante par défaut.

**Valeurs hexadécimales**

Pour le **_MCW_EM** masque, effacer le masque définit l’exception, ce qui permet à l’exception de matériel ; définir masque l’exception. Si un **_EM_UNDERFLOW** ou **_EM_OVERFLOW** se produit, aucune exception de matériel n’est levée jusqu'à ce que la prochaine instruction à virgule flottante est exécutée. Pour générer une exception matérielle immédiatement après **_EM_UNDERFLOW** ou **_EM_OVERFLOW**, appelez le **FWAIT** instruction MASM.

|Masque|Valeur hexadécimale|Constante|Valeur hexadécimale|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (contrôle de la dénormalisation)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (masque d’exception d’interruption)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (contrôle de l’infini)<br /><br /> (Non pris en charge sur ARM ou x64] plateformes.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (en arrondissant contrôle)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (contrôle de précision)<br /><br /> (Pas plateformes prises en charge sur ARM ou x64.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_control87**, **_controlfp**, **_control87_2**|\<float.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_cntrl87.c
// processor: x86
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87;

    // Show original x87 control word and do calculation.
    control_word_x87 = __control87_2(0, 0,
                                     &control_word_x87, 0);
    printf( "Original: 0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    control_word_x87 = __control87_2(_PC_24, MCW_PC,
                                     &control_word_x87, 0);
    printf( "24-bit:   0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    control_word_x87 = __control87_2( _CW_DEFAULT, MCW_PC,
                                     &control_word_x87, 0 );
    printf( "Default:  0x%.4x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0001
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0x0001
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x0001
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
