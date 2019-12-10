---
title: EXTERN (MASM)
ms.date: 12/06/2019
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 38ea50e75f2a8e19a7a99860f691904053b6739a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987853"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Définit une ou plusieurs variables externes, étiquettes ou symboles appelés *Name* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> **Extern** ⟦*Language-type*⟧ *Name* ⟦ __(__ *ALTID* __)__ ⟧ __:__ *type* ⟦ __,__ ⟦*Language-type*⟧ *Name* ⟦ __(__ *ALTID* __)__ ⟧ __:__ *type* ... ⟧

## <a name="remarks"></a>Notes

L’argument de *type Language* est valide uniquement dans MASM 32 bits.

Le *type* peut être [ABS](../../assembler/masm/operator-abs.md), qui importe le *nom* en tant que constante. Identique à [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
