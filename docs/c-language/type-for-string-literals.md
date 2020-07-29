---
title: Type pour les littéraux de chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
ms.openlocfilehash: cd84a8c37e2929394e34010d14fc9264080539cc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198994"
---
# <a name="type-for-string-literals"></a>Type pour les littéraux de chaîne

Les littéraux de chaîne ont un tableau de type **`char`** (autrement dit, **Char []**). (Les chaînes à caractères larges ont un tableau de **`wchar_t`** type (autrement dit, **wchar_t []**).) Cela signifie qu’une chaîne est un tableau avec des éléments de type **`char`** . Le nombre d'éléments du tableau est égal au nombre de caractères dans la chaîne plus un pour le caractère null de fin.

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)
