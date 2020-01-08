---
title: OPTION (MASM)
ms.date: 12/17/2019
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: bd50ac2e051db7f02ac077054e5856524745df54
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318746"
---
# <a name="option"></a>OPTION

Active et désactive les fonctionnalités de l’assembleur.

## <a name="syntax"></a>Syntaxe

> **Option** *optionlist*

## <a name="remarks"></a>Notes

Les options disponibles sont les suivantes :

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**ÉMULATEUR**|
|**NOEMULATOR**|**ÉPILOGUE**|**EXPR16**|**EXPR32**|
|**LANGUAGE**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NoKeyword**|**NOSIGNEXTEND**|**DÉCALAGE**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGUE**|**SEULEMENT**|**Noreadonly**|
|**ÉTENDUE**|**NOLIMITED**|**SEGMENT**|**SETIF2**.|

La syntaxe de LANGUAGE est **Language option :** <em>x</em>, où *x* est l’un des langages C, syscall, stdcall, Pascal, Fortran ou de base.  SYSCALL, PASCAL, FORTRAN et BASIC ne sont pas pris en charge avec [. MODÈLE](dot-model.md) plat.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
