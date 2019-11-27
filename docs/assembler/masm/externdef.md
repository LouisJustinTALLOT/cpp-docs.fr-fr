---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 469b49832c171ee78336a0c457f0d269acd3b59d
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397539"
---
# <a name="externdef"></a>EXTERNDEF

Définit une ou plusieurs variables externes, étiquettes ou symboles appelés *Name* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> **EXTERNDEF** ⟦*Language-type*⟧ __:__ *type* ⟦ __,__ ⟦*Language-type*⟧ *nom* __:__ *type* ... ⟧

## <a name="remarks"></a>Notes

Si le *nom* est défini dans le module, il est traité comme [public](../../assembler/masm/public-masm.md). Si le *nom* est référencé dans le module, il est traité comme [extern](../../assembler/masm/extern-masm.md). Si le *nom* n’est pas référencé, il est ignoré. Le *type* peut être [ABS](../../assembler/masm/operator-abs.md), qui importe le *nom* en tant que constante. Normalement utilisé dans les fichiers include.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
