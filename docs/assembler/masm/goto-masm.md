---
title: GOTO (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0be678e2d39389cbc551c386c1890f799124b5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43694004"
---
# <a name="goto-masm"></a>GOTO (MASM)

Transfère un assembly à la ligne marquée **:**_macrolabel_.

## <a name="syntax"></a>Syntaxe

> **GOTO** *macrolabel*

## <a name="remarks"></a>Notes

**GOTO** est autorisé uniquement à l’intérieur de [MACRO](macro.md), [pour](for-masm.md), [FICHI](forc.md), [RÉPÉTEZ](repeat.md), et [lors de la](while-masm.md)blocs. Le *macrolabel* cible doit être la seule directive sur la ligne et doit être précédée d’un signe deux-points de début.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>
