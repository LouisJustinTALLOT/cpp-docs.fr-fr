---
title: Messages de Diagnostic assembleur ARM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1616b4bd9c4b64e771ec537a1b8cd7b582702222
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052771"
---
# <a name="arm-assembler-diagnostic-messages"></a>Messages de diagnostic de l'assembleur ARM
L’assembleur Microsoft ARM (*armasm*) émet des erreurs et des avertissements de diagnostic lorsqu’il les rencontre. Cet article décrit les messages plus courants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## <a name="diagnostic-messages"></a>Messages de diagnostic  
  
### <a name="errors"></a>Erreurs  
 A2193 : cette instruction génère un comportement imprévisible  
 L’architecture ARM ne peut pas garantir que se passe-t-il lorsque cette instruction est exécutée.  Pour plus d’informations sur les formes bien définis de cette instruction, consultez la [manuel de référence d’Architecture ARM](http://go.microsoft.com/fwlink/p/?linkid=246464).  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196 : instruction ne peut pas être encodée en 16 bits  
 L’instruction spécifiée ne peut pas être codée comme une instruction de curseur de défilement de 16 bits.  Spécifiez une instruction 32 bits ou de réorganiser le code afin que l’étiquette cible dans la plage d’une instruction de 16 bits.  
  
 L’assembleur peut essayer d’encoder une branche de 16 bits et échouer avec cette erreur, même si une branche de 32 bits est puissent être codée. Vous pouvez résoudre ce problème à l’aide de la `.W` spécificateur marquer explicitement la branche en tant que 32 bits.  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 A2202 : Syntaxe d’instruction Pre-UAL interdite dans la région du curseur de défilement  
 Code Thumb doit utiliser la syntaxe de langage unifiée de l’assembleur (UAL).  L’ancienne syntaxe n’est plus acceptée  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513 : Rotation doit être un nombre pair  
 En mode ARM, il existe une autre syntaxe pour la spécification de constantes.  Au lieu d’écrire `#<const>`, vous pouvez écrire `#<byte>,#<rot>`, qui représente la valeur de constante qui est obtenue en appliquant une rotation de la valeur `<byte>` vers la droite de `<rot>`.  Lorsque vous utilisez cette syntaxe, vous devez rendre la valeur de `<rot>` même.  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 A2557 : Le nombre Incorrect d’octets pour l’écriture différée  
 Sur la structure NEON charger et stocker des instructions (`VLDn`, `VSTn`), il existe une autre syntaxe pour la spécification de l’écriture différée pour le Registre de base.  Au lieu de placer un point d’exclamation ( !) après l’adresse, vous pouvez spécifier une valeur immédiate qui indique l’offset à ajouter à l’historique de base.  Si vous utilisez cette syntaxe, vous devez spécifier le nombre exact d’octets qui ont été chargées ou stockée par l’instruction.  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### <a name="warnings"></a>Avertissements  
 A4228 : Valeur d’alignement dépasse alignement de la zone ; alignement non garantie  
 L’alignement spécifié dans un `ALIGN` la directive est supérieure à l’alignement de la forme `AREA`.  Par conséquent, l’assembleur ne garantit pas que le `ALIGN` la directive est respectée.  
  
 Pour résoudre ce problème, vous pouvez spécifier dans le `AREA` directive une `ALIGN` attribut qui est égale ou supérieure à l’alignement souhaité.  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508 : Utilisation de cette constante paysage est déconseillée.  
 En mode ARM, il existe une autre syntaxe pour la spécification de constantes.  Au lieu d’écrire `#<const>`, vous pouvez écrire `#<byte>,#<rot>`, qui représente la valeur de constante qui est obtenue en appliquant une rotation de la valeur `<byte>` vers la droite de `<rot>`.  Dans certains contextes, ARM a déconseillé de l’utilisation de ces constantes paysage. Dans ce cas, utilisez la basic `#<const>` syntaxe à la place.  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 A4509 : Cette forme d’instruction conditionnelle est déconseillée.  
 Cette forme de l’instruction conditionnelle a été déconseillée par ARM dans l’architecture ARMv8. Nous vous recommandons de modifier le code pour utiliser des branches conditionnelles. Pour consulter les instructions conditionnelles sont toujours gérées, consultez le [manuel de référence d’Architecture ARM](http://go.microsoft.com/fwlink/p/?linkid=246464).  
  
 Cet avertissement n’est pas émis lorsque le `-oldit` commutateur de ligne de commande est utilisé.  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande de l’assembleur ARM](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [Directive d’assembleur ARM](../../assembler/arm/arm-assembler-directives.md)