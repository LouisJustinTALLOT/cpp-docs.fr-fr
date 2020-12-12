---
description: 'En savoir plus sur : &lt; clocale&gt;'
title: '&lt;clocale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <clocale>
helpviewer_keywords:
- clocale header
ms.assetid: 5bde3e01-cf67-4f1f-a383-447ec814d00e
ms.openlocfilehash: 3a1efb972d33ccb5b28fac6d77803aa6de2e08c7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325112"
---
# <a name="ltclocalegt"></a>&lt;clocale&gt;

Inclut l’en-tête de la bibliothèque C standard \<locale.h> et ajoute les noms associés à l' `std` espace de noms.

## <a name="requirements"></a>Spécifications

**En-tête :**\<clocale>

**Espace de noms :** std

## <a name="remarks"></a>Notes

L'inclusion de cet en-tête garantit également que les noms déclarés à l'aide d'une liaison externe dans l'en-tête de la bibliothèque C standard soient déclarés dans l'espace de noms `std`.

## <a name="constants"></a>Constantes

```cpp
#define NULL see below
#define LC_ALL see below
#define LC_COLLATE see below
#define LC_CTYPE see below
#define LC_MONETARY see below
#define LC_NUMERIC see below
#define LC_TIME see below
```

## <a name="structures"></a>Structures

```cpp
struct lconv;
```

## <a name="functions"></a>Fonctions

```cpp
char* setlocale(int category, const char* locale);
lconv* localeconv();
```

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
