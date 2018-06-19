---
title: Décompte de références (ATL) | Documents Microsoft
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
ms.openlocfilehash: d1ba27f00bf25f88575101b1299daf50f94000ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358246"
---
# <a name="reference-counting"></a>Comptage des références
COM n’essaie pas automatiquement de supprimer un objet de la mémoire lorsqu’il détermine que l’objet n’est plus utilisé. Au lieu de cela, le programmeur de l’objet doit supprimer l’objet d’inutilisé. Le programmeur détermine si un objet peut être supprimé en fonction du décompte de références.  
  
 COM utilise le **IUnknown** méthodes, [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) et [version](http://msdn.microsoft.com/library/windows/desktop/ms682317), pour gérer le décompte de références des interfaces sur un objet. Les règles générales pour l’appel de ces méthodes sont :  
  
-   Chaque fois qu’un client reçoit un pointeur d’interface, `AddRef` doit être appelée sur l’interface.  
  
-   Chaque fois que le client a terminé d’utiliser le pointeur d’interface, il doit appeler **version**.  
  
 Dans une implémentation simple, chaque `AddRef` appeler incréments et chaque **version** appeler décrémente une variable de compteur à l’intérieur de l’objet. Lorsque le compteur revient à zéro, l’interface n’est plus a tous les utilisateurs et peut se supprimer de la mémoire.  
  
 Comptage des références peut également être implémenté afin que chaque référence à l’objet (pas une interface individuelle) est comptabilisé. Dans ce cas, chaque `AddRef` et **version** appeler des délégués à une implémentation centrale sur l’objet, et **version** libère l’objet complet lorsque son décompte de références atteint zéro.  
  
> [!NOTE]
>  Lorsqu’un `CComObject`-objet dérivé est construit à l’aide de la **nouvelle** (opérateur), le nombre de références est 0. Par conséquent, un appel à `AddRef` doit être effectué après la création du `CComObject`-objet dérivé.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à COM](../atl/introduction-to-com.md)   
 [Gérer la durée de vie des objets via le décompte](http://msdn.microsoft.com/library/windows/desktop/ms687260)

