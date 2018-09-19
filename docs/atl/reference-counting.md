---
title: Décompte de références (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9288eda15b0bac3d3694ee56a2f427aefb60e032
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086432"
---
# <a name="reference-counting"></a>Comptage de références

COM lui-même n’essaie pas automatiquement supprimer un objet de la mémoire lorsqu’il détermine que l’objet n’est plus utilisé. Au lieu de cela, le programmeur de l’objet doit supprimer l’objet inutilisé. Le programmeur détermine si un objet peut être supprimé en fonction d’un décompte de références.

COM utilise le `IUnknown` méthodes, [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) et [version](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), pour gérer le décompte de références des interfaces sur un objet. Les règles générales pour l’appel de ces méthodes sont :

- Chaque fois qu’un client reçoit un pointeur d’interface, `AddRef` doit être appelée sur l’interface.

- Chaque fois que le client a terminé d’utiliser le pointeur d’interface, il doit appeler `Release`.

Dans une implémentation simple, chaque `AddRef` appeler incrémente et chacun `Release` appeler décrémente une variable de compteur à l’intérieur de l’objet. Lorsque le compteur revient à zéro, l’interface n’est plus a tous les utilisateurs et est libre de supprimer lui-même de la mémoire.

Comptage de références peut également être implémentée afin que chaque référence à l’objet (pas une interface individuelle) est comptabilisé. Dans ce cas, chaque `AddRef` et `Release` appeler des délégués à une implémentation centrale sur l’objet, et `Release` libère l’objet entier lorsque son décompte de références atteint zéro.

> [!NOTE]
>  Quand un `CComObject`-objet dérivé est construit à l’aide de la **nouveau** opérateur, le décompte de références est 0. Par conséquent, un appel à `AddRef` doit être effectué après la création du `CComObject`-objet dérivé.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[La gestion des durées de vie des objets via le décompte](/windows/desktop/com/managing-object-lifetimes-through-reference-counting)

