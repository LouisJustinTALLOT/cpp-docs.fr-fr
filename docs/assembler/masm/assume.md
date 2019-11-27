---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: 73ef8bcc33087a56747b80f94482fcd6c50e3bf6
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399264"
---
# <a name="assume-32-bit-masm"></a>SUPPOSER (32-bit MASM)

Active la vérification des erreurs pour les valeurs de registre. (uniquement MASM 32 bits.)

## <a name="syntax"></a>Syntaxe

> **Supposons que**  *segregister* __:__ *Name* ⟦ __,__ *segregister* __:__ *Name*... ⟧\
> **Supposons que**  *dataregister* __:__ *type* ⟦ __,__ *dataregister* __:__ *type*... ⟧\
> **Supposer que**  *Register* __: Error__ ⟦ __,__ *Register* __: erreur__... ⟧\
> **Supposons que** ⟦*Register* __:__ ⟧**Nothing** ⟦ __,__ *Register* __: Nothing__... ⟧

## <a name="remarks"></a>Notes

Une fois **que l’hypothèse** est mise en vigueur, l’assembleur surveille les modifications apportées aux valeurs des registres donnés. **Error** génère une erreur si le Registre est utilisé. **Rien ne** supprime la vérification des erreurs du Registre. Vous pouvez combiner différents genres d’hypothèses dans une instruction.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
