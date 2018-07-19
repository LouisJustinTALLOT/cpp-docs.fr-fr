---
title: Implémentation de gestionnaire de chaînes personnalisé (méthode d’avancé) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d72ce586c7c93f6bd5ade613ab2807398a13ab7
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882154"
---
# <a name="implementation-of-a-custom-string-manager-advanced-method"></a>Implémentation d’un gestionnaire de chaînes personnalisé (méthode avancée)
Dans des cas spéciaux, vous souhaiterez implémenter un gestionnaire de chaînes personnalisé qui change plus que du segment de mémoire est utilisé pour allouer de la mémoire. Dans ce cas, vous devez implémenter manuellement le [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interface en tant que gestionnaire de chaînes personnalisé.  
  
 Pour ce faire, il est important de comprendre d’abord comment [CStringT](../atl-mfc-shared/reference/cstringt-class.md) utilise cette interface pour gérer ses données de chaîne. Chaque instance de `CStringT` possède un pointeur vers un [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) structure. Cette structure de longueur variable contient des informations importantes sur la chaîne (par exemple, longueur), ainsi que les données de caractères réel de la chaîne. Chaque gestionnaire de chaînes personnalisé est chargé d’allouer et libérer ces structures à la demande de `CStringT`.  
  
 Le `CStringData` structure comprend les quatre champs :  
  
-   [pStringMgr](../atl-mfc-shared/reference/cstringdata-class.md#pstringmgr) ce champ pointe vers le `IAtlStringMgr` interface utilisée pour gérer les données de type chaîne. Lorsque `CStringT` doit réallouer ou libérer la mémoire tampon de chaîne qu’elle appelle la réallocation ou méthodes gratuits de cette interface, en passant le `CStringData` structure en tant que paramètre. Lors de l’allocation un `CStringData` structure dans le Gestionnaire de chaînes, vous devez définir ce champ pour pointer vers le Gestionnaire de chaînes personnalisé.  
  
-   [nDataLength](../atl-mfc-shared/reference/cstringdata-class.md#ndatalength) ce champ contient la longueur logique actuelle de la chaîne stockée dans la mémoire tampon à l’exclusion du caractère null de fin. `CStringT` met à jour ce champ lorsque la longueur de la chaîne change. Lors de l’allocation un `CStringData` structure, le Gestionnaire de chaînes doit définissez ce champ à zéro. Quand vous réallouez une `CStringData` structure, le Gestionnaire de chaînes personnalisé doit laisser ce champ inchangé.  
  
-   [nAllocLength](../atl-mfc-shared/reference/cstringdata-class.md#nalloclength) ce champ contient le nombre maximal de caractères (à l’exclusion du caractère null de fin) qui peuvent être stockées dans cette mémoire tampon de chaîne sans la réallouer. Chaque fois que `CStringT` a besoin d’augmenter la longueur logique de la chaîne, il vérifie d’abord ce champ s’assurer que l’espace est suffisant dans la mémoire tampon. Si la vérification échoue, `CStringT` appelle le Gestionnaire de chaînes personnalisé pour réallouer la mémoire tampon. Lors de l’attribution ou de réallocation un `CStringData` structure, vous devez définir ce champ au moins le nombre de caractères demandés dans le *nChars* paramètre [IAtlStringMgr::Allocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#allocate) ou [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate). S’il existe davantage d’espace dans la mémoire tampon que prévu, vous pouvez définir cette valeur afin de refléter la quantité réelle d’espace disponible. Cela permet de `CStringT` pour agrandir la chaîne pour remplir l’intégralité de l’espace alloué avant d’avoir à effectuer un rappel dans le Gestionnaire de chaînes pour réallouer la mémoire tampon.  
  
-   [nRefs](../atl-mfc-shared/reference/cstringdata-class.md#nrefs) ce champ contient le nombre actuel de la référence de la mémoire tampon de chaîne. Si la valeur est 1, une seule instance de `CStringT` à l’aide de la mémoire tampon. En outre, l’instance est autorisé à lire et modifier le contenu de la mémoire tampon. Si la valeur est supérieure à un, plusieurs instances de `CStringT` pouvez utiliser la mémoire tampon. Étant donné que la mémoire tampon de caractères est partagé, `CStringT` uniquement les instances peuvent lire le contenu de la mémoire tampon. Pour modifier le contenu, `CStringT` effectue tout d’abord une copie de la mémoire tampon. Si la valeur est négative, seule une instance de `CStringT` à l’aide de la mémoire tampon. Dans ce cas, la mémoire tampon est considéré comme verrouillé. Quand un `CStringT` instance n’utilise une mémoire tampon verrouillée aucune autre instance de `CStringT` peuvent partager la mémoire tampon. Au lieu de cela, ces instances de créent une copie de la mémoire tampon avant de manipuler le contenu. En outre, le `CStringT` instance à l’aide de la mémoire tampon verrouillée n’essaie pas de partager la mémoire tampon de n’importe quel autre `CStringT` instance qui lui est assignée. Dans ce cas, le `CStringT` instance copie l’autre chaîne dans la mémoire tampon verrouillée.  
  
     Lors de l’allocation un `CStringData` structure, vous devez définir ce champ pour refléter le type de partage autorisé pour la mémoire tampon. Pour la plupart des implémentations, définissez cette valeur sur 1. Cela permet au comportement de partage de copie sur écriture normal. Toutefois, si votre gestionnaire de chaînes ne prend pas en charge le partage de la mémoire tampon de chaîne, définissez ce champ à un état verrouillé. Cela force `CStringT` à utiliser uniquement cette mémoire tampon pour l’instance de `CStringT` qui lui a été alloué.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

