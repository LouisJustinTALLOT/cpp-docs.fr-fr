---
title: Gestion de la mémoire avec CStringT
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, memory management
- memory [C++], usage
- IAtlStringMgr class, using
- strings [C++], custom memory management
- CFixedStringT class, description of
- strings [C++], memory management
- CStringT class, memory management
ms.assetid: 88b8342d-19b5-48c4-9cf6-e4c44cece21e
ms.openlocfilehash: bf1f99b92761c84d59b6f7bfb9aef67d7e097893
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222028"
---
# <a name="memory-management-with-cstringt"></a>Gestion de la mémoire avec CStringT

La classe [CStringT](../atl-mfc-shared/reference/cstringt-class.md) est une classe de modèle utilisée pour manipuler des chaînes de caractères de longueur variable. La mémoire pour stocker ces chaînes est allouée et libérée par le biais d’un objet gestionnaire de chaînes, associé à chaque instance de `CStringT` . MFC et ATL fournissent des instanciations par défaut de `CStringT` , appelées, `CString` `CStringA` et `CStringW` , qui manipulent des chaînes de différents types de caractères. Ces types de caractères sont de type TCHAR, **`char`** , et **`wchar_t`** , respectivement. Ces types de chaîne par défaut utilisent un gestionnaire de chaînes qui alloue de la mémoire à partir du tas de processus (dans ATL) ou du tas CRT (dans MFC). Pour les applications classiques, ce schéma d’allocation de mémoire est suffisant. Toutefois, pour que le code utilise intensivement des chaînes (ou du code multithread), les gestionnaires de mémoire par défaut peuvent ne pas fonctionner de manière optimale. Cette rubrique explique comment remplacer le comportement de gestion de la mémoire par défaut de `CStringT` , en créant des allocateurs spécifiquement optimisés pour la tâche en cours.

- [Implémentation d’un gestionnaire de chaînes personnalisé (méthode de base)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Évitement de contention de tas](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Implémentation d’un gestionnaire de chaînes personnalisé (méthode avancée)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT : exemple de gestionnaire de chaînes personnalisé](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Voir aussi

[Exemple CustomString](../overview/visual-cpp-samples.md)
