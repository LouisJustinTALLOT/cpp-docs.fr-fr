---
description: 'En savoir plus sur : &lt; cstdbool&gt;'
title: '&lt;cstdbool&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdbool>
helpviewer_keywords:
- cstdbool header
ms.assetid: 44ccb8b2-d808-4715-8097-58ba09ab33ed
ms.openlocfilehash: de36d4088c3494cf9b8efcf5175a527da7af8ece
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126596"
---
# <a name="ltcstdboolgt"></a>&lt;cstdbool&gt;

Inclut l’en-tête de la bibliothèque standard C \<stdbool.h> et ajoute les noms associés à l' `std` espace de noms.

> [!NOTE]
> Étant donné que l' \<stdbool.h> en-tête définit des macros qui sont des mots clés en C++, il n’a aucun effet. L' \<stdbool.h> en-tête est déconseillé en C++. L' \<cstdbool> en-tête est déconseillé en c++ 17 et supprimé dans le brouillon c++ 20 standard.

## <a name="requirements"></a>Spécifications

**En-tête :**\<cstdbool>

**Espace de noms :** std

## <a name="remarks"></a>Notes

L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l’en-tête de la bibliothèque standard C sont déclarés dans l' `std` espace de noms.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](thread-safety-in-the-cpp-standard-library.md)
