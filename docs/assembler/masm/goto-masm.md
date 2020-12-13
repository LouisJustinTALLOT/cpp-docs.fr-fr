---
description: 'En savoir plus sur : GOTO'
title: GOTO (MASM)
ms.date: 12/16/2019
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: ab373d77cbfb660d4cc256e39de38b7f066eac27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97130258"
---
# <a name="goto"></a>GOTO

Transfère l’assembly à la ligne marquée **:**_macrolabel_.

## <a name="syntax"></a>Syntaxe

> **Goto** *macrolabel*

## <a name="remarks"></a>Notes

**Goto** n’est autorisé que dans [les](for-masm.md)blocs [macro](macro.md), for, [fichi](forc.md), [REPEAT](repeat.md)et [while](while-masm.md) . La cible *macrolabel* doit être la seule directive sur la ligne et doit être précédée d’un signe deux-points de début.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
