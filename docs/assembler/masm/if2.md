---
title: IF1 et IF2
ms.date: 11/21/2019
f1_keywords:
- IF2
- IF1
helpviewer_keywords:
- IF2 directive
- IF2 directive
ms.assetid: a0f75564-b51b-4e39-ad3b-f7421e7ecad6
ms.openlocfilehash: f1b5126d9294c229d773acd29af463164bb46536
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397446"
---
# <a name="if1-and-if2"></a>IF1 et IF2

Le bloc **IF1** est évalué lors du premier passage de l’assembly.

Le bloc **IF2** est évalué à chaque passe d’assembly si l' **option : SETIF2** a la **valeur true**.

## <a name="syntax"></a>Syntaxe

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>Notes

Vérifiez [si](../../assembler/masm/if-masm.md) la syntaxe est complète.

Contrairement à la version 5,1, MASM 6,1 et versions ultérieures effectuent la majeure partie de son travail lors de sa première passe, puis effectuent autant de passes que nécessaire. En revanche, MASM 5,1 est toujours assemblé en deux passes sources. Par conséquent, vous devrez peut-être modifier ou supprimer certaines constructions dépendantes de MASM 6,1 et versions ultérieures.

### <a name="two-pass-directives"></a>Directives en deux passes

Pour garantir la compatibilité, MASM 6,1 et versions ultérieures prennent en charge les directives 5,1 qui font référence à deux passes. Il s’agit notamment de **. ERR1**, **. ERR2**, **IF1**, **IF2**, **ELSEIF1**et **ELSEIF2**. Pour les constructions de deuxième passe, vous devez spécifier l' [option SETIF2](option-masm.md). Sans l' **option SETIF2**, **IF2** et **.** Les directives Err2 provoquent une erreur :

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6,1 et versions ultérieures gèrent différemment les constructions de première passe. Elle traite le **. Directive ERR1** comme **. ERR**et la directive **IF1** comme **If**.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
