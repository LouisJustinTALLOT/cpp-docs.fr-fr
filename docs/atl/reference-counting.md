---
title: Comptage de référence (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 095f0ad2ecc1e1a870077899d61a3c594f8cc95f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321740"
---
# <a name="reference-counting"></a>Comptage de référence

COM lui-même n’essaie pas automatiquement de supprimer un objet de la mémoire quand il pense que l’objet n’est plus utilisé. Au lieu de cela, le programmeur d’objets doit supprimer l’objet inutilisé. Le programmeur détermine si un objet peut être supprimé en fonction d’un décompte de référence.

COM utilise `IUnknown` les méthodes, [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), pour gérer le nombre de références des interfaces sur un objet. Les règles générales d’appel de ces méthodes sont les :

- Chaque fois qu’un `AddRef` client reçoit un pointeur d’interface, doit être appelé sur l’interface.

- Chaque fois que le client a fini `Release`d’utiliser le pointeur d’interface, il doit appeler .

Dans une mise `AddRef` en œuvre simple, chaque appel incréments et chaque `Release` appel décrète une variable de compteur à l’intérieur de l’objet. Lorsque le nombre revient à zéro, l’interface n’a plus d’utilisateurs et est libre de se retirer de la mémoire.

Le comptage des références peut également être mis en œuvre de sorte que chaque référence à l’objet (et non à une interface individuelle) soit comptabilisée. Dans ce cas, chacun `AddRef` et `Release` appeler les délégués `Release` à une implémentation centrale sur l’objet, et libère l’objet entier lorsque son nombre de références atteint zéro.

> [!NOTE]
> Lorsqu’un `CComObject`objet dérivé est construit à l’aide du **nouvel** opérateur, le nombre de références est de 0. Par conséquent, `AddRef` un appel doit être `CComObject`fait après avoir réussi à créer l’objet dérivé.

## <a name="see-also"></a>Voir aussi

[Introduction à COM](../atl/introduction-to-com.md)<br/>
[Gérer les durées de vie des objets par le comptage des références](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
