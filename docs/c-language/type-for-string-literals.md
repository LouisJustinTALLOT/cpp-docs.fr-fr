---
title: Type pour les littéraux de chaîne
ms.date: 11/04/2016
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
ms.openlocfilehash: 7e832ac7aa08ad80ab395baa59eabbabb486b46f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152272"
---
# <a name="type-for-string-literals"></a>Type pour les littéraux de chaîne

Les littéraux de chaîne ont un tableau de type `char` (autrement dit, **char[ ]**). (Les chaînes à caractères larges ont un tableau de type `wchar_t` (autrement dit, **wchar_t[ ]**).) Cela signifie qu'une chaîne est un tableau avec des éléments de type `char`. Le nombre d'éléments du tableau est égal au nombre de caractères dans la chaîne plus un pour le caractère null de fin.

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)
