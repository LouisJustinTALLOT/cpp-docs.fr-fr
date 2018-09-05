---
title: IF (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0cce834924f7fc147b1ef301d5bd345dfd2973
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685305"
---
# <a name="if-masm"></a>IF (MASM)

Accorde l’assembly de *ifstatements* si *expression1* a la valeur true (différent de zéro) ou *elseifstatements* si *expression1* a la valeur false (0) et *expression2* a la valeur true.

## <a name="syntax"></a>Syntaxe

> IF *expression1*<br/>
> *ifstatements*<br/>
> [[ELSEIF *expression2*<br/>
> *elseifstatements*]]<br/>
> [[ELSE<br/>
> *qu’elsestatements*]]<br/>
> ENDIF

## <a name="remarks"></a>Notes

Les directives suivantes peuvent être remplacés par [ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI** , **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**, et **ELSEIFNDEF** . Si vous le souhaitez, assemble *qu’elsestatements* si l’expression précédente a la valeur false. Notez que les expressions sont évaluées au moment de l’assembly.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>