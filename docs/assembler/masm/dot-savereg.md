---
title: . SAVEREG | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAVEREG
dev_langs:
- C++
helpviewer_keywords:
- .SAVEREG directive
ms.assetid: 1dbc2ef6-a197-40e7-9e55-fddcae8cef29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7010664cd2e80841d9e35d8fcf72d195cecf796
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688987"
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