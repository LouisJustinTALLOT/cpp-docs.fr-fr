---
description: 'En savoir plus sur : évitement de contention de tas'
title: Évitement de contention de tas
ms.date: 11/04/2016
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
ms.openlocfilehash: c58849bee46dd0d870d1067f17581429339fbc0e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142569"
---
# <a name="avoidance-of-heap-contention"></a>Évitement de contention de tas

Les gestionnaires de chaînes par défaut fournis par MFC et ATL sont des wrappers simples sur un tas global. Ce tas global est entièrement sécurisé au niveau du thread, ce qui signifie que plusieurs threads peuvent allouer et libérer de la mémoire simultanément sans endommager le tas. Pour garantir la sécurité des threads, le tas doit sérialiser l’accès à lui-même. Cela s’effectue généralement à l’aide d’une section critique ou d’un mécanisme de verrouillage similaire. Chaque fois que deux threads essaient d’accéder simultanément au tas, un thread est bloqué jusqu’à ce que la demande de l’autre thread soit terminée. Pour de nombreuses applications, cette situation se produit rarement et l’impact sur les performances du mécanisme de verrouillage du tas est négligeable. Toutefois, pour les applications qui accèdent fréquemment au segment de mémoire à partir de plusieurs threads, la contention du verrou du tas peut ralentir l’exécution de l’application, même si elle était à thread unique (même sur des ordinateurs avec plusieurs processeurs).

Les applications qui utilisent [CStringT](../atl-mfc-shared/reference/cstringt-class.md) sont particulièrement sensibles à la contention des tas, car les opérations sur `CStringT` les objets requièrent fréquemment la réallocation de la mémoire tampon de chaîne.

Une façon de réduire la contention du tas entre les threads consiste à faire en sorte que chaque thread alloue des chaînes à partir d’un tas privé de thread local. Tant que les chaînes allouées avec l’allocateur d’un thread particulier sont utilisées uniquement dans ce thread, l’allocateur n’a pas besoin d’être thread-safe.

## <a name="example"></a>Exemple

L’exemple ci-dessous illustre une procédure de thread qui alloue son propre tas privé non thread-safe à utiliser pour les chaînes sur ce thread :

[!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]

## <a name="comments"></a>Commentaires

Plusieurs threads peuvent s’exécuter à l’aide de cette même procédure de thread, mais comme chaque thread a son propre tas, il n’y a pas de conflit entre les threads. En outre, le fait que chaque segment de mémoire n’est pas thread-safe donne une augmentation mesurable des performances même si une seule copie du thread est en cours d’exécution. Cela est dû au fait que le tas n’utilise pas d’opérations verrouillées coûteuses pour se protéger contre les accès simultanés.

Pour une procédure de thread plus complexe, il peut être pratique de stocker un pointeur vers le gestionnaire de chaînes du thread dans un emplacement de stockage local des threads (TLS). Cela permet à d’autres fonctions appelées par la procédure de thread d’accéder au gestionnaire de chaînes du thread.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
