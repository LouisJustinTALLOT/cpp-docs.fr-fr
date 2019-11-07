---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 8f0388c3df9804c0cdb105162a962a44fe207345
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703319"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG ((MASM 32 bits)

Classe les segments en fonction de la Convention de segment MS-DOS : CODE First, puis segments not in DGROUP, puis segments in DGROUP. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> .DOSSEG

## <a name="remarks"></a>Notes

Les segments dans DGROUP suivent cet ordre : les segments non dans BSS ou STACK, les segments BSS et enfin les segments de pile. Principalement utilisé pour garantir la prise en charge de CodeView dans les programmes autonomes MASM. Identique à [dosseg (](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>