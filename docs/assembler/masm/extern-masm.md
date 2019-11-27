---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: fc66338d90b54ecb12ef3ab1aa56214fb445cb13
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397561"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Définit une ou plusieurs variables externes, étiquettes ou symboles appelés *Name* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> **Extern** ⟦*Language-type*⟧ *Name* ⟦ __(__ *ALTID* __)__ ⟧ __:__ *type* ⟦ __,__ ⟦*Language-type*⟧ *Name* ⟦ __(__ *ALTID* __)__ ⟧ __:__ *type* ... ⟧

## <a name="remarks"></a>Notes

Le *type* peut être [ABS](../../assembler/masm/operator-abs.md), qui importe le *nom* en tant que constante. Identique à [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
