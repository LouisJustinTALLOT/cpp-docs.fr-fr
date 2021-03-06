---
description: 'En savoir plus sur : gestion de la mémoire avec CStringT'
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
ms.openlocfilehash: 8306159aac44a2a8185052880459c9150b0cfda2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166926"
---
# <a name="memory-management-with-cstringt"></a>Gestion de la mémoire avec CStringT

La classe [CStringT](../atl-mfc-shared/reference/cstringt-class.md) est une classe de modèle utilisée pour manipuler des chaînes de caractères de longueur variable. La mémoire pour stocker ces chaînes est allouée et libérée par le biais d’un objet gestionnaire de chaînes, associé à chaque instance de `CStringT` . MFC et ATL fournissent des instanciations par défaut de `CStringT` , appelées, `CString` `CStringA` et `CStringW` , qui manipulent des chaînes de différents types de caractères. Ces types de caractères sont de type TCHAR, **`char`** , et **`wchar_t`** , respectivement. Ces types de chaîne par défaut utilisent un gestionnaire de chaînes qui alloue de la mémoire à partir du tas de processus (dans ATL) ou du tas CRT (dans MFC). Pour les applications classiques, ce schéma d’allocation de mémoire est suffisant. Toutefois, pour que le code utilise intensivement des chaînes (ou du code multithread), les gestionnaires de mémoire par défaut peuvent ne pas fonctionner de manière optimale. Cette rubrique explique comment remplacer le comportement de gestion de la mémoire par défaut de `CStringT` , en créant des allocateurs spécifiquement optimisés pour la tâche en cours.

- [Implémentation d’un gestionnaire de chaînes personnalisé (méthode de base)](../atl-mfc-shared/implementation-of-a-custom-string-manager-basic-method.md)

- [Évitement de contention de tas](../atl-mfc-shared/avoidance-of-heap-contention.md)

- [Implémentation d’un gestionnaire de chaînes personnalisé (méthode avancée)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)

- [CFixedStringT : exemple de gestionnaire de chaînes personnalisé](../atl-mfc-shared/cfixedstringt-example-of-a-custom-string-manager.md)

## <a name="see-also"></a>Voir aussi

[Exemple CustomString](../overview/visual-cpp-samples.md)
