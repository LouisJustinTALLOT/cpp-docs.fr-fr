---
title: Informations de référence sur les opérateurs MASM
ms.date: 07/15/2020
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: db79473f5d4264b869eeac334fa7957cfe553364
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830941"
---
# <a name="masm-operators-reference"></a>Informations de référence sur les opérateurs MASM

## <a name="arithmetic"></a>Arithmétique

:::row:::
   :::column span="":::
      [`*` multiplier](operator-multiply.md)\
      [`+` complémentaires](operator-add.md)\
      [`-` (soustraction ou négation)](operator-subtract-2.md)
   :::column-end:::
   :::column span="":::
      [`.` case](operator-dot.md)\
      [`/` diviser](operator-subtract-1.md)
   :::column-end:::
   :::column span="":::
      [`[]` évaluer](operator-brackets.md)\
      [`MOD` sections](operator-mod.md)
   :::column-end:::
:::row-end:::

## <a name="control-flow"></a>Flux de contrôle

:::row:::
   :::column span="":::
      [`!` (non logique du Runtime)](operator-logical-not-masm-run-time.md)\
      [`!=` (Runtime non égal)](operator-not-equal-masm.md)\
      [`||` (ou logique Runtime)](operator-logical-or.md)\
      [`&&` (and logique Runtime)](operator-logical-and-masm-run-time.md)\
      [`<` (Runtime inférieur à)](operator-less-than-masm-run-time.md)
   :::column-end:::
   :::column span="":::
      [`<=` (le runtime est inférieur ou égal à)](operator-less-or-equal-masm-run-time.md)\
      [`==` (égal à l’exécution)](operator-equal-masm-run-time.md)\
      [`>` (Runtime supérieur à)](operator-greater-than-masm-run-time.md)\
      [`>=` (version du runtime supérieure ou égale à)](operator-greater-or-equal-masm-run-time.md)\
      [`&` (and au niveau du bit au moment de l’exécution)](operator-bitwise-and.md)
   :::column-end:::
   :::column span="":::
      [`CARRY?` (test Carry du Runtime)](operator-carry-q.md)\
      [`OVERFLOW?` (test de dépassement de capacité du Runtime)](operator-overflow-q.md)\
      [`PARITY?` (test de parité du Runtime)](operator-parity-q.md)\
      [`SIGN?` (test de signature du Runtime)](operator-sign-q.md)\
      [`ZERO?` (test Zero Runtime)](operator-zero-q.md)
   :::column-end:::
:::row-end:::

## <a name="logical-and-shift"></a>Opérateur and logique

:::row:::
   :::column span="":::
      [`AND` (and au niveau du bit)](operator-and.md)\
      [`NOT` (not au niveau du bit)](operator-not.md)
   :::column-end:::
   :::column span="":::
      [`OR` (opérateur or au niveau du bit)](operator-or.md)\
      [`SHL` (décalage vers la gauche)](operator-shl.md)
   :::column-end:::
   :::column span="":::
      [`SHR` (décalage des bits vers la droite)](operator-shr.md)\
      [`XOR` (or exclusif au niveau du bit)](operator-xor.md)
   :::column-end:::
:::row-end:::

## <a name="macro"></a>Macro

:::row:::
   :::column span="":::
      [`!` (caractère littéral)](operator-logical-not-masm.md)\
      [`%` (traiter en tant que texte)](operator-percent.md)
   :::column-end:::
   :::column span="":::
      [`;;` (considérer comme commentaire)](operator-semicolons.md)\
      [`< >` (considérer comme un littéral)](operator-literal.md)
   :::column-end:::
   :::column span="":::
      [`& &` (remplacer la valeur de paramètre)](operator-logical-and-masm.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>Divers

:::row:::
   :::column span="":::
      [`' '` (traiter en tant que chaîne)](operator-single-quote.md)\
      [`" "` (traiter en tant que chaîne)](operator-double-quote.md)\
      `:` (définition d’étiquette locale)
   :::column-end:::
   :::column span="":::
      `::` (inscrire segment et décalage) \
      `::` (définition d’étiquette globale)
   :::column-end:::
   :::column span="":::
      [`;` (considérer comme commentaire)](operator-semicolon.md)\
      [`DUP` (déclaration de répétition)](operator-dup.md)
   :::column-end:::
:::row-end:::

## <a name="record"></a>Enregistrement

:::row:::
   :::column span="":::
      [`MASK` (Obtient le masque de réenregistrement ou le champ)](operator-mask.md)
   :::column-end:::
   :::column span="2":::
      [`WIDTH` (Obtient l’enregistrement ou la largeur du champ)](operator-width.md)
   :::column-end:::
:::row-end:::

## <a name="relational"></a>Relationnel

:::row:::
   :::column span="":::
      [`EQ` valeur](operator-eq.md)\
      [`GE` (supérieur ou égal à)](operator-ge.md)
   :::column-end:::
   :::column span="":::
      [`GT` (supérieur à)](operator-gt.md)\
      [`LE` (inférieur ou égal à)](operator-le.md)
   :::column-end:::
   :::column span="":::
      [`LT` (inférieur à)](operator-lt.md)\
      [`NE` (différent de)](operator-ne.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>Segment

:::row:::
   :::column span="":::
      [`:` (remplacement de segment)](operator-colon.md)\
      `::` (inscrire segment et décalage) \
      [`IMAGEREL` (décalage relatif de l’image)](operator-imagerel.md)
   :::column-end:::
   :::column span="":::
      [`LROFFSET` (décalage résolu du chargeur)](operator-lroffset.md)\
      [`OFFSET` (décalage relatif du segment)](operator-offset.md)
   :::column-end:::
   :::column span="":::
      [`SECTIONREL` (décalage relatif de la section)](operator-sectionrel.md)\
      [`SEG` (Obtient le segment)](operator-seg.md)
   :::column-end:::
:::row-end:::

## <a name="type"></a>Type

:::row:::
   :::column span="":::
      [`HIGH` (8 bits de poids fort des 16 bits les plus bas)](operator-high.md)\
      [`HIGH32` (32 bits de 64 bits)](operator-high32.md)\
      [`HIGHWORD` (16 bits de poids fort de 32 bits de poids faible)](operator-highword.md)\
      [`LENGTH` (nombre d’éléments dans un tableau)](operator-length.md)\
      [`LENGTHOF` (nombre d’éléments dans un tableau)](operator-lengthof.md)\
      [`LOW` (8 bits de poids faible)](operator-low.md)
   :::column-end:::
   :::column span="":::
      [`LOW32` (32 bits bas)](operator-low32.md)\
      [`LOWWORD` (16 bits de poids faible)](operator-lowword.md)\
      [`OPATTR` (Obtient les informations sur le type d’argument)](operator-opattr.md)\
      [`PTR` (pointeur vers ou en tant que type)](operator-ptr.md)\
      [`SHORT` (marquer le type d’étiquette abrégée)](operator-short.md)
   :::column-end:::
   :::column span="":::
      [`SIZE` (taille du type ou de la variable)](operator-size.md)\
      [`SIZEOF` (taille du type ou de la variable)](operator-sizeof.md)\
      [`THIS` (emplacement actuel)](operator-this.md)\
      [`TYPE` (Obtient le type d’expression)](operator-type.md)\
      [`.TYPE` (Obtient les informations sur le type d’argument)](operator-dot-type.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi

[Référence de Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
