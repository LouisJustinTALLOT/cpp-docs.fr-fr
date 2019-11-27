---
title: Informations de référence sur les opérateurs MASM
ms.date: 08/30/2018
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: 5295307ad668b76e5ff39882ce2613f2042f914a
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395214"
---
# <a name="masm-operators-reference"></a>Informations de référence sur les opérateurs MASM

## <a name="arithmetic"></a>Arithmétique

||||
|-|-|-|
|[* (multiplier)](operator-multiply.md)|[+ (ajouter)](operator-add.md)|[-(soustraction ou négation)](operator-subtract-2.md)|
|[. case](operator-dot.md)|[/(Division)](operator-subtract-1.md)|[&#91;&#93;évaluer](operator-brackets.md)|
|[MOD (reste)](operator-mod.md)|||

## <a name="control-flow"></a>Flux de contrôle

||||
|-|-|-|
|[\! (non logique du Runtime)](operator-logical-not-masm-run-time.md)|[\!= (Runtime non égal)](operator-not-equal-masm.md)|[&#124;&#124;(ou logique Runtime)](operator-logical-or.md)|
|[& & (and logique Runtime)](operator-logical-and-masm-run-time.md)|[< (Runtime inférieur à)](operator-less-than-masm-run-time.md)|[\<= (Runtime inférieur ou égal à)](operator-less-or-equal-masm-run-time.md)|
|[= = (égal à l’exécution)](operator-equal-masm-run-time.md)|[> (Runtime supérieur à)](operator-greater-than-masm-run-time.md)|[> = (version du runtime supérieure ou égale à)](operator-greater-or-equal-masm-run-time.md)|
|[& (Runtime and au niveau du bit)](operator-bitwise-and.md)|||
|[EMPORTER? (test Carry du Runtime)](operator-carry-q.md)|[SURCHARGE? (test de dépassement de capacité du Runtime)](operator-overflow-q.md)|[PARITÉ? (test de parité du Runtime)](operator-parity-q.md)|
|[EXPÉDITEUR? (test de signature du Runtime)](operator-sign-q.md)|[NULS? (test Zero Runtime)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>Opérateur and logique

||||
|-|-|-|
|[AND (and au niveau du bit)](operator-and.md)|[NOT (opérateur or au niveau du bit)](operator-not.md)|[OU (opérateur or au niveau du bit)](operator-or.md)|
|[SHL (décalage de bits vers la gauche)](operator-shl.md)|[SHR (décalage des bits vers la droite)](operator-shr.md)|[XOR (or exclusif au niveau du bit)](operator-xor.md)|

## <a name="macro"></a>Macro

||||
|-|-|-|
|[\! (littéral de caractère)](operator-logical-not-masm.md)|[% (traiter en tant que texte)](operator-percent.md)||
|[;; (considérer comme commentaire)](operator-semicolons.md)|[&lt; &gt; (considérer comme un littéral)](operator-literal.md)|[& & (valeur de paramètre de substitution)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>Divers

||||
|-|-|-|
|[' ' (traiter en tant que chaîne)](operator-single-quote.md)|["" (traiter en tant que chaîne)](operator-double-quote.md)||
|: (définition d’étiquette locale)|:: (segment d’enregistrement et décalage)|:: (définition d’étiquette globale)|
|[; (considérer comme commentaire)](operator-semicolon.md)|[DUP (déclaration de répétition)](operator-dup.md)||

## <a name="record"></a>Enregistrement

|||
|-|-|
|[MASK (Obtient un enregistrement ou un masque de champ)](operator-mask.md)|[WIDTH (Obtient l’enregistrement ou la largeur du champ)](operator-width.md)|

## <a name="relational"></a>Relation

||||
|-|-|-|
|[EQ (égal à)](operator-eq.md)|[GE (supérieur ou égal à)](operator-ge.md)|[GT (supérieur à)](operator-gt.md)|
|[LE (inférieur ou égal à)](operator-le.md)|[LT (inférieur à)](operator-lt.md)|[Ne (pas égal à)](operator-ne.md)|

## <a name="segment"></a>partie

|||
|-|-|
|[: (remplacement de segment)](operator-colon.md)|:: (segment d’enregistrement et décalage)|
|[IMAGEREL, (décalage relatif de l’image)](operator-imagerel.md)|[LROFFSET, (décalage résolu du chargeur)](operator-lroffset.md)|
|[OFFSET (décalage relatif du segment)](operator-offset.md)|[SECTIONREL, (décalage relatif de la section)](operator-sectionrel.md)|
|[SEG (récupérer le segment)](operator-seg.md)||

## <a name="type"></a>Type

||||
|-|-|-|
|[ÉLEVÉ (8 bits de poids fort de 16 bits de poids faible)](operator-high.md)|[HIGH32, (haute 32 bits de 64 bits)](operator-high32.md)|[HIGHWORD, (16 bits de poids fort de 32 bits de poids faible)](operator-highword.md)|
|[LONGUEUR (nombre d’éléments dans un tableau)](operator-length.md)|[LENGTHOF, (nombre d’éléments dans un tableau)](operator-lengthof.md)|[FAIBLE (8 bits de poids faible)](operator-low.md)|
|[LOW32, (faible 32 bits)](operator-low32.md)|[LOWWORD, (16 bits de poids faible)](operator-lowword.md)|[OPATTR, (recevoir les informations sur le type d’argument)](operator-opattr.md)|
|[PTR (pointeur vers ou en tant que type)](operator-ptr.md)|[SHORT (marquer le type d’étiquette abrégée)](operator-short.md)|[TAILLE (taille du type ou de la variable)](operator-size.md)|
|[SIZEOF (taille du type ou de la variable)](operator-sizeof.md)|[THIS (emplacement actuel)](operator-this.md)|[TYPE (Obtient l’expression type)](operator-type.md)|
|[. TYPE (Obtient les informations sur le type d’argument)](operator-dot-type.md)|||

## <a name="see-also"></a>Voir aussi

[Informations de référence sur Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)<br/>
