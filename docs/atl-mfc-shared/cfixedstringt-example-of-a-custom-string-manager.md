---
title: "CFixedStringT : Exemple d’un gestionnaire de chaîne personnalisé. | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7164d2313f5610d1d7e56f5449c81ea9e2282981
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT : Exemple d’un gestionnaire de chaîne personnalisé.
La bibliothèque ATL implémente un exemple d’un gestionnaire de chaîne personnalisé utilisé par la classe [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md), appelé **CFixedStringMgr**. `CFixedStringT`est dérivé de [CStringT](../atl-mfc-shared/reference/cstringt-class.md) et implémente une chaîne qui alloue ses données de caractères dans le cadre de la `CFixedStringT` de l’objet lui-même, que la chaîne est inférieure à la longueur spécifiée par le **t_nChars** paramètre de modèle de `CFixedStringT`. Avec cette approche, la chaîne n'a pas besoin du tas, sauf si la longueur de la chaîne dépasse la taille de la mémoire tampon fixe. Étant donné que `CFixedStringT` n’utilise pas toujours un segment de mémoire pour allouer ses données de chaîne, il ne peut pas utiliser **CAtlStringMgr** en tant que gestionnaire de chaînes. Elle utilise un gestionnaire de chaîne personnalisée (**CFixedStringMgr**), qui implémente le [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interface. Cette interface est décrite dans [implémentation d’un gestionnaire de chaînes personnalisé (méthode avancée)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).  
  
 Le constructeur de **CFixedStringMgr** accepte trois paramètres :  
  
-   **pData :** un pointeur vers le texte fixe `CStringData` structure à utiliser.  
  
-   **nChars :** le nombre maximal de caractères le `CStringData` structure peut contenir.  
  
-   **pMgr :** un pointeur vers le `IAtlStringMgr` interface d’un « gestionnaire de chaînes de sauvegarde ».  
  
 Le constructeur stocke les valeurs de `pData` et **pMgr** dans leurs variables membres respectives (`m_pData` et **m_pMgr**). Il définit ensuite la longueur de la mémoire tampon à zéro, la longueur disponible égale à la taille maximale de la mémoire tampon fixe et le nombre de références à -1. La valeur du nombre de référence indique la mémoire tampon est verrouillée et d’utiliser cette instance de **CFixedStringMgr** en tant que le Gestionnaire de chaînes.  
  
 Le marquage de la mémoire tampon comme étant verrouillée empêche les autres `CStringT` instances à partir de contenir une référence partagée dans la mémoire tampon. Si d’autres `CStringT` instances étaient autorisés à partager la mémoire tampon il serait possible pour la mémoire tampon contenue par `CFixedStringT` seront supprimées et autres chaînes ont toujours à l’aide de la mémoire tampon.  
  
 **CFixedStringMgr** est une implémentation complète de la `IAtlStringMgr` interface. L’implémentation de chaque méthode est traitée séparément.  
  
## <a name="implementation-of-cfixedstringmgrallocate"></a>Implémentation de CFixedStringMgr::Allocate  
 L’implémentation de **CFixedStringMgr::Allocate** premier vérifie si la taille demandée de la chaîne est inférieure ou égale à la taille de la mémoire tampon fixe (stockée dans le `m_pData` membre). Si la mémoire tampon fixe est suffisante, **CFixedStringMgr** verrouille la mémoire tampon fixe avec une longueur de zéro. Tant que la longueur de chaîne n’augmente pas au-delà de la taille de la mémoire tampon fixe, `CStringT` aurez pas à réallouer la mémoire tampon.  
  
 Si la taille demandée de la chaîne est supérieure à la mémoire tampon fixe **CFixedStringMgr** transfère la demande au Gestionnaire de chaînes de sauvegarde. Le Gestionnaire de chaînes de sauvegarde est censé allouer la mémoire tampon à partir du tas. Toutefois, avant de retourner cette mémoire tampon **CFixedStringMgr** verrouille la mémoire tampon et remplace le pointeur de la mémoire tampon du Gestionnaire de chaîne avec un pointeur vers le **CFixedStringMgr** objet. Cela garantit que les tentatives de réallouer ou libérer la mémoire tampon par `CStringT` appelle **CFixedStringMgr**.  
  
## <a name="implementation-of-cfixedstringmgrreallocate"></a>Implémentation de CFixedStringMgr::ReAllocate  
 L’implémentation de **CFixedStringMgr::ReAllocate** est très similaire à son implémentation de **Allocate**.  
  
 Si la mémoire tampon réallouée est la mémoire tampon fixe et la taille de mémoire tampon demandée est inférieure à la mémoire tampon fixe, aucune affectation n’est effectuée. Toutefois, si la mémoire tampon réallouée n’est pas la mémoire tampon fixe, il doit être une mémoire tampon alloué avec le Gestionnaire de sauvegarde. Dans ce cas, le Gestionnaire de sauvegarde est utilisé pour réallouer la mémoire tampon.  
  
 Si la mémoire tampon réallouée est la mémoire tampon fixe et la nouvelle taille de mémoire tampon est trop grande pour tenir dans la mémoire tampon fixe, **CFixedStringMgr** alloue une nouvelle mémoire tampon à l’aide du Gestionnaire de sauvegarde. Le contenu de la mémoire tampon fixe est ensuite copié dans la nouvelle mémoire tampon.  
  
## <a name="implementation-of-cfixedstringmgrfree"></a>Implémentation de CFixedStringMgr::Free  
 L’implémentation de **CFixedStringMgr::Free** suit le même modèle en tant que **Allocate** et `ReAllocate`. Si la mémoire tampon libérée est la mémoire tampon fixe, la méthode lui affecte une mémoire tampon verrouillée de longueur nulle. Si la mémoire tampon libérée a été allouée avec le Gestionnaire de sauvegarde, **CFixedStringMgr** utilise le Gestionnaire de sauvegarde pour le libérer.  
  
## <a name="implementation-of-cfixedstringmgrclone"></a>Implémentation de CFixedStringMgr::Clone  
 L’implémentation de **CFixedStringMgr::Clone** toujours retourne un pointeur vers le Gestionnaire de sauvegarde plutôt que la **CFixedStringMgr** lui-même. Cela se produit car chaque instance de **CFixedStringMgr** peut uniquement être associé à une seule instance de `CStringT`. Toutes les autres instances de `CStringT` la tentative de clonage du gestionnaire doit obtenir le Gestionnaire de sauvegarde à la place. Il s’agit, car le Gestionnaire de sauvegarde prend en charge le partage.  
  
## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>Implémentation de CFixedStringMgr::GetNilString  
 L’implémentation de **CFixedStringMgr::GetNilString** retourne la mémoire tampon fixe. En raison de la correspondance bi-univoque **CFixedStringMgr** et `CStringT`, une instance donnée de `CStringT` n’utilise jamais plus d’une mémoire tampon à la fois. Par conséquent, une chaîne nulle et une mémoire tampon de chaîne réelles ne sont jamais nécessaires en même temps.  
  
 Chaque fois que la mémoire tampon fixe n’est pas en cours d’utilisation, **CFixedStringMgr** permet de s’assurer qu’elle est initialisée avec une longueur nulle. Ainsi, pour être utilisée en tant que chaîne nulle. En prime, le `nAllocLength` membre de la mémoire tampon fixe est toujours définie sur la taille totale de la mémoire tampon fixe. Cela signifie que `CStringT` peut atteindre la chaîne sans appeler [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate), même pour la chaîne nulle.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** cstringt.h  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

