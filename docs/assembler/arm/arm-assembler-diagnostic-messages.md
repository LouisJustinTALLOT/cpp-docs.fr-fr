---
title: Messages de diagnostic assembleur ARM
ms.date: 08/30/2018
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
ms.openlocfilehash: 72c1ea64501ef8104fee9bdf914a1464c07c3b76
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449211"
---
# <a name="arm-assembler-diagnostic-messages"></a>Messages de diagnostic assembleur ARM

L’assembleur Microsoft ARM (*armasm*) émet des erreurs et avertissements de diagnostics lorsqu’il les rencontre. Cet article décrit les messages plus fréquemment rencontrée.

## <a name="syntax"></a>Syntaxe

> <em>nom de fichier</em> **(** <em>numéro de ligne</em> **) :** \[ **erreur**|**avertissement** ] **A**<em>nombre</em> **:** *message*

## <a name="diagnostic-messages---errors"></a>Messages de diagnostic - erreurs

> A2193 : cette instruction génère un comportement imprévisible

L’architecture ARM ne peut pas garantir que se passe-t-il lorsque cette instruction est exécutée.  Pour plus d’informations sur les formes bien définis de cette instruction, consultez la [manuel de référence d’Architecture ARM](https://go.microsoft.com/fwlink/p/?linkid=246464).

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196 : l’instruction ne peut pas être encodée en 16 bits

L’instruction spécifiée ne peut pas être encodée en tant qu’une instruction de curseur de 16 bits.  Spécifiez une instruction 32 bits, ou réorganiser le code pour placer l’étiquette cible dans la plage d’une instruction de 16 bits.

L’assembleur peut essayer d’encoder une branche de 16 bits et échouer avec cette erreur, même si une branche de 32 bits est puissent être codée. Vous pouvez résoudre ce problème à l’aide de la `.W` spécificateur marquer explicitement la branche en tant que 32 bits.

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202 : Syntaxe d’instruction Pre-UAL interdite dans la région de curseur

Code Thumb doit utiliser la syntaxe de langage unifiée de l’assembleur (UAL).  L’ancienne syntaxe n’est plus accepté

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513 : Rotation doit être paire

Dans le mode ARM, il existe une autre syntaxe pour la spécification de constantes.  Au lieu d’écrire `#<const>`, vous pouvez écrire `#<byte>,#<rot>`, qui représente la valeur de constante qui est obtenue en faisant pivoter la valeur `<byte>` droite par `<rot>`.  Lorsque vous utilisez cette syntaxe, vous devez rendre la valeur de `<rot>` même.

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557 : Nombre incorrect d’octets pour l’écriture différée

Sur la structure NEON charger et stocker des instructions (`VLDn`, `VSTn`), il existe une autre syntaxe pour la spécification de l’écriture différée pour le Registre de base.  Au lieu de placer un point d’exclamation ( !) après l’adresse, vous pouvez spécifier une valeur immédiate qui indique le décalage à ajouter au Registre de base.  Si vous utilisez cette syntaxe, vous devez spécifier le nombre exact d’octets qui ont été chargés ou enregistrés par l’instruction.

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>Messages de diagnostic - avertissements

> A4228 : Valeur d’alignement dépasse l’alignement de la zone ; alignement ne pas garanti

L’alignement spécifié dans un `ALIGN` directive est supérieure à l’alignement de la forme `AREA`.  Par conséquent, l’assembleur ne garantit pas que le `ALIGN` directive sera honorée.

Pour résoudre ce problème, vous pouvez spécifier sur le `AREA` directive une `ALIGN` attribut est égale ou supérieure à l’alignement souhaité.

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508 : L’utilisation de cette constante pivotée est déconseillée.

Dans le mode ARM, il existe une autre syntaxe pour la spécification de constantes.  Au lieu d’écrire `#<const>`, vous pouvez écrire `#<byte>,#<rot>`, qui représente la valeur de constante qui est obtenue en faisant pivoter la valeur `<byte>` droite par `<rot>`.  Dans certains contextes, ARM a déconseillé l’utilisation de ces constantes pivotés. Dans ce cas, utilisez la basic `#<const>` syntaxe à la place.

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509 : Cette forme d’une instruction conditionnelle est déconseillée.

Cette forme d’une instruction conditionnelle a été déconseillée par ARM dans l’architecture ARMv8. Nous vous recommandons de modifier le code pour utiliser des branches conditionnelles. Pour consulter les instructions conditionnelles sont toujours gérées, consultez le [manuel de référence d’Architecture ARM](https://go.microsoft.com/fwlink/p/?linkid=246464).

Cet avertissement n’est pas émis lorsque le **- oldit** commutateur de ligne de commande est utilisé.

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>Voir aussi

[Référence de la ligne de commande de l’assembleur ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Directive d’assembleur ARM](../../assembler/arm/arm-assembler-directives.md)<br/>
