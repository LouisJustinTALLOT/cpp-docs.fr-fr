---
title: Ajout d’une fonctionnalité au contrôle Composite | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 67602e16fc5a30c82e82772b6b9f6c553ba79d9b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354180"
---
# <a name="adding-functionality-to-the-composite-control"></a>Ajout d’une fonctionnalité au contrôle Composite
Une fois que vous avez inséré les contrôles nécessaires dans le contrôle composite, l’étape suivante implique l’ajout de nouvelles fonctionnalités. Cette nouvelle fonctionnalité se situe généralement en deux catégories :  
  
-   Prise en charge des interfaces supplémentaires et de personnaliser le comportement de votre contrôle composite doté de fonctionnalités supplémentaires spécifiques.  
  
-   Gestion des événements à partir de la relation contenant-contenu contrôle ActiveX (ou contrôles).  
  
 Pour l’objectif et la portée de cet article, le reste de cette section se concentre uniquement sur la gestion des événements à partir de contrôles ActiveX.  
  
> [!NOTE]
>  Si vous avez besoin gérer les messages à partir de contrôles Windows, consultez [implémentation d’une fenêtre](../atl/implementing-a-window.md) pour plus d’informations sur la gestion des messages dans ATL.  
  
 Après avoir inséré un contrôle ActiveX dans la ressource de boîte de dialogue, cliquez sur le contrôle, puis cliquez sur **ajouter un gestionnaire d’événements**. Sélectionnez l’événement que vous souhaitez gérer et cliquez sur **ajouter et modifier des**. Le code de gestionnaire d’événements est ajouté pour le fichier .h du contrôle.  
  
 Points de connexion pour les contrôles ActiveX sur le contrôle composite sont automatiquement connectés et déconnectés via des appels à [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base des contrôles composites](../atl/atl-composite-control-fundamentals.md)

