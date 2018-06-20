---
title: Utilisation de CString | Documents Microsoft
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5759c8a0aaa628d612010cb7d04690a3d3bfa54f
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238719"
---
# <a name="using-cstring"></a>Utilisation de CString
Les rubriques de cette section décrivent comment programmer avec `CString`. Pour la documentation de référence sur les `CString` de classe, consultez la documentation de [CStringT](../atl-mfc-shared/reference/cstringt-class.md).  
  
 Pour utiliser `CString`, incluez l'en-tête `atlstr.h`.  
  
 Le `CString`, `CStringA`, et `CStringW` classes sont des spécialisations de modèle de classe appelé [CStringT](../atl-mfc-shared/reference/cstringt-class.md) en fonction du type de données de caractères pris en charge.  
  
 Un objet `CStringW` contient le type `wchar_t` et prend en charge les chaînes Unicode. Un objet `CStringA` contient le type `char` et prend en charge les chaînes sur un octet et les chaînes multi-octets (MBCS). Un objet `CString` prend en charge le type `char` ou le type `wchar_t`, selon que le symbole `MBCS` ou le symbole `UNICODE` est défini à la compilation.  
  
 Un objet `CString` conserve les données caractères dans un objet `CStringData`. `CString` accepte `null`-arrêté des chaînes de style C. `CString` assure le suivi de la longueur de chaîne pour améliorer les performances, mais elle conserve également la `null` caractères dans les données de type caractère pour prendre en charge la conversion en LPCWSTR. `CString` inclut le terminateur null quand il exporte une chaîne de style C. Vous pouvez insérer un `null` à d’autres emplacements dans un `CString`, mais elle peut produire des résultats inattendus.  
  
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
 [Opérations CString de base](../atl-mfc-shared/basic-cstring-operations.md)  
 Décrit les opérations `CString` de base, y compris la création d'objets à partir de chaînes littérales C, l'accès à des caractères individuels d'un objet `CString`, la concaténation de deux objets et la comparaison d'objets `CString`.  
  
 [Gestion des données chaînes](../atl-mfc-shared/string-data-management.md)  
 Présente l'utilisation de Unicode et MBCS avec `CString`.  
  
 [Sémantique CString](../atl-mfc-shared/cstring-semantics.md)  
 Explique comment les objets `CString` sont utilisés.  
  
 [Opérations CString relatives aux chaînes de style C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)  
 Décrit la manipulation du contenu d'un objet `CString` sous la forme d'une chaîne de style C terminée par un caractère null.  
  
 [Allocation et libération de mémoire pour un BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)  
 Présente l'utilisation de la mémoire pour un `BSTR` et des objets COM.  
  
 [Nettoyage des exceptions CString](../atl-mfc-shared/cstring-exception-cleanup.md)  
 Explique qu'un nettoyage explicite dans MFC 3.0 et ultérieur n'est plus nécessaire.  
  
 [Passage d’arguments CString](../atl-mfc-shared/cstring-argument-passing.md)  
 Explique comment passer des objets CString à des fonctions et comment retourner des objets `CString` depuis des fonctions.  
  
 [Prise en charge des jeux de caractères Unicode et MBCS (Multibyte Character Set)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)  
 Explique comment MFC prend en charge Unicode et MBCS.  
  
## <a name="reference"></a>Référence  
 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)  
 Fournit des informations de référence sur la classe `CStringT`.  
  
 [CSimpleStringT, classe](../atl-mfc-shared/reference/csimplestringt-class.md)  
 Fournit des informations de référence sur la classe `CSimpleStringT`.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
 Contient des liens vers des rubriques décrivant plusieurs façons de gérer les données chaînes.  
  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)

