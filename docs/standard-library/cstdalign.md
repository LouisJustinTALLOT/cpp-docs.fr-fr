---
description: 'En savoir plus sur : &lt; cstdalign&gt;'
title: '&lt;cstdalign&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdalign>
- cstdalign
- __alignas_is_defined
- __alignof_is_defined
helpviewer_keywords:
- cstdalign header
- __alignas_is_defined
- __alignof_is_defined
ms.assetid: 9d570924-d299-4225-9a58-8c4c820f5903
ms.openlocfilehash: 149893b33ead3e66223b9124ff7c1b6346929799
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324746"
---
# <a name="ltcstdaligngt"></a>&lt;cstdalign&gt;

Dans certaines implémentations de la bibliothèque standard C++, cet en-tête inclut l’en-tête de la bibliothèque standard C \<stdalign.h> et ajoute les noms associés à l' `std` espace de noms. Étant donné que cet en-tête n’est pas implémenté dans MSVC, l' \<cstdalign> en-tête définit des macros `__alignas_is_defined` de compatibilité et `__alignof_is_defined` .

> [!NOTE]
> Étant donné que l' \<stdalign.h> en-tête définit des macros qui sont des mots clés en C++, il n’a aucun effet. L' \<stdalign.h> en-tête est déconseillé en C++. L' \<cstdalign> en-tête est déconseillé en c++ 17 et supprimé dans le brouillon c++ 20 standard.

## <a name="requirements"></a>Spécifications

**En-tête :**\<cstdalign>

**Espace de noms :** std

## <a name="macros"></a>Macros

| Macro | Description |
| - | - |
| `__alignas_is_defined` | Macro de compatibilité C qui se développe en une constante entière de 1. |
| `__alignof_is_defined` | Macro de compatibilité C qui se développe en une constante entière de 1. |

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](thread-safety-in-the-cpp-standard-library.md)
