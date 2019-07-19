---
title: '&lt;cstdbool&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdbool>
- cstdbool
helpviewer_keywords:
- cstdbool header
ms.assetid: 44ccb8b2-d808-4715-8097-58ba09ab33ed
ms.openlocfilehash: ed780e059a5e456731fd6a4f651639e282016f5e
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341102"
---
# <a name="ltcstdboolgt"></a>&lt;cstdbool&gt;

Inclut l’en-tête \<Stdbool. > h de la bibliothèque standard C et ajoute les noms associés à l' `std` espace de noms.

> [!NOTE]
> Étant donné \<que l’en-tête Stdbool. h > définit des macros qui sont des mots clés dans C++, y compris il n’a aucun effet. L' \<en-tête Stdbool. h > est déconseillé C++dans. L' \<en-tête > cstdbool est déconseillé dans c++ 17 et supprimé dans le brouillon c++ 20 standard.

## <a name="requirements"></a>Configuration requise

**En-tête:** \<cstdbool >

**Espace de noms :** std

## <a name="remarks"></a>Notes

L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l' `std` en-tête de la bibliothèque standard C sont déclarés dans l’espace de noms.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[C++vue d’ensemble de la bibliothèque standard](cpp-standard-library-overview.md)\
[Sécurité des threads C++ dans la bibliothèque standard](thread-safety-in-the-cpp-standard-library.md)
