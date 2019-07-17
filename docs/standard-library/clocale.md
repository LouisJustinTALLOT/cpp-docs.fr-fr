---
title: '&lt;clocale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <clocale>
helpviewer_keywords:
- clocale header
ms.assetid: 5bde3e01-cf67-4f1f-a383-447ec814d00e
ms.openlocfilehash: 624a1afdbe0e73c81a324273836eff6b89705236
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244761"
---
# <a name="ltclocalegt"></a>&lt;clocale&gt;

Inclut l’en-tête \<locale.h> de la bibliothèque C Standard et ajoute les noms associés à l’espace de noms `std`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<clocale >

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

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
