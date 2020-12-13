---
description: 'En savoir plus sur : INVOKE'
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: eb372ad3d7ccde9f217f55ed9817acfe9bd8f1cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129842"
---
# <a name="invoke"></a>INVOKE

(uniquement MASM 32 bits.) Appelle la procédure à l’adresse donnée par l' *expression*, en passant les arguments sur la pile ou dans les registres en fonction des conventions d’appel standard du type de langage.

## <a name="syntax"></a>Syntaxe

> **Appeler** l' *expression* ⟦__,__ *argument* ... ⟧

## <a name="remarks"></a>Notes

Chaque argument passé à la procédure peut être une expression, une paire de registres ou une expression d’adresse (une expression précédée de **addr**).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
