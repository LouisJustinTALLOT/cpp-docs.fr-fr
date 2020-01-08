---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 23c6b0aefae856da449da574669e8475122c7556
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312948"
---
# <a name="macro"></a>MACRO

Marque un bloc de macro appelé *Name* et établit des espaces réservés de *paramètre* pour les arguments passés lorsque la macro est appelée.

## <a name="syntax"></a>Syntaxe

> *nom*de la**macro** ⟦*paramètre* ⟦ **: req** | : =*valeur par défaut* | *arguments* **: vararg**⟧... ⟧\
> *instructions*\
⟦**Goto** :*macrolabelId*⟧ \
> ⟦**Exit**⟧ \
> **ENDM** ⟦*valeur*⟧

## <a name="remarks"></a>Notes

Une fonction macro retourne une *valeur* à l’instruction appelante.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Goto (MASM)](goto-masm.md)\
[ENDM](endm.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)

