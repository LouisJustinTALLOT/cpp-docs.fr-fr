---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 30d1b3ae7c6676aeb97b91c7627da859525b9ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497355"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Définit une ou plusieurs variables externes, des étiquettes ou des symboles appelés *nom* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> EXTERN [[*langtype*]] *nom* [[(*altid*)]] : *type* [[, [[*langtype*]]  *nom* [[(*altid*)]] : *type*]]...

## <a name="remarks"></a>Notes

Le *type* peut être [ABS](../../assembler/masm/operator-abs.md), qui importe *nom* en tant que constante. Identique à [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>