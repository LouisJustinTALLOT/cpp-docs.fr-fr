---
title: .SAVEREG
ms.date: 08/30/2018
f1_keywords:
- .SAVEREG
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
ms.openlocfilehash: cac7aa7f2bdbf6b60831d2beb062f86559ec0358
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178161"
---
# <a name="savereg"></a>.SAVEREG

Génère soit un `UWOP_SAVE_NONVOL` ou un `UWOP_SAVE_NONVOL_FAR` d’entrée du code pour le Registre spécifié de déroulement (`reg`) et le décalage (`offset`) à l’aide de l’offset de prologue actuel. MASM choisira l’encodage le plus efficace.

## <a name="syntax"></a>Syntaxe

> . SAVEREG reg, offset

## <a name="remarks"></a>Notes

. SAVEREG permet aux utilisateurs de ml64.exe spécifier la façon dont une fonction de frame se déroule et est autorisé uniquement dans le prologue, qui s’étend de la [PROC](../../assembler/masm/proc.md) déclaration FRAME pour le [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directive. Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata`. . SAVEREG doit être précédé d’instructions qui implémentent les actions pour être déroulée. Il est conseillé pour encapsuler les directives de déroulement et le code qu’ils sont destinés à déroulement dans une macro pour garantir l’accord.

Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>