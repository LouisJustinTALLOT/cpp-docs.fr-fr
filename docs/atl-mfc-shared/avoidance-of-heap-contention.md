---
title: Éviter les conflits de tas
ms.date: 11/04/2016
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
ms.openlocfilehash: 45510607a63759aad9444959716bef164eda1492
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743282"
---
# <a name="avoidance-of-heap-contention"></a>Éviter les conflits de tas

Les gestionnaires de chaînes par défaut fournis par MFC et ATL sont des wrappers simples sur un segment de mémoire globale. Ce tas global est entièrement thread-safe, ce qui signifie que plusieurs threads peuvent allouer et libérer de la mémoire simultanément sans endommager le tas. Pour fournir la sécurité des threads, le tas doit sérialiser l’accès à lui-même. Cela est généralement effectué avec une section critique ou d’un mécanisme de verrouillage semblable. Chaque fois que deux threads essaient d’accéder au tas simultanément, un thread est bloqué jusqu'à la fin de la demande de l’autre thread. Pour de nombreuses applications, cette situation se produit rarement et l’impact sur les performances du tas mécanisme de verrouillage est négligeable. Toutefois, pour les applications qui accèdent fréquemment au tas à partir de plusieurs threads contention pour le verrouillage du tas peut ralentir l’application s’exécute plus lentement que s’il se trouvait à thread unique (même sur des ordinateurs avec plusieurs unités centrales).

Les applications qui utilisent [CStringT](../atl-mfc-shared/reference/cstringt-class.md) sont particulièrement sensibles à la contention de tas, car les opérations sur `CStringT` objets nécessitent fréquemment la réallocation de la mémoire tampon de chaîne.

Une façon de réduire la contention de tas entre les threads est que chaque thread alloue des chaînes à partir d’un segment de mémoire privée, thread-local. Tant que les chaînes allouées avec allocateur d’un thread particulier sont utilisées uniquement dans ce thread, l’allocateur ne sont pas nécessairement thread-safe.

## <a name="example"></a>Exemple

L’exemple ci-dessous illustre une procédure de thread qui alloue son propre tas non thread-safe à utiliser pour les chaînes sur ce thread :

[!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]

## <a name="comments"></a>Commentaires

Plusieurs threads peuvent être exécutés à l’aide de cette même procédure de thread, mais étant donné que chaque thread possède son propre tas il n’existe aucun conflit entre les threads. En outre, le fait que chaque segment de mémoire n’est pas thread-safe donne une augmentation des performances mesurable, même si une seule copie du thread est en cours d’exécution. Voici le résultat du tas ne pas à l’aide d’opérations verrouillées coûteuses pour vous protéger contre les accès simultanés.

Pour une procédure de thread plus complexe, il peut être pratique de stocker un pointeur vers le Gestionnaire de chaînes du thread dans un emplacement de stockage local (TLS) du thread. Ainsi, les autres fonctions appelées par la procédure de thread pour accéder au Gestionnaire de chaîne du thread.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
