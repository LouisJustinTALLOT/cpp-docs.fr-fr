---
description: 'En savoir plus sur : opérateurs additifs C'
title: Opérateurs additifs C
ms.date: 10/18/2018
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
ms.openlocfilehash: b77c3e9716cba716f625fa142129f5c1ce095907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211594"
---
# <a name="c-additive-operators"></a>Opérateurs additifs C

Les opérateurs additifs effectuent l’addition ( **+** ) et la soustraction ( **-** ).

## <a name="syntax"></a>Syntaxe

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **+** *multiplicatif-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **-** *multiplicatif-expression*

> [!NOTE]
> Même si la syntaxe de l’élément *additive-expression* comprend *multiplicative-expression*, cela n’implique pas l’obligation d’utiliser des expressions avec multiplication. Consultez la syntaxe dans [Résumé de syntaxe du langage C](../c-language/c-language-syntax-summary.md), pour les éléments *multiplicative-expression*, *cast-expression* et *unary-expression*.

Les opérandes peuvent être des valeurs intégrales ou flottantes. Certaines opérations additives peuvent également être exécutées sur des valeurs de pointeur, comme l'indique la description de chaque opérateur.

Les opérateurs additifs exécutent les conversions arithmétiques habituelles sur les opérandes de type entier et flottant. Le type du résultat est le type des opérandes après conversion. Étant donné que les conversions exécutées par les opérateurs additifs ne fournissent pas de conditions de dépassement de capacité positif ou de dépassement de capacité négatif, les informations risquent d’être perdues si le résultat d’une opération additive ne peut pas être représenté dans le type des opérandes après conversion.

## <a name="see-also"></a>Voir aussi

[Opérateurs additifs : + et-](../cpp/additive-operators-plus-and.md)
