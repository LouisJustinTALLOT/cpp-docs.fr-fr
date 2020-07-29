---
title: Comptage de références (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: f90c818e58ae7ef6e4a0b771cb53ae5b185d1617
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224342"
---
# <a name="reference-counting"></a>Décompte de références

COM n’essaie pas automatiquement de supprimer un objet de la mémoire lorsqu’il pense que l’objet n’est plus utilisé. Au lieu de cela, le programmeur d’objets doit supprimer l’objet inutilisé. Le programmeur détermine si un objet peut être supprimé en fonction d’un décompte de références.

COM utilise les `IUnknown` méthodes, [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), pour gérer le décompte de références des interfaces sur un objet. Les règles générales pour l’appel de ces méthodes sont les suivantes :

- Chaque fois qu’un client reçoit un pointeur d’interface, `AddRef` doit être appelé sur l’interface.

- Chaque fois que le client a terminé d’utiliser le pointeur d’interface, il doit appeler `Release` .

Dans une implémentation simple, chaque `AddRef` appel est incrémenté et chaque `Release` appel décrémente une variable de compteur à l’intérieur de l’objet. Lorsque le nombre retourne à zéro, l’interface n’a plus d’utilisateurs et est libre de se supprimer de la mémoire.

Le décompte de références peut également être implémenté afin que chaque référence à l’objet (et non à une interface individuelle) soit comptée. Dans ce cas, chacun `AddRef` et `Release` appelle des délégués à une implémentation centrale sur l’objet et `Release` libère l’objet entier lorsque son décompte de références atteint zéro.

> [!NOTE]
> Lorsqu’un `CComObject` objet dérivé de est construit à l’aide de l' **`new`** opérateur, le nombre de références est égal à 0. Par conséquent, un appel à `AddRef` doit être effectué après la création réussie de l' `CComObject` objet dérivé de.

## <a name="see-also"></a>Voir aussi

[Introduction à COM](../atl/introduction-to-com.md)<br/>
[Gestion des durées de vie des objets via le décompte de références](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
