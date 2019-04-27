---
title: .SAVEXMM128
ms.date: 08/30/2018
f1_keywords:
- .SAVEXMM128
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
ms.openlocfilehash: c29ec47170c5e0f46f02d53f23ab477a79bbdc32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205217"
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