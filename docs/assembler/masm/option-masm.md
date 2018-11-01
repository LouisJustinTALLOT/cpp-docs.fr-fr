---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: a8215bf1f816baa490a768fb2cab0b3c2e53e20b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596480"
---
# <a name="option-masm"></a>OPTION (MASM)

Active et désactive les fonctionnalités de l’assembleur.

## <a name="syntax"></a>Syntaxe

> OPTION *optionlist*

## <a name="remarks"></a>Notes

Les options disponibles sont les suivantes :

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**ÉMULATEUR**|
|**NOEMULATOR**|**ÉPILOGUE**|**EXPR16**|**EXPR32**|
|**LANGAGE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**DÉCALAGE**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGUE**|**EN LECTURE SEULE**|**NOREADONLY**|
|**ÉTENDUE**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|

La syntaxe de langage est **OPTION LANGUAGE :**<em>x</em>, où *x* est un des C, SYSCALL, STDCALL, PASCAL, FORTRAN ou BASIC.  SYSCALL, PASCAL, FORTRAN et BASIC ne sont pas pris en charge avec utilisé avec [. MODÈLE](../../assembler/masm/dot-model.md) plat.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>