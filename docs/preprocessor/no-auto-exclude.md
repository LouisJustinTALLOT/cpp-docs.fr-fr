---
title: no_auto_exclude importer l’attribut
ms.date: 08/29/2019
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 530c2b2adf24e964cb0a512371f4430a61bf8b11
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216079"
---
# <a name="no_auto_exclude-import-attribute"></a>no_auto_exclude importer l’attribut

**C++Plus**

Désactive l'exclusion automatique.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **no_auto_exclude**

## <a name="remarks"></a>Notes

Les bibliothèques de types peuvent inclure des définitions d'éléments définis dans les en-têtes système ou dans d'autres bibliothèques de types. `#import` tente d'éviter les erreurs de définitions multiples en excluant automatiquement ces éléments. Cela entraîne l’exclusion de l' [Avertissement du compilateur (niveau 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) pour chaque élément à exclure. Vous pouvez désactiver l’exclusion automatique à l’aide de cet attribut.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
