---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: 0f90ab0115c3dde894d468bbbe60ffa0193b8336
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395169"
---
# <a name="option-masm"></a>OPTION (MASM)

Active et désactive les fonctionnalités de l’assembleur.

## <a name="syntax"></a>Syntaxe

> **Option** *optionlist*

## <a name="remarks"></a>Notes

Les options disponibles sont les suivantes :

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**ÉMULATEUR**|
|**NOEMULATOR**|**ÉPILOGUE**|**EXPR16**|**EXPR32**|
|**SOUS**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NoKeyword**|**NOSIGNEXTEND**|**DÉCALAGE**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**PROLOGUE**|**SEULEMENT**|**Noreadonly**|
|**ÉTENDUE**|**NOLIMITED**|**SEGMENT**|**SETIF2**.|

La syntaxe de LANGUAGE est **Language option :** <em>x</em>, où *x* est l’un des langages C, syscall, stdcall, Pascal, Fortran ou de base.  SYSCALL, PASCAL, FORTRAN et BASIC ne sont pas pris en charge avec utilisé avec [. MODÈLE](../../assembler/masm/dot-model.md) plat.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
