---
title: Référence des opérateurs MASM | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4708af3c0fa272a1ca803f549ce8953caccaa27
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688174"
---
# <a name="masm-operators-reference"></a>Référence des opérateurs MASM

## <a name="arithmetic"></a>opérations arithmétiques

||||
|-|-|-|
|[* (multiplication)](operator-multiply.md)|[+ (addition)](operator-add.md)|[-(soustraction ou nier)](operator-subtract-2.md)|
|[. (champ)](operator-dot.md)|[/ (division)](operator-subtract-1.md)|[&#91;&#93;(index)](operator-brackets.md)|
|[MODULO (reste)](operator-mod.md)|||

## <a name="control-flow"></a>Flux de contrôle

||||
|-|-|-|
|[! (not logique runtime)](operator-logical-not-masm-run-time.md)|[! = (différent de runtime)](operator-not-equal-masm.md)|[&#124;&#124;(runtime logique ou)](operator-logical-or.md)|
|[& & (runtime logique et)](operator-logical-and-masm-run-time.md)|[< (runtime inférieur à)](operator-less-than-masm-run-time.md)|[\<= (runtime inférieur ou égal à)](operator-less-or-equal-masm-run-time.md)|
|[== (égal de runtime)](operator-equal-masm-run-time.md)|[> (supérieur à l’exécution)](operator-greater-than-masm-run-time.md)|[> = (runtime supérieur ou égal à)](operator-greater-or-equal-masm-run-time.md)|
|[& (runtime au niveau du bit et)](operator-bitwise-and.md)|||
|[CARRY ? (runtime carry test)](operator-carry-q.md)|[DÉPASSEMENT DE CAPACITÉ ? (test de dépassement de capacité de runtime)](operator-overflow-q.md)|[PARITÉ ? (test de parité de runtime)](operator-parity-q.md)|
|[SE CONNECTER ? (test des signes runtime)](operator-sign-q.md)|[ZÉRO ? (test runtime zéro)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>Logique- and -Shift

||||
|-|-|-|
|[ET (au niveau du bit et)](operator-and.md)|[PAS (not au niveau du bit)](operator-not.md)|[OR (au niveau du bit ou)](operator-or.md)|
|[SHL (bits de décalage vers la gauche)](operator-shl.md)|[SHR (bits de décalage vers la droite)](operator-shr.md)|[XOR (OR exclusif ou)](operator-xor.md)|

## <a name="macro"></a>Macro

||||
|-|-|-|
|[! (littéral de caractère)](operator-logical-not-masm.md)|[% (treat sous forme de texte)](operator-percent.md)||
|[;; (traiter en tant que commentaire)](operator-semicolons.md)|[&lt; &gt; (traiter comme un littéral)](operator-literal.md)|[& & (remplacez la valeur de paramètre)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>Divers

||||
|-|-|-|
|[' ' (traiter en tant que chaîne)](operator-single-quote.md)|[« » (traiter en tant que chaîne)](operator-double-quote.md)||
|: (local définition de l’étiquette)|:: (inscrire le segment et le décalage)|:: (global définition de l’étiquette)|
|[; (traiter en tant que commentaire)](operator-semicolon.md)|[DUP (déclaration de répétition)](operator-dup.md)||

## <a name="record"></a>Enregistrement

|||
|-|-|
|[MASQUE (obtenir l’enregistrement ou de champ masque de bits)](operator-mask.md)|[LARGEUR (obtenir l’enregistrement ou de champ de la largeur)](operator-width.md)|

## <a name="relational"></a>Relation

||||
|-|-|-|
|[EQ (égal à)](operator-eq.md)|[GE (supérieur ou égal à)](operator-ge.md)|[GT (supérieur à)](operator-gt.md)|
|[LE (inférieur ou égal)](operator-le.md)|[LT (inférieur à)](operator-lt.md)|[Nou (non égal)](operator-ne.md)|

## <a name="segment"></a>Segment

|||
|-|-|
|[: (substitution de segment)](operator-colon.md)|:: (inscrire le segment et le décalage)|
|[IMAGEREL (offset relatif d’image)](operator-imagerel.md)|[LROFFSET (chargeur résolu décalage)](operator-lroffset.md)|
|[DÉCALAGE (offset relatif de segment)](operator-offset.md)|[SECTIONREL (décalage relatif de la section)](operator-sectionrel.md)|
|[SEG (segment get)](operator-seg.md)||

## <a name="type"></a>Type

||||
|-|-|-|
|[HAUTE (8 bits de poids fort 16 bits le plus bas)](operator-high.md)|[HIGH32 (32 bits de poids fort 64 bits)](operator-high32.md)|[HIGHWORD (16 bits de poids fort 32 bits les plus bas)](operator-highword.md)|
|[LONGUEUR (nombre d’éléments dans le tableau)](operator-length.md)|[LENGTHOF (nombre d’éléments dans le tableau)](operator-lengthof.md)|[FAIBLE (8 bits de poids faibles)](operator-low.md)|
|[LOW32 (basse 32 bits)](operator-low32.md)|[LOWWORD (16 bits de poids faibles)](operator-lowword.md)|[OPATTR (informations de type get argument)](operator-opattr.md)|
|[PTR (pointeur vers ou en tant que type)](operator-ptr.md)|[SHORT (type d’étiquette courts marque)](operator-short.md)|[(Taille du type ou de variable)](operator-size.md)|
|[SIZEOF (taille du type ou de variable)](operator-sizeof.md)|[(Emplacement actuel)](operator-this.md)|[TYPE (type d’expression get)](operator-type.md)|
|[. TYPE (informations de type get argument)](operator-dot-type.md)|||

## <a name="see-also"></a>Voir aussi

[Informations de référence sur Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)<br/>