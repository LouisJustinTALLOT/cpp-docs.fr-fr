---
description: En savoir plus sur :. DOSSEG ((MASM 32 bits)
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 636f3f811b20e7cf9955648c71025cfb1766fb47
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132104"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG ((MASM 32 bits)

Classe les segments en fonction de la Convention de segment MS-DOS : CODE First, puis segments not in DGROUP, puis segments in DGROUP. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **. DOSSEG (**

## <a name="remarks"></a>Notes

Les segments dans DGROUP suivent cet ordre : les segments non dans BSS ou STACK, les segments BSS et enfin les segments de pile. Principalement utilisé pour garantir la prise en charge de CodeView dans les programmes autonomes MASM. Identique à [dosseg (](dosseg.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
