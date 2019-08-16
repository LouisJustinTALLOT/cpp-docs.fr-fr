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
ms.openlocfilehash: 565b74956280d4e80c41376ead4249e69980a80e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492218"
---
# <a name="reference-counting"></a>Décompte de références

COM n’essaie pas automatiquement de supprimer un objet de la mémoire lorsqu’il pense que l’objet n’est plus utilisé. Au lieu de cela, le programmeur d’objets doit supprimer l’objet inutilisé. Le programmeur détermine si un objet peut être supprimé en fonction d’un décompte de références.

COM utilise les `IUnknown` méthodes, [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) et [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), pour gérer le décompte de références des interfaces sur un objet. Les règles générales pour l’appel de ces méthodes sont les suivantes:

- Chaque fois qu’un client reçoit un pointeur `AddRef` d’interface, doit être appelé sur l’interface.

- Chaque fois que le client a terminé d’utiliser le pointeur d’interface `Release`, il doit appeler.

Dans une implémentation simple, chaque `AddRef` appel est incrémenté et `Release` chaque appel décrémente une variable de compteur à l’intérieur de l’objet. Lorsque le nombre retourne à zéro, l’interface n’a plus d’utilisateurs et est libre de se supprimer de la mémoire.

Le décompte de références peut également être implémenté afin que chaque référence à l’objet (et non à une interface individuelle) soit comptée. Dans ce cas, chacun `AddRef` et `Release` appelle des délégués à une implémentation centrale sur l’objet et `Release` libère l’objet entier lorsque son décompte de références atteint zéro.

> [!NOTE]
>  Lorsqu’un `CComObject`objet dérivé de est construit à l’aide de l’opérateur **New** , le nombre de références est égal à 0. Par conséquent, un appel `AddRef` à doit être effectué après la création `CComObject`réussie de l’objet dérivé de.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Gestion des durées de vie des objets via le décompte de références](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
