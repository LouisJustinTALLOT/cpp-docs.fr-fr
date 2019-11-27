---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 424ff295fe37e7c5ff02897a01b99a7c75876f85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397482"
---
# <a name="goto-masm"></a>GOTO (MASM)

Transfère l’assembly à la ligne marquée **:** _macrolabel_.

## <a name="syntax"></a>Syntaxe

> **Goto** *macrolabel*

## <a name="remarks"></a>Notes

**Goto** n’est autorisé que dans [les](for-masm.md)blocs [macro](macro.md), for, [fichi](forc.md), [REPEAT](repeat.md)et [while](while-masm.md) . La cible *macrolabel* doit être la seule directive sur la ligne et doit être précédée d’un signe deux-points de début.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
