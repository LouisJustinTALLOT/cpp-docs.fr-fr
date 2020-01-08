---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 681c4091a3c54a781bed4b01b235dfeb04f552c6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318096"
---
# <a name="extern"></a>EXTERN

Définit une ou plusieurs variables externes, étiquettes ou symboles appelés *Name* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> **Extern** ⟦*Language-type*⟧ *Name* ⟦ __(__ *ALTID* __)__ ⟧ __:__ *type* ⟦ __,__ ⟦*Language-type*⟧ *Name* ⟦ __(__ *ALTID* __)__ ⟧ __:__ *type* ... ⟧

## <a name="remarks"></a>Notes

L’argument de *type Language* est valide uniquement dans MASM 32 bits.

Le *type* peut être [ABS](operator-abs.md), qui importe le *nom* en tant que constante. Identique à [EXTRN](extrn.md).

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
