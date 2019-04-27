---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 2b91698640e028bf91d822c12b85ded651a04d8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203062"
---
# <a name="if-masm"></a>IF (MASM)

Accorde l’assembly de *ifstatements* si *expression1* a la valeur true (différent de zéro) ou *elseifstatements* si *expression1* a la valeur false (0) et *expression2* a la valeur true.

## <a name="syntax"></a>Syntaxe

> IF *expression1*<br/>
> *ifstatements*<br/>
> [[ELSEIF *expression2*<br/>
> *elseifstatements*]]<br/>
> [[ELSE<br/>
> *elsestatements*]]<br/>
> ENDIF

## <a name="remarks"></a>Notes

Les directives suivantes peuvent être remplacés par [ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI**, **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**, et **ELSEIFNDEF**. Si vous le souhaitez, assemble *qu’elsestatements* si l’expression précédente a la valeur false. Notez que les expressions sont évaluées au moment de l’assembly.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>