---
description: 'En savoir plus sur : CFixedStringT : exemple de gestionnaire de chaînes personnalisé'
title: 'CFixedStringT : exemple de gestionnaire de chaînes personnalisé'
ms.date: 11/04/2016
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
ms.openlocfilehash: c9af2530500ad5972c01d063116e7ac981109493
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142504"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT : exemple de gestionnaire de chaînes personnalisé

La bibliothèque ATL implémente un exemple de gestionnaire de chaînes personnalisé utilisé par la classe [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md), appelée **CFixedStringMgr**. `CFixedStringT` est dérivée de [CStringT](../atl-mfc-shared/reference/cstringt-class.md) et implémente une chaîne qui alloue ses données de type caractère dans le cadre de l' `CFixedStringT` objet lui-même tant que la chaîne est inférieure à la longueur spécifiée par le `t_nChars` paramètre de modèle de `CFixedStringT` . Avec cette approche, la chaîne n’a pas besoin du tas, sauf si la longueur de la chaîne dépasse la taille de la mémoire tampon fixe. Étant donné que `CFixedStringT` n’utilise pas toujours un segment pour allouer ses données de chaîne, il ne peut pas utiliser `CAtlStringMgr` comme gestionnaire de chaînes. Elle utilise un gestionnaire de chaînes personnalisé ( `CFixedStringMgr` ), implémentant l’interface [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) . Cette interface est décrite dans [implémentation d’un gestionnaire de chaînes personnalisé (méthode avancée)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).

Le constructeur pour `CFixedStringMgr` prend trois paramètres :

- *pData :* Pointeur vers la structure fixe `CStringData` à utiliser.

- *nChars :* Nombre maximal de caractères que la `CStringData` structure peut contenir.

- *PMGR :* Pointeur vers l' `IAtlStringMgr` interface d’un « gestionnaire de chaînes de sauvegarde ».

Le constructeur stocke les valeurs de *pData* et *PMGR* dans leurs variables membres respectives ( `m_pData` et `m_pMgr` ). Il définit ensuite la longueur de la mémoire tampon sur zéro, la longueur disponible égale à la taille maximale de la mémoire tampon fixe et le nombre de références à-1. La valeur du nombre de références indique que la mémoire tampon est verrouillée et à utiliser cette instance de `CFixedStringMgr` comme gestionnaire de chaînes.

Le marquage de la mémoire tampon comme verrouillée empêche les autres `CStringT` instances de conserver une référence partagée à la mémoire tampon. Si d’autres `CStringT` instances étaient autorisées à partager la mémoire tampon, il serait possible de supprimer la mémoire tampon contenue dans `CFixedStringT` tandis que d’autres chaînes utilisaient toujours la mémoire tampon.

`CFixedStringMgr` est une implémentation complète de l' `IAtlStringMgr` interface. L’implémentation de chaque méthode est décrite séparément.

## <a name="implementation-of-cfixedstringmgrallocate"></a>Implémentation de CFixedStringMgr :: Allocate

L’implémentation de `CFixedStringMgr::Allocate` vérifie d’abord si la taille demandée de la chaîne est inférieure ou égale à la taille de la mémoire tampon fixe (stockée dans le `m_pData` membre). Si la mémoire tampon fixe est suffisamment grande, `CFixedStringMgr` verrouille la mémoire tampon fixe avec une longueur de zéro. Tant que la longueur de la chaîne n’augmente pas au-delà de la taille de la mémoire tampon fixe, ne doit `CStringT` pas réallouer la mémoire tampon.

Si la taille demandée de la chaîne est supérieure à celle de la mémoire tampon fixe `CFixedStringMgr` , la demande est transférée au gestionnaire de chaînes de sauvegarde. Le gestionnaire de chaînes de sauvegarde est supposé allouer la mémoire tampon à partir du tas. Toutefois, avant de retourner cette mémoire tampon, `CFixedStringMgr` la mémoire tampon est verrouillée et le pointeur de gestionnaire de chaînes de la mémoire tampon est remplacé par un pointeur vers l' `CFixedStringMgr` objet. Cela permet de s’assurer que les tentatives de réallocation ou de libération de la mémoire tampon par `CStringT` appellent `CFixedStringMgr` .

## <a name="implementation-of-cfixedstringmgrreallocate"></a>Implémentation de CFixedStringMgr :: Allocate

L’implémentation de `CFixedStringMgr::ReAllocate` est très similaire à son implémentation de `Allocate` .

Si la mémoire tampon réallouée est la mémoire tampon fixe et que la taille de la mémoire tampon demandée est inférieure à la mémoire tampon fixe, aucune allocation n’est effectuée. Toutefois, si la mémoire tampon réallouée n’est pas la mémoire tampon fixe, il doit s’agir d’une mémoire tampon allouée avec le gestionnaire de sauvegarde. Dans ce cas, le gestionnaire de sauvegarde est utilisé pour réallouer la mémoire tampon.

Si la mémoire tampon réallouée est la mémoire tampon fixe et que la nouvelle taille de mémoire tampon est trop grande pour tenir dans la mémoire tampon fixe, `CFixedStringMgr` alloue une nouvelle mémoire tampon à l’aide du gestionnaire de sauvegarde. Le contenu de la mémoire tampon fixe est ensuite copié dans la nouvelle mémoire tampon.

## <a name="implementation-of-cfixedstringmgrfree"></a>Implémentation de CFixedStringMgr :: Free

L’implémentation de `CFixedStringMgr::Free` suit le même modèle que `Allocate` et `ReAllocate` . Si la mémoire tampon libérée est la mémoire tampon fixe, la méthode lui affecte une mémoire tampon verrouillée de longueur nulle. Si la mémoire tampon libérée a été allouée avec le gestionnaire de sauvegarde, `CFixedStringMgr` utilise le gestionnaire de sauvegarde pour le libérer.

## <a name="implementation-of-cfixedstringmgrclone"></a>Implémentation de CFixedStringMgr :: Clone

L’implémentation de `CFixedStringMgr::Clone` retourne toujours un pointeur vers le gestionnaire de sauvegarde plutôt que le `CFixedStringMgr` lui-même. Cela se produit parce que chaque instance de `CFixedStringMgr` ne peut être associée qu’à une seule instance de `CStringT` . Toutes les autres instances de `CStringT` la tentative de clonage du gestionnaire doivent utiliser le gestionnaire de sauvegarde à la place. Cela est dû au fait que le gestionnaire de sauvegarde prend en charge le partage.

## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>Implémentation de CFixedStringMgr :: GetNilString

L’implémentation de `CFixedStringMgr::GetNilString` retourne la mémoire tampon fixe. En raison de la correspondance un-à-un entre `CFixedStringMgr` et `CStringT` , une instance donnée de `CStringT` n’utilise jamais plus d’une mémoire tampon à la fois. Par conséquent, une chaîne nulle et une mémoire tampon de chaîne réelle ne sont jamais nécessaires en même temps.

Chaque fois que la mémoire tampon fixe n’est pas utilisée, s' `CFixedStringMgr` assure qu’elle est initialisée avec une longueur de zéro. Cela lui permet d’être utilisé comme chaîne Nil. En guise de bonus supplémentaire, le `nAllocLength` membre de la mémoire tampon fixe est toujours défini sur la taille totale de la mémoire tampon fixe. Cela signifie que `CStringT` peut augmenter la chaîne sans appeler [IAtlStringMgr :: Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate), même pour la chaîne Nil.

## <a name="requirements"></a>Spécifications

**En-tête :** CStringT. h

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
