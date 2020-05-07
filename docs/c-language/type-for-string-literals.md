---
title: Type pour les littéraux de chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
ms.openlocfilehash: 7e832ac7aa08ad80ab395baa59eabbabb486b46f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344848"
---
# <a name="type-for-string-literals"></a>Type pour les littéraux de chaîne

Les littéraux de chaîne ont un tableau de type `char` (autrement dit, **char[ ]**). (Les chaînes à caractères larges ont un tableau `wchar_t` de type (autrement dit, **wchar_t []**).) Cela signifie qu’une chaîne est un tableau avec des éléments de `char`type. Le nombre d'éléments du tableau est égal au nombre de caractères dans la chaîne plus un pour le caractère null de fin.

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)
