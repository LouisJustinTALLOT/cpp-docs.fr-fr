---
description: 'En savoir plus sur : implémentation d’un gestionnaire de chaînes personnalisé (méthode avancée)'
title: Implémentation d’un gestionnaire de chaînes personnalisé (méthode avancée)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
ms.openlocfilehash: 042c0759076d14e2fd0cf8dd91e34c4f1d8bb534
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166965"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>Implémentation d’un gestionnaire de chaînes personnalisé (méthode avancée)

Dans des situations particulières, vous souhaiterez peut-être implémenter un gestionnaire de chaînes personnalisé qui ne se contente pas de modifier le tas utilisé pour allouer de la mémoire. Dans ce cas, vous devez implémenter manuellement l’interface [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) comme gestionnaire de chaînes personnalisé.

Pour ce faire, il est important de comprendre comment [CStringT](../atl-mfc-shared/reference/cstringt-class.md) utilise cette interface pour gérer ses données de chaîne. Chaque instance de `CStringT` a un pointeur vers une structure [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) . Cette structure de longueur variable contient des informations importantes sur la chaîne (telles que la longueur), ainsi que les données de caractères réelles de la chaîne. Chaque gestionnaire de chaînes personnalisé est chargé d’allouer et de libérer ces structures à la demande de `CStringT` .

La `CStringData` structure comprend quatre champs :

- [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) Ce champ pointe vers l' `IAtlStringMgr` interface utilisée pour gérer ces données de chaîne. Lorsque `CStringT` doit réallouer ou libérer la mémoire tampon de chaîne, il appelle les méthodes de réallocation ou de libération de cette interface, en passant la `CStringData` structure en tant que paramètre. Lors de l’allocation d’une `CStringData` structure dans votre gestionnaire de chaînes, vous devez définir ce champ de sorte qu’il pointe vers votre gestionnaire de chaînes personnalisé.

- [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) Ce champ contient la longueur logique actuelle de la chaîne stockée dans la mémoire tampon, à l’exclusion de la valeur null de fin. `CStringT` met à jour ce champ lorsque la longueur de la chaîne change. Lors de l’allocation d’une `CStringData` structure, votre gestionnaire de chaînes doit affecter la valeur zéro à ce champ. Lors de la réallocation d’une `CStringData` structure, votre gestionnaire de chaînes personnalisé doit conserver ce champ inchangé.

- [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) Ce champ contient le nombre maximal de caractères (à l’exception de la valeur null de fin) qui peuvent être stockés dans cette mémoire tampon de chaîne sans réallocation. Chaque fois que `CStringT` doit augmenter la longueur logique de la chaîne, il vérifie d’abord ce champ pour s’assurer qu’il y a suffisamment d’espace dans la mémoire tampon. Si la vérification échoue, `CStringT` appelle votre gestionnaire de chaînes personnalisé pour réallouer la mémoire tampon. Lors de l’allocation ou de la réallocation d’une `CStringData` structure, vous devez définir ce champ sur au moins le nombre de caractères demandés dans le paramètre *nChars* à [IAtlStringMgr :: Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) ou [IAtlStringMgr :: Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate). S’il y a plus d’espace dans la mémoire tampon que ce qui a été demandé, vous pouvez définir cette valeur pour refléter la quantité réelle d’espace disponible. Cela permet `CStringT` à d’augmenter la chaîne pour remplir l’intégralité de l’espace alloué avant de pouvoir effectuer un rappel dans le gestionnaire de chaînes pour réallouer la mémoire tampon.

- [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) Ce champ contient le décompte de références actuel de la mémoire tampon de chaîne. Si la valeur est un, une seule instance de `CStringT` utilise la mémoire tampon. En outre, l’instance est autorisée à lire et à modifier le contenu de la mémoire tampon. Si la valeur est supérieure à un, plusieurs instances de `CStringT` peuvent utiliser la mémoire tampon. Étant donné que la mémoire tampon de caractères est partagée, les `CStringT` instances peuvent uniquement lire le contenu de la mémoire tampon. Pour modifier le contenu, `CStringT` crée d’abord une copie de la mémoire tampon. Si la valeur est négative, une seule instance de `CStringT` utilise la mémoire tampon. Dans ce cas, la mémoire tampon est considérée comme verrouillée. Lorsqu’une `CStringT` instance utilise une mémoire tampon verrouillée, aucune autre instance de `CStringT` ne peut partager la mémoire tampon. Au lieu de cela, ces instances créent une copie de la mémoire tampon avant de manipuler le contenu. En outre, l' `CStringT` instance qui utilise la mémoire tampon verrouillée ne tente pas de partager la mémoire tampon d’une autre `CStringT` instance qui lui est assignée. Dans ce cas, l' `CStringT` instance copie l’autre chaîne dans la mémoire tampon verrouillée.

   Lors de l’allocation d’une `CStringData` structure, vous devez définir ce champ pour refléter le type de partage autorisé pour la mémoire tampon. Pour la plupart des implémentations, définissez cette valeur sur un. Cela permet le comportement habituel de partage de copie sur écriture. Toutefois, si votre gestionnaire de chaînes ne prend pas en charge le partage de la mémoire tampon de chaîne, définissez ce champ sur un état verrouillé. Cela force `CStringT` à utiliser uniquement cette mémoire tampon pour l’instance de qui l’a `CStringT` allouée.

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
