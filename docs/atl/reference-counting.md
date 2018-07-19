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
ms.openlocfilehash: 8e0ce8b2cc412c576b0eded9662d8e70b34cf2ec
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850811"
---
# <a name="reference-counting"></a>Comptage de références
COM lui-même n’essaie pas automatiquement supprimer un objet de la mémoire lorsqu’il détermine que l’objet n’est plus utilisé. Au lieu de cela, le programmeur de l’objet doit supprimer l’objet inutilisé. Le programmeur détermine si un objet peut être supprimé en fonction d’un décompte de références.  
  
 COM utilise le `IUnknown` méthodes, [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) et [version](http://msdn.microsoft.com/library/windows/desktop/ms682317), pour gérer le décompte de références des interfaces sur un objet. Les règles générales pour l’appel de ces méthodes sont :  
  
-   Chaque fois qu’un client reçoit un pointeur d’interface, `AddRef` doit être appelée sur l’interface.  
  
-   Chaque fois que le client a terminé d’utiliser le pointeur d’interface, il doit appeler `Release`.  
  
 Dans une implémentation simple, chaque `AddRef` appeler incrémente et chacun `Release` appeler décrémente une variable de compteur à l’intérieur de l’objet. Lorsque le compteur revient à zéro, l’interface n’est plus a tous les utilisateurs et est libre de supprimer lui-même de la mémoire.  
  
 Comptage de références peut également être implémentée afin que chaque référence à l’objet (pas une interface individuelle) est comptabilisé. Dans ce cas, chaque `AddRef` et `Release` appeler des délégués à une implémentation centrale sur l’objet, et `Release` libère l’objet entier lorsque son décompte de références atteint zéro.  
  
> [!NOTE]
>  Quand un `CComObject`-objet dérivé est construit à l’aide de la **nouveau** opérateur, le décompte de références est 0. Par conséquent, un appel à `AddRef` doit être effectué après la création du `CComObject`-objet dérivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à COM](../atl/introduction-to-com.md)   
 [La gestion des durées de vie des objets via le décompte](http://msdn.microsoft.com/library/windows/desktop/ms687260)

