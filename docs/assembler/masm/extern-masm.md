---
title: EXTERN (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9008e8c1153c0a9b06530b14e661436f7e62a9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693668"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Définit une ou plusieurs variables externes, des étiquettes ou des symboles appelés *nom* dont le type est *type*.

## <a name="syntax"></a>Syntaxe

> EXTERN [[*langtype*]] *nom* [[(*altid*)]] : *type* [[, [[*langtype*]]  *nom* [[(*altid*)]] : *type*]]...

## <a name="remarks"></a>Notes

Le *type* peut être [ABS](../../assembler/masm/operator-abs.md), qui importe *nom* en tant que constante. Identique à [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>