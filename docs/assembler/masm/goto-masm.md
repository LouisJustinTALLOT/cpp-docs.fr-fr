---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: a03cbda5a8ff64f6c167766f416e7744a5382ad5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203078"
---
# <a name="goto-masm"></a>GOTO (MASM)

Transfère un assembly à la ligne marquée **:**_macrolabel_.

## <a name="syntax"></a>Syntaxe

> **GOTO** *macrolabel*

## <a name="remarks"></a>Notes

**GOTO** est autorisé uniquement à l’intérieur de [MACRO](macro.md), [pour](for-masm.md), [FICHI](forc.md), [RÉPÉTEZ](repeat.md), et [lors de la](while-masm.md)blocs. Le *macrolabel* cible doit être la seule directive sur la ligne et doit être précédée d’un signe deux-points de début.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>
