---
description: 'En savoir plus sur : EXTERN'
title: EXTERN (MASM)
ms.date: 12/06/2019
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 354a390a16fb663dc6e907e37022a362c3ab5648
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97130349"
---
# <a name="extern"></a>EXTERN

Définit une ou plusieurs variables externes, étiquettes ou symboles appelés *Name* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> **Extern** ⟦*Language-type*⟧ *Name* ⟦ __(__*ALTID*__)__ ⟧ __:__ *type* ⟦__,__ ⟦*Language-type*⟧ *Name* ⟦ __(__*ALTID*__)__ ⟧ __:__ *type* ... ⟧

## <a name="remarks"></a>Notes

L’argument de *type Language* est valide uniquement dans MASM 32 bits.

Le *type* peut être [ABS](operator-abs.md), qui importe le *nom* en tant que constante. Identique à [EXTRN](extrn.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
