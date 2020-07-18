---
title: Informations de référence sur les opérateurs MASM
ms.date: 07/15/2020
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c29b173a1dcf29c297e41f136044599fbd5218a5
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446461"
---
# <a name="masm-operators-reference"></a>Informations de référence sur les opérateurs MASM

## <a name="arithmetic"></a>Arithmétique

:::row:::
   :::column span="":::
      [`*`multiplier](operator-multiply.md)<br/>[`+`complémentaires](operator-add.md)<br/>[`-`(soustraction ou négation)](operator-subtract-2.md)
   :::column-end:::
   :::column span="":::
      [`.`case](operator-dot.md)<br/>[`/`diviser](operator-subtract-1.md)
   :::column-end:::
   :::column span="":::
      [`[]`évaluer](operator-brackets.md)<br/>[`MOD`sections](operator-mod.md)
   :::column-end:::
:::row-end:::

## <a name="control-flow"></a>Flux de contrôle

:::row:::
   :::column span="":::
      [`!`(non logique du Runtime)](operator-logical-not-masm-run-time.md)<br/>[`!=`(Runtime non égal)](operator-not-equal-masm.md)<br/>[`||`(ou logique Runtime)](operator-logical-or.md)<br/>[`&&`(and logique Runtime)](operator-logical-and-masm-run-time.md)<br/>[`<`(Runtime inférieur à)](operator-less-than-masm-run-time.md)
   :::column-end:::
   :::column span="":::
      [`<=`(le runtime est inférieur ou égal à)](operator-less-or-equal-masm-run-time.md)<br/>[`==`(égal à l’exécution)](operator-equal-masm-run-time.md)<br/>[`>`(Runtime supérieur à)](operator-greater-than-masm-run-time.md)<br/>[`>=`(version du runtime supérieure ou égale à)](operator-greater-or-equal-masm-run-time.md)<br/>[`&`(and au niveau du bit au moment de l’exécution)](operator-bitwise-and.md)
   :::column-end:::
   :::column span="":::
      [`CARRY?`(test Carry du Runtime)](operator-carry-q.md)<br/>[`OVERFLOW?`(test de dépassement de capacité du Runtime)](operator-overflow-q.md)<br/>[`PARITY?`(test de parité du Runtime)](operator-parity-q.md)<br/>[`SIGN?`(test de signature du Runtime)](operator-sign-q.md)<br/>[`ZERO?`(test Zero Runtime)](operator-zero-q.md)
   :::column-end:::
:::row-end:::

## <a name="logical-and-shift"></a>Opérateur and logique

:::row:::
   :::column span="":::
      [`AND`(and au niveau du bit)](operator-and.md)<br/>[`NOT`(not au niveau du bit)](operator-not.md)
   :::column-end:::
   :::column span="":::
      [`OR`(opérateur or au niveau du bit)](operator-or.md)<br/>[`SHL`(décalage vers la gauche)](operator-shl.md)
   :::column-end:::
   :::column span="":::
      [`SHR`(décalage des bits vers la droite)](operator-shr.md)<br/>[`XOR`(or exclusif au niveau du bit)](operator-xor.md)
   :::column-end:::
:::row-end:::

## <a name="macro"></a>Macro

:::row:::
   :::column span="":::
      [`!`(caractère littéral)](operator-logical-not-masm.md)<br/>[`%`(traiter en tant que texte)](operator-percent.md)
   :::column-end:::
   :::column span="":::
      [`;;`(considérer comme commentaire)](operator-semicolons.md)<br/>[`< >`(considérer comme un littéral)](operator-literal.md)
   :::column-end:::
   :::column span="":::
      [`& &`(remplacer la valeur de paramètre)](operator-logical-and-masm.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>Divers

:::row:::
   :::column span="":::
      [`' '`(traiter en tant que chaîne)](operator-single-quote.md)<br/>[`" "`(traiter en tant que chaîne)](operator-double-quote.md)<br/>`:`(définition d’étiquette locale)
   :::column-end:::
   :::column span="":::
      `::`(inscrire segment et décalage)<br/>`::`(définition d’étiquette globale)
   :::column-end:::
   :::column span="":::
      [`;`(considérer comme commentaire)](operator-semicolon.md)<br/>[`DUP`(déclaration de répétition)](operator-dup.md)
   :::column-end:::
:::row-end:::

## <a name="record"></a>Enregistrement

:::row:::
   :::column span="":::
      [`MASK`(Obtient le masque de réenregistrement ou le champ)](operator-mask.md)
   :::column-end:::
   :::column span="2":::
      [`WIDTH`(Obtient l’enregistrement ou la largeur du champ)](operator-width.md)
   :::column-end:::
:::row-end:::

## <a name="relational"></a>Relationnel

:::row:::
   :::column span="":::
      [`EQ`valeur](operator-eq.md)<br/>[`GE`(supérieur ou égal à)](operator-ge.md)
   :::column-end:::
   :::column span="":::
      [`GT`(supérieur à)](operator-gt.md)<br/>[`LE`(inférieur ou égal à)](operator-le.md)
   :::column-end:::
   :::column span="":::
      [`LT`(inférieur à)](operator-lt.md)<br/>[`NE`(différent de)](operator-ne.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>Segment

:::row:::
   :::column span="":::
      [`:`(remplacement de segment)](operator-colon.md)<br/>`::`(inscrire segment et décalage)<br/>[`IMAGEREL`(décalage relatif de l’image)](operator-imagerel.md)
   :::column-end:::
   :::column span="":::
      [`LROFFSET`(décalage résolu du chargeur)](operator-lroffset.md)<br/>[`OFFSET`(décalage relatif du segment)](operator-offset.md)
   :::column-end:::
   :::column span="":::
      [`SECTIONREL`(décalage relatif de la section)](operator-sectionrel.md)<br/>[`SEG`(Obtient le segment)](operator-seg.md)
   :::column-end:::
:::row-end:::

## <a name="type"></a>Type

:::row:::
   :::column span="":::
      [`HIGH`(8 bits de poids fort des 16 bits les plus bas)](operator-high.md)<br/>[`HIGH32`(32 bits de 64 bits)](operator-high32.md)<br/>[`HIGHWORD`(16 bits de poids fort de 32 bits de poids faible)](operator-highword.md)<br/>[`LENGTH`(nombre d’éléments dans un tableau)](operator-length.md)<br/>[`LENGTHOF`(nombre d’éléments dans un tableau)](operator-lengthof.md)<br/>[`LOW`(8 bits de poids faible)](operator-low.md)
   :::column-end:::
   :::column span="":::
      [`LOW32`(32 bits bas)](operator-low32.md)<br/>[`LOWWORD`(16 bits de poids faible)](operator-lowword.md)<br/>[`OPATTR`(Obtient les informations sur le type d’argument)](operator-opattr.md)<br/>[`PTR`(pointeur vers ou en tant que type)](operator-ptr.md)<br/>[`SHORT`(marquer le type d’étiquette abrégée)](operator-short.md)
   :::column-end:::
   :::column span="":::
      [`SIZE`(taille du type ou de la variable)](operator-size.md)<br/>[`SIZEOF`(taille du type ou de la variable)](operator-sizeof.md)<br/>[`THIS`(emplacement actuel)](operator-this.md)<br/>[`TYPE`(Obtient le type d’expression)](operator-type.md)<br/>[`.TYPE`(Obtient les informations sur le type d’argument)](operator-dot-type.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi

[Référence de Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
