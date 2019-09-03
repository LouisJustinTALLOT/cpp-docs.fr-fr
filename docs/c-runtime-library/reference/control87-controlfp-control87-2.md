---
title: _control87, _controlfp, __control87_2
ms.date: 08/29/2019
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
ms.openlocfilehash: 75b2870543ec3ddd20d445a492ad4270b91e80d7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218416"
---
# <a name="_control87-_controlfp-__control87_2"></a>_control87, _controlfp, __control87_2

Obtient et définit le mot de contrôle à virgule flottante. Une version plus sécurisée de _ **controlfp** est disponible; consultez [_controlfp_s](controlfp-s.md).

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

*new*\
Nouvelles valeurs en bits du mot de contrôle.

*filtrage*\
Masque des bits du nouveau mot de contrôle à définir.

*x86_cw*\
Renseigné avec le mot de contrôle pour l’unité de virgule flottante x87. Transmettez 0 (**null**) pour définir uniquement le mot de contrôle SSE2.

*sse2_cw*\
Mot de contrôle pour l’unité de virgule flottante SSE. Transmettez 0 (**null**) pour définir uniquement le mot de contrôle X87.

## <a name="return-value"></a>Valeur de retour

Pour **_control87** et _ **controlfp**, les bits de la valeur retournée indiquent l’état de contrôle à virgule flottante. Pour obtenir une définition complète des bits retournés par **_control87**, consultez float. Manutention.

Pour **__control87_2**, la valeur de retour est 1, ce qui indique une réussite.

## <a name="remarks"></a>Notes

La fonction **_control87** obtient et définit le mot de contrôle à virgule flottante. Le mot de contrôle à virgule flottante permet au programme de modifier les modes de précision, d’arrondi et d’infini, en fonction de la plateforme. Vous pouvez également utiliser **_control87** pour masquer ou démasquer les exceptions de virgule flottante. Si la valeur du *masque* est égale à 0, **_control87** obtient le mot de contrôle à virgule flottante. Si *Mask* est différent de zéro, une nouvelle valeur est définie pour le mot de contrôle: Pour tout bit sur (autrement dit, égal à 1) dans le *masque*, le bit correspondant dans *New* est utilisé pour mettre à jour le mot de contrôle. En d’autres termes **, fpcntrl** = ((**fpcntrl** & ~*Mask*) &#124; (*nouveau* & *masque*)) où **fpcntrl** est le mot de contrôle à virgule flottante.

> [!NOTE]
> Par défaut, les bibliothèques d’exécution masquent toutes les exceptions de virgule flottante.

_ **controlfp** est une version portable, indépendante de la plateforme, de **_control87** qui est quasiment identique à la fonction **_control87** . Si votre code cible plusieurs plateformes, utilisez _ **controlfp** ou **_controlfp_s**. La différence entre **_control87** et _ **controlfp** réside dans la façon dont ils traitent les valeurs Denormal. Pour les plateformes x86, x64, ARM et ARM64, **_control87** peut définir et désélectionner le masque d’exception Denormal OPERAND. _ **controlfp** ne modifie pas le masque d’exception dénormal des opérandes. Cet exemple illustre la différence :

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Les valeurs possibles pour les constantes de masque (*masque*) et les nouvelles valeurs de contrôle (*nouveau*) s’affichent dans le tableau de contrôles des masques et des valeurs de mot. Utilisez les constantes portables listées ci-dessous ( **_MCW_EM**, **_EM_INVALID**, etc.) comme arguments pour ces fonctions, au lieu de fournir les valeurs hexadécimales explicitement.

Les plateformes dérivées d’Intel x86 prennent en charge les valeurs d’entrée et de sortie dénormalisées dans le matériel. Le comportement x86 consiste à conserver les valeurs DENORMAL. Les plateformes ARM et ARM64 et les plateformes x64 qui disposent de la prise en charge de SSE2 activent les opérandes et les résultats dénormals à vider, ou sont forcés à zéro. Les fonctions _ **controlfp** et **_control87** fournissent un masque pour modifier ce comportement. L’exemple suivant illustre l’utilisation de ce masque.

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Sur les plateformes ARM et ARM64, les fonctions **_control87** et _ **controlfp** s’appliquent au registre Registre fpscr. Seul le mot de contrôle SSE2 qui est stocké dans le registre MXCSR est affecté sur les plateformes x64. Sur les plateformes x86, **_control87** et _ **controlfp** affectent les mots de contrôle pour le X87 et le SSE2, le cas échéant.

La fonction **__control87_2** permet de contrôler les unités à virgule flottante X87 et SSE2 ensemble ou séparément. Pour affecter les deux unités, transmettez les adresses de deux entiers à **x86_cw** et **sse2_cw**. Si vous souhaitez uniquement affecter une unité, transmettez une adresse pour ce paramètre, mais transmettez la valeur 0 (**null**) pour l’autre. Si 0 est passé pour l’un de ces paramètres, la fonction n’a aucun effet sur cette unité de virgule flottante. Elle est utile quand une partie de votre code utilise l’unité à virgule flottante X87 et qu’une autre partie utilise l’unité à virgule flottante SSE2.

Si vous utilisez **__control87_2** pour définir des valeurs différentes pour les mots de contrôle à virgule flottante, **_control87** ou _ **controlfp** peut ne pas être en mesure de retourner un mot de contrôle unique pour représenter l’état des deux unités à virgule flottante. Dans ce cas, ces fonctions définissent l’indicateur **EM_AMBIGUOUS** dans la valeur entière retournée pour indiquer une incohérence entre les deux mots de contrôle. L’indicateur **EM_AMBIGUOUS** est un avertissement indiquant que le mot de contrôle retourné peut ne pas représenter l’état des deux mots de contrôle à virgule flottante avec précision.

Sur les plateformes ARM, ARM64 et x64, la modification du mode infini ou de la précision à virgule flottante n’est pas prise en charge. Si le masque de contrôle de précision est utilisé sur la plateforme x64, la fonction lève une assertion, et le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md).

> [!NOTE]
> **__control87_2** n’est pas pris en charge sur les plateformes ARM, ARM64 ou x64. Si vous utilisez **__control87_2** et compilez votre programme pour les plateformes ARM, ARM64 ou x64, le compilateur génère une erreur.

Ces fonctions sont ignorées lorsque vous utilisez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) à compiler. Le common language runtime (CLR) prend uniquement en charge la précision à virgule flottante par défaut.

### <a name="control-word-masks-and-values"></a>Contrôler les masques et les valeurs de mots

Pour le masque **_MCW_EM** , l’effacement du masque définit l’exception, ce qui permet l’exception matérielle. la définition du masque masque l’exception. Si un **_EM_UNDERFLOW** ou **_EM_OVERFLOW** se produit, aucune exception matérielle n’est levée tant que l’instruction à virgule flottante suivante n’est pas exécutée. Pour générer une exception matérielle immédiatement après **_EM_UNDERFLOW** ou **_EM_OVERFLOW**, appelez l’instruction **FWAIT** MASM.

|Masque|Valeur hexadécimale|Constante|Valeur hexadécimale|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (Contrôle de dénormalisation)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (Masque d’exception d’interruption)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (Contrôle infini)<br /><br /> (Non pris en charge sur les plateformes ARM ou x64.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (Contrôle d’arrondi)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (Contrôle de précision)<br /><br /> (Non pris en charge sur les plateformes ARM ou x64.)|0x00030000|**_PC_24** (24 bits)<br /><br /> **_PC_53** (53 bits)<br /><br /> **_PC_64** (64 bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_control87**, **_controlfp**, **_control87_2**|\<float.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_cntrl87.c
// processor: x86
// compile by using: cl /W4 /arch:IA32 crt_cntrl87.c
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87 = 0;
    int result;

    // Show original x87 control word and do calculation.
    result = __control87_2(0, 0, &control_word_x87, 0 );
    printf( "Original: 0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    result = __control87_2(_PC_24, MCW_PC, &control_word_x87, 0 );
    printf( "24-bit:   0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    result = __control87_2( _CW_DEFAULT, MCW_PC, &control_word_x87, 0 );
    printf( "Default:  0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
24-bit:   0x000a001f
0.1 * 0.1 = 9.999999776482582e-03
Default:  0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
```

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[_clear87, _clearfp](clear87-clearfp.md)\
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)\
[_controlfp_s](controlfp-s.md)
