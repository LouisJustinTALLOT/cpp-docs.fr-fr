---
title: Hébergement de contrôles ActiveX à l’aide d’ATL AXHost | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2T class
- Calendar control (ActiveX), hosting with ATL AXHost
- Calendar control (ActiveX)
- ActiveX controls [C++], hosting
- hosting ActiveX controls
- AXHost method
ms.assetid: 2c1200ec-effb-4814-820a-509519699468
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e26fd9e80b96c2b0196e3fd0e11b9c97f0f3bff3
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027204"
---
# <a name="hosting-activex-controls-using-atl-axhost"></a>Hébergement de contrôles ActiveX à l’aide d’ATL AXHost
L’exemple dans cette rubrique montre comment créer AXHost et comment héberger un contrôle ActiveX à l’aide de différentes fonctions ATL. Il montre également comment accéder aux événements de contrôle et le récepteur (à l’aide de [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) à partir du contrôle hébergé. L’exemple héberge le contrôle calendrier dans une fenêtre principale ou dans une fenêtre enfant.  
  
 Notez que la définition du symbole USE_METHOD. Vous pouvez modifier la valeur de ce symbole pour faire varier entre 1 et 8. La valeur du symbole détermine comment le contrôle sera créé :  
  
-   Pour les paires de valeurs de USE_METHOD, l’appel pour créer l’hôte sous-classe une fenêtre et le convertit en un hôte de contrôle. Pour les valeurs impaires, le code crée une fenêtre enfant qui agit en tant qu’hôte.  
  
-   Pour les valeurs de USE_METHOD entre 1 et 4, l’accès au contrôle et la réception des événements sont réalisées dans l’appel qui crée également l’hôte. Valeurs comprises entre 5 et 8 interrogent l’hôte pour les interfaces et la raccordent le récepteur.  
  
Voici un résumé :  
  
|USE_METHOD|Hôte|Contrôler l’accès et la réception d’événements|Fonction démontrée|  
|-----------------|----------|--------------------------------------|---------------------------|  
|1|Fenêtre enfant|Une seule étape|CreateControlLicEx|  
|2|Fenêtre principale|Une seule étape|AtlAxCreateControlLicEx|  
|3|Fenêtre enfant|Une seule étape|CreateControlEx|  
|4|Fenêtre principale|Une seule étape|AtlAxCreateControlEx|  
|5|Fenêtre enfant|Plusieurs étapes|CreateControlLic|  
|6|Fenêtre principale|Plusieurs étapes|AtlAxCreateControlLic|  
|7|Fenêtre enfant|Plusieurs étapes|CreateControl|  
|8|Fenêtre principale|Plusieurs étapes|AtlAxCreateControl|  
  
 [!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions sur la contenance de contrôles](../atl/atl-control-containment-faq.md)   
 [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)   
 [AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)   
 [AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)   
 [CAxWindow2T classe](../atl/reference/caxwindow2t-class.md)   
 [IAxWinHostWindowLic, interface](../atl/reference/iaxwinhostwindowlic-interface.md)

