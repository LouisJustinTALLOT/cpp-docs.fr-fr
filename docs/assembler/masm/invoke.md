---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 853bc9cd22d866357a4cd2d695beccc3efc20acf
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703959"
---
# <a name="invoke-32-bit-masm"></a>INVOKE (MASM 32 bits)

Appelle la procédure à l’adresse donnée par l' *expression*, en passant les arguments sur la pile ou dans les registres en fonction des conventions d’appel standard du type de langage. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> INVOKE, *expression* [[, *arguments*]]

## <a name="remarks"></a>Notes

Chaque argument passé à la procédure peut être une expression, une paire de registres ou une expression d’adresse (une expression précédée de `ADDR`).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>