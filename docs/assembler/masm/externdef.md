---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 23d34af470e825a8535de8cb28645a7bfb4c4d1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203087"
---
# <a name="externdef"></a>EXTERNDEF

Définit une ou plusieurs variables externes, des étiquettes ou des symboles appelés *nom* dont le type est `type`.

## <a name="syntax"></a>Syntaxe

> Type de nom : EXTERNDEF [[langtype]] [[, [[langtype]] : type de nom]]...

## <a name="remarks"></a>Notes

Si *nom* est défini dans le module, il est traité comme [PUBLIC](../../assembler/masm/public-masm.md). Si *nom* est référencé dans le module, il est traité comme [EXTERN](../../assembler/masm/extern-masm.md). Si *nom* est ne pas référencé, il est ignoré. Le `type` peut être [ABS](../../assembler/masm/operator-abs.md), qui importe *nom* en tant que constante. Normalement utilisé dans les fichiers include.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>