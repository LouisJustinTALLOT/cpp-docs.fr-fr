---
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
ms.openlocfilehash: 603a590190c50495aa80f1b41a574149eb8f760a
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342838"
---
# <a name="ltcstdaligngt"></a>&lt;cstdalign&gt;

Dans certaines C++ implémentations de bibliothèque standard, cet en-tête inclut l’en \<-tête stdalign. > h de la bibliothèque standard C, `std` et ajoute les noms associés à l’espace de noms. Étant donné que cet en-tête n’est \<pas implémenté dans MSVC, l’en `__alignas_is_defined` - `__alignof_is_defined`tête > cstdalign définit des macros de compatibilité et.

> [!NOTE]
> Étant donné \<que l’en-tête stdalign. h > définit des macros qui sont des mots clés dans C++, y compris il n’a aucun effet. L' \<en-tête stdalign. h > est déconseillé C++dans. L' \<en-tête > cstdalign est déconseillé dans c++ 17 et supprimé dans le brouillon c++ 20 standard.

## <a name="requirements"></a>Configuration requise

**En-tête:** \<cstdalign >

**Espace de noms :** std

## <a name="macros"></a>Macros

| Macro | Description |
| - | - |
| `__alignas_is_defined` | Macro de compatibilité C qui se développe en une constante entière de 1. |
| `__alignof_is_defined` | Macro de compatibilité C qui se développe en une constante entière de 1. |

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[C++vue d’ensemble de la bibliothèque standard](cpp-standard-library-overview.md)\
[Sécurité des threads C++ dans la bibliothèque standard](thread-safety-in-the-cpp-standard-library.md)
