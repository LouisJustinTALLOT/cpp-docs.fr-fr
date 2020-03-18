---
title: EXTERN (MASM)
ms.date: 12/06/2019
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 2674f358fe22f74c5272d90a0d8cbff234ddcd11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440887"
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
