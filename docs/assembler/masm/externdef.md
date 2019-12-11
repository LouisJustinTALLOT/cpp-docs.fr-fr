---
title: EXTERNDEF
ms.date: 12/06/2019
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: e757781151bd1bb57940e5c54f7333a5daa93c74
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987898"
---
# <a name="externdef"></a>EXTERNDEF

Définit une ou plusieurs variables externes, étiquettes ou symboles appelés *Name* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> **EXTERNDEF** ⟦*Language-type*⟧ __:__ *type* ⟦ __,__ ⟦*Language-type*⟧ *nom* __:__ *type* ... ⟧

## <a name="remarks"></a>Notes

L’argument de *type Language* est valide uniquement dans MASM 32 bits.

Si le *nom* est défini dans le module, il est traité comme [public](../../assembler/masm/public-masm.md). Si le *nom* est référencé dans le module, il est traité comme [extern](../../assembler/masm/extern-masm.md). Si le *nom* n’est pas référencé, il est ignoré. Le *type* peut être [ABS](../../assembler/masm/operator-abs.md), qui importe le *nom* en tant que constante. Normalement utilisé dans les fichiers include.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
