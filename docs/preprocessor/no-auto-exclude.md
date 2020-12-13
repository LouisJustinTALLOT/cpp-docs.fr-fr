---
description: 'En savoir plus sur les éléments suivants : no_auto_exclude l’attribut import'
title: no_auto_exclude l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 81e4d7e7f9295a4ed983e2a5024d891e30fe1361
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333358"
---
# <a name="no_auto_exclude-import-attribute"></a>no_auto_exclude l’attribut d’importation

**Section spécifique à C++**

Désactive l'exclusion automatique.

## <a name="syntax"></a>Syntaxe

>  *bibliothèque de types* #import **no_auto_exclude**

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. `#import` tente d'éviter les erreurs de définitions multiples en excluant automatiquement ces éléments. Cela entraîne l’exclusion de l' [Avertissement du compilateur (niveau 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) pour chaque élément à exclure. Vous pouvez désactiver l’exclusion automatique à l’aide de cet attribut.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
