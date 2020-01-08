---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: a74a5336e626f561f1fc61e866792ce193332d84
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316536"
---
# <a name="assume"></a>ASSUME

Active la vérification des erreurs pour les valeurs de registre. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **Supposons que**  *segregister* __:__ *Name* ⟦ __,__ *segregister* __:__ *Name*... ⟧\
> **Supposons que**  *dataregister* __:__ *type* ⟦ __,__ *dataregister* __:__ *type*... ⟧\
> **Supposer que**  *Register* __: Error__ ⟦ __,__ *Register* __: erreur__... ⟧\
> **Supposons que** ⟦*Register* __:__ ⟧**Nothing** ⟦ __,__ *Register* __: Nothing__... ⟧

## <a name="remarks"></a>Notes

Une fois **que l’hypothèse** est mise en vigueur, l’assembleur surveille les modifications apportées aux valeurs des registres donnés. **Error** génère une erreur si le Registre est utilisé. **Rien ne** supprime la vérification des erreurs du Registre. Vous pouvez combiner différents genres d’hypothèses dans une instruction.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
