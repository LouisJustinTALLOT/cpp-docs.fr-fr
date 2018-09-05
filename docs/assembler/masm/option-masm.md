---
title: OPTION (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09db749baf09525957faaf8af99434cc9775d0e7
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678043"
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