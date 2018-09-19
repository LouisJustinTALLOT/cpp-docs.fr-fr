---
title: Type pour les littéraux de chaîne | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- string literals, type
- types [C], string literals
ms.assetid: f50a28af-20c1-4440-bdc6-564c86a309c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7773882d6fb04341a6f6d3a2cbcfda1d05f85d17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063279"
---
# <a name="type-for-string-literals"></a>Type pour les littéraux de chaîne

Les littéraux de chaîne ont un tableau de type `char` (autrement dit, **char[ ]**). (Les chaînes à caractères larges ont un tableau de type `wchar_t` (autrement dit, **wchar_t[ ]**).) Cela signifie qu'une chaîne est un tableau avec des éléments de type `char`. Le nombre d'éléments du tableau est égal au nombre de caractères dans la chaîne plus un pour le caractère null de fin.

## <a name="see-also"></a>Voir aussi

[Littéraux de chaîne C](../c-language/c-string-literals.md)