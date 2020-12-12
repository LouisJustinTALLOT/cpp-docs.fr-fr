---
description: 'En savoir plus sur : les messages de diagnostic de l’assembleur ARM'
title: Messages de diagnostic de l’assembleur ARM
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
ms.openlocfilehash: 91e4640c161cbb58522c3680ae5decdb4cc1e992
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118197"
---
# <a name="arm-assembler-diagnostic-messages"></a>Messages de diagnostic de l’assembleur ARM

L’assembleur Microsoft ARM (*armasm*) émet des avertissements et des erreurs de diagnostic lorsqu’il les rencontre. Cet article décrit les messages les plus fréquemment rencontrés.

## <a name="syntax"></a>Syntaxe

> <em>nom de fichier</em>**(**<em>numéro de ligne</em>**) :** \[  | **Avertissement** **d'** erreur]<em>nombre</em>**:** *message*

## <a name="diagnostic-messages---errors"></a>Messages de diagnostic-Erreurs

> A2193 : cette instruction génère un comportement imprévisible

L’architecture ARM ne peut pas garantir ce qui se passe lorsque cette instruction est exécutée.  Pour plus d’informations sur les formes bien définies de cette instruction, consultez le manuel de référence sur l' [architecture ARM](https://go.microsoft.com/fwlink/p/?linkid=246464).

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196 : l’instruction ne peut pas être encodée en 16 bits

L’instruction spécifiée ne peut pas être encodée en tant qu’instruction Thumb 16 bits.  Spécifiez une instruction 32 bits ou réorganisez le code pour amener l’étiquette cible dans la plage d’une instruction de 16 bits.

L’assembleur peut tenter d’encoder une branche en 16 bits et échouer avec cette erreur, même si une branche 32 bits est encodable. Vous pouvez résoudre ce problème en utilisant le `.W` spécificateur pour marquer explicitement la branche comme 32 bits.

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202 : syntaxe des instructions de préconfiguration non autorisée dans une zone de défilement

Le code Thumb doit utiliser la syntaxe Unified assembler.  L’ancienne syntaxe n’est plus acceptée

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513 : la rotation doit être paire

En mode ARM, il existe une autre syntaxe pour spécifier des constantes.  Au lieu d’écrire `#<const>` , vous pouvez écrire `#<byte>,#<rot>` , qui représente la valeur de constante obtenue en faisant pivoter la valeur `<byte>` de droite par `<rot>` .  Lorsque vous utilisez cette syntaxe, vous devez définir la valeur de `<rot>` pair.

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557 : nombre d’octets incorrect pour l’écriture différée

Sur les instructions de chargement et de stockage de la structure néon ( `VLDn` , `VSTn` ), il existe une autre syntaxe pour spécifier l’écriture différée dans le registre de base.  Au lieu de placer un point d’exclamation ( !) après l’adresse, vous pouvez spécifier une valeur immédiate qui indique le décalage à ajouter au registre de base.  Si vous utilisez cette syntaxe, vous devez spécifier le nombre exact d’octets qui ont été chargés ou stockés par l’instruction.

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>Messages de diagnostic-avertissements

> A4228 : la valeur d’alignement dépasse l’alignement de zone ; alignement non garanti

L’alignement spécifié dans une `ALIGN` directive est supérieur à l’alignement du englobant `AREA` .  Par conséquent, l’assembleur ne peut pas garantir que la `ALIGN` directive sera respectée.

Pour résoudre ce problème, vous pouvez spécifier sur la `AREA` directive un `ALIGN` attribut qui est supérieur ou égal à l’alignement souhaité.

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508 : l’utilisation de cette constante pivotée est déconseillée

En mode ARM, il existe une autre syntaxe pour spécifier des constantes.  Au lieu d’écrire `#<const>` , vous pouvez écrire `#<byte>,#<rot>` , qui représente la valeur de constante obtenue en faisant pivoter la valeur `<byte>` de droite par `<rot>` .  Dans certains contextes, ARM a déconseillé l’utilisation de ces constantes pivotées. Dans ce cas, utilisez plutôt la `#<const>` syntaxe de base.

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509 : cette forme d’instruction conditionnelle est dépréciée

Cette forme d’instruction conditionnelle a été dépréciée par ARM dans l’architecture ARMv8. Nous vous recommandons de modifier le code pour qu’il utilise des branches conditionnelles. Pour connaître les instructions conditionnelles toujours prises en charge, consultez le manuel de référence sur l' [architecture ARM](https://go.microsoft.com/fwlink/p/?linkid=246464).

Cet avertissement n’est pas émis lorsque le commutateur de ligne de commande **-oldit** est utilisé.

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>Voir aussi

[Référence Command-Line assembly ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Directives de l’assembleur ARM](../../assembler/arm/arm-assembler-directives.md)<br/>
