---
description: 'En savoir plus sur : type pour les littéraux de chaîne'
title: Type pour les littéraux de chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
ms.openlocfilehash: 9b752d79a1f33e43f24fb86902ba91b3d31777c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242819"
---
# <a name="type-for-string-literals"></a>Type pour les littéraux de chaîne

Les littéraux de chaîne ont un tableau de type **`char`** (autrement dit, **Char []**). (Les chaînes à caractères larges ont un tableau de **`wchar_t`** type (autrement dit, **wchar_t []**).) Cela signifie qu’une chaîne est un tableau avec des éléments de type **`char`** . Le nombre d'éléments du tableau est égal au nombre de caractères dans la chaîne plus un pour le caractère null de fin.

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)
