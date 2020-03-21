---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: ba1377359ba9bc960e5d7d2a55df15adfe0d5d33
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076221"
---
# <a name="invoke"></a>INVOKE

(uniquement MASM 32 bits.) Appelle la procédure à l’adresse donnée par l' *expression*, en passant les arguments sur la pile ou dans les registres en fonction des conventions d’appel standard du type de langage.

## <a name="syntax"></a>Syntaxe

> **Appeler** l' *expression* ⟦ __,__ *argument* ... ⟧

## <a name="remarks"></a>Notes

Chaque argument passé à la procédure peut être une expression, une paire de registres ou une expression d’adresse (une expression précédée de **addr**).

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
