---
title: EXTERNDEF | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5c3d42cabb88c38ce1d98da24cd2cb4ddec8d5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683659"
---
# <a name="externdef"></a>EXTERNDEF

Définit une ou plusieurs variables externes, des étiquettes ou des symboles appelés *nom* dont le type est `type`.

## <a name="syntax"></a>Syntaxe

> Type de nom : EXTERNDEF [[langtype]] [[, [[langtype]] : type de nom]]...

## <a name="remarks"></a>Notes

Si *nom* est défini dans le module, il est traité comme [PUBLIC](../../assembler/masm/public-masm.md). Si *nom* est référencé dans le module, il est traité comme [EXTERN](../../assembler/masm/extern-masm.md). Si *nom* est ne pas référencé, il est ignoré. Le `type` peut être [ABS](../../assembler/masm/operator-abs.md), qui importe *nom* en tant que constante. Normalement utilisé dans les fichiers include.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>