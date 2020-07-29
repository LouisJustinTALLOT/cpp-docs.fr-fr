---
title: Utilisation de CString
ms.date: 06/18/2018
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
ms.openlocfilehash: 8ebf3441c7d8856fe412e2efed4c717b01ced362
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219012"
---
# <a name="using-cstring"></a>Utilisation de CString

Les rubriques de cette section décrivent comment programmer avec `CString`. Pour obtenir une documentation de référence sur la `CString` classe, consultez la documentation de [CStringT](../atl-mfc-shared/reference/cstringt-class.md).

Pour utiliser `CString`, incluez l'en-tête `atlstr.h`.

Les `CString` `CStringA` classes, et `CStringW` sont des spécialisations d’un modèle de classe appelé [CStringT](../atl-mfc-shared/reference/cstringt-class.md) selon le type de données de caractères qu’ils prennent en charge.

Un `CStringW` objet contient le **`wchar_t`** type et prend en charge les chaînes Unicode. Un `CStringA` objet contient le **`char`** type et prend en charge les chaînes codées sur un octet et multioctets (MBCS). Un `CString` objet prend en charge le **`char`** type ou le **`wchar_t`** type, selon que le symbole MBCS ou le symbole Unicode est défini au moment de la compilation.

Un objet `CString` conserve les données caractères dans un objet `CStringData`. `CString`accepte les chaînes de style C se terminant par un caractère NULL. `CString`effectue le suivi de la longueur de chaîne pour accélérer les performances, mais conserve également le caractère NULL dans les données de caractères stockées pour prendre en charge la conversion en LPCWSTR. `CString`comprend le terminateur null lorsqu’il exporte une chaîne de style C. Vous pouvez insérer une valeur NULL à d’autres emplacements dans un `CString` , mais cela peut produire des résultats inattendus.

L'ensemble suivant de classes de chaîne peut être utilisé sans liaison avec la bibliothèque MFC, avec ou sans prise en charge de CRT : `CAtlString`, `CAtlStringA` et `CAtlStringW`.

`CString` est utilisé dans les projets natifs. Pour les projets en code managé (C++/CLI), utilisez `System::String`.

Pour ajouter davantage de capacités à celles actuellement offertes par `CString`, `CStringA` ou `CStringW`, vous devez créer une sous-classe de `CStringT` qui contient les fonctionnalités supplémentaires.

Le code suivant montre comment créer un objet `CString` et l'imprimer dans la sortie standard :

```cpp
#include <atlstr.h>

int main() {
    CString aCString = CString(_T("A string"));
    _tprintf(_T("%s"), (LPCTSTR) aCString);
}
```

## <a name="in-this-section"></a>Dans cette section

[Opérations CString de base](../atl-mfc-shared/basic-cstring-operations.md)<br/>
Décrit les opérations `CString` de base, y compris la création d'objets à partir de chaînes littérales C, l'accès à des caractères individuels d'un objet `CString`, la concaténation de deux objets et la comparaison d'objets `CString`.

[Gestion des données de chaîne](../atl-mfc-shared/string-data-management.md)<br/>
Présente l'utilisation de Unicode et MBCS avec `CString`.

[Sémantique CString](../atl-mfc-shared/cstring-semantics.md)<br/>
Explique comment les objets `CString` sont utilisés.

[Opérations CString relatives aux chaînes de style C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)<br/>
Décrit la manipulation du contenu d'un objet `CString` sous la forme d'une chaîne de style C terminée par un caractère null.

[Allocation et libération de mémoire pour un BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)<br/>
Décrit l’utilisation de la mémoire pour un BSTR et des objets COM.

[Nettoyage des exceptions CString](../atl-mfc-shared/cstring-exception-cleanup.md)<br/>
Explique qu'un nettoyage explicite dans MFC 3.0 et ultérieur n'est plus nécessaire.

[Réussite de l’argument CString](../atl-mfc-shared/cstring-argument-passing.md)<br/>
Explique comment passer des objets CString à des fonctions et comment retourner des objets `CString` depuis des fonctions.

[Prise en charge d’Unicode et du jeu de caractères multioctets (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)<br/>
Explique comment MFC prend en charge Unicode et MBCS.

## <a name="reference"></a>Informations de référence

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Fournit des informations de référence sur la classe `CStringT`.

[CSimpleStringT, classe](../atl-mfc-shared/reference/csimplestringt-class.md)<br/>
Fournit des informations de référence sur la classe `CSimpleStringT`.

## <a name="related-sections"></a>Sections connexes

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
Contient des liens vers des rubriques décrivant plusieurs façons de gérer les données chaînes.

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
