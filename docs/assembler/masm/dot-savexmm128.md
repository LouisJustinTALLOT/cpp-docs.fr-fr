---
title: . SAVEXMM128 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAVEXMM128
dev_langs:
- C++
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d44855d3449000c588f7e840753bd734af4b1af
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689905"
---
# <a name="savexmm128"></a>.SAVEXMM128

Génère soit un `UWOP_SAVE_XMM128` ou un `UWOP_SAVE_XMM128_FAR` de déroulement d’entrée du code pour le registre XMM spécifié et le décalage à l’aide de l’offset de prologue actuel. MASM choisira l’encodage le plus efficace.

## <a name="syntax"></a>Syntaxe

> .savexmm128 xmmreg, offset

## <a name="remarks"></a>Notes

. SAVEXMM128 permet aux utilisateurs de ml64.exe spécifier comment se déroule une fonction de frame et est autorisée uniquement dans le prologue, qui s’étend de la [PROC](../../assembler/masm/proc.md) déclaration FRAME pour le [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directive. Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata`. . SAVEXMM128 doit être précédé d’instructions qui implémentent les actions pour être déroulée. Il est conseillé pour encapsuler les directives de déroulement et le code qu’ils sont destinés à déroulement dans une macro pour garantir l’accord.

*décalage* doit être un multiple de 16.

Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>