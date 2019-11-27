---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 17edea122afc03a8c3a2fdc86ee6c06c2ccf3c85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398487"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG ((MASM 32 bits)

Classe les segments en fonction de la Convention de segment MS-DOS : CODE First, puis segments not in DGROUP, puis segments in DGROUP. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **.DOSSEG**

## <a name="remarks"></a>Notes

Les segments dans DGROUP suivent cet ordre : les segments non dans BSS ou STACK, les segments BSS et enfin les segments de pile. Principalement utilisé pour garantir la prise en charge de CodeView dans les programmes autonomes MASM. Identique à [dosseg (](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
