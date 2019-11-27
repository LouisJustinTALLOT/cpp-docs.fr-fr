---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: a5175252364918ca218e81536b29f084f7fd19cc
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397300"
---
# <a name="invoke-32-bit-masm"></a>INVOKE (MASM 32 bits)

Appelle la procédure à l’adresse donnée par l' *expression*, en passant les arguments sur la pile ou dans les registres en fonction des conventions d’appel standard du type de langage. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **Appeler** l' *expression* ⟦ __,__ *argument* ... ⟧

## <a name="remarks"></a>Notes

Chaque argument passé à la procédure peut être une expression, une paire de registres ou une expression d’adresse (une expression précédée de **addr**).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
