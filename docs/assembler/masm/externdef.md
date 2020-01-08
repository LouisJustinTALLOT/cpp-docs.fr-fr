---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 2cc5884a7473da9175a6b6af4b4251314deffeb4
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313390"
---
# <a name="externdef"></a>EXTERNDEF

Définit une ou plusieurs variables externes, étiquettes ou symboles appelés *Name* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> **EXTERNDEF** ⟦*Language-type*⟧ __:__ *type* ⟦ __,__ ⟦*Language-type*⟧ *nom* __:__ *type* ... ⟧

## <a name="remarks"></a>Notes

L’argument de *type Language* est valide uniquement dans MASM 32 bits.

Si le *nom* est défini dans le module, il est traité comme [public](public-masm.md). Si le *nom* est référencé dans le module, il est traité comme [extern](extern-masm.md). Si le *nom* n’est pas référencé, il est ignoré. Le *type* peut être [ABS](operator-abs.md), qui importe le *nom* en tant que constante. Normalement utilisé dans les fichiers include.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
