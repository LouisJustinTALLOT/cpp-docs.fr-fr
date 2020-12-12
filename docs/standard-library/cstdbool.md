---
description: 'En savoir plus sur : &lt; cstdbool&gt;'
title: '&lt;cstdbool&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdbool>
- cstdbool
helpviewer_keywords:
- cstdbool header
ms.assetid: 44ccb8b2-d808-4715-8097-58ba09ab33ed
ms.openlocfilehash: 0711c05ff136f90a701ff707976a172d2bcb1315
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324733"
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
