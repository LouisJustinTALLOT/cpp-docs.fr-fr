---
description: 'En savoir plus sur : MACRO'
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 5410357e76d28cddd54f3c90a34d3e85b8629143
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129738"
---
# <a name="macro"></a>MACRO

Marque un bloc de macro appelé *Name* et établit des espaces réservés de *paramètre* pour les arguments passés lorsque la macro est appelée.

## <a name="syntax"></a>Syntaxe

> *nom* de la **macro** ⟦*paramètre* ⟦**: req** | : =*arguments par défaut*  |   **: vararg**⟧... ⟧\  
> *publication*\
⟦**Goto** :*macrolabelId*⟧ \
> ⟦**Exit**⟧ \
> **ENDM** ⟦*valeur*⟧

## <a name="remarks"></a>Notes

Une fonction macro retourne une *valeur* à l’instruction appelante.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[GOTO (MASM)](goto-masm.md)\
[ENDM](endm.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
