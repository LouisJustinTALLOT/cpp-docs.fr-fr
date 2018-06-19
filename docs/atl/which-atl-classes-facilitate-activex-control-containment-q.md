---
title: Les Classes ATL facilitent la relation contenant-contenu de contrôle ActiveX ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
ms.assetid: 803a4605-7f4c-4139-8638-49d8783d31b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f024e9929e916e15b110bfc32bc704c4aef755a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361948"
---
# <a name="which-atl-classes-facilitate-activex-control-containment"></a>Les Classes ATL facilitent la relation contenant-contenu de contrôle ActiveX ?
Le code d’hébergement des contrôles ATL ne vous oblige à utiliser les classes ATL ; Vous pouvez simplement créer un **« AtlAxWin80 »** fenêtre et utilisez l’API d’hébergement du contrôle si nécessaire (pour plus d’informations, consultez **quel est l’API hébergeant des contrôles ATL**. Toutefois, les classes suivantes rendent les fonctionnalités de la relation contenant-contenu plus facile à utiliser.  
  
|Classe|Description|  
|-----------|-----------------|  
|[Objet CAxWindow](../atl/reference/caxwindow-class.md)|Encapsule une **« AtlAxWin80 »** fenêtre, en fournissant des méthodes pour la création de la fenêtre, création d’un contrôle et/ou attacher un contrôle à la fenêtre et la récupération des pointeurs d’interface sur l’objet hôte.|  
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Encapsule une **« AtlAxWinLic80 »** fenêtre, en fournissant des méthodes pour la création de la fenêtre, création d’un contrôle et/ou attacher un contrôle sous licence à la fenêtre et la récupération des pointeurs d’interface sur l’objet hôte.|  
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Agit comme une classe de base pour les classes de contrôle ActiveX basées sur une ressource de boîte de dialogue. Ces contrôles peuvent contenir d’autres contrôles ActiveX.|  
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Agit comme une classe de base pour les classes de boîte de dialogue basées sur une ressource de boîte de dialogue. Ces boîtes de dialogue peuvent contenir des contrôles ActiveX.|  
|[CWindow](../atl/reference/cwindow-class.md)|Fournit une méthode, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), qui retourne un pointeur d’interface sur un contrôle, en fonction de l’ID de sa fenêtre hôte. En outre, les wrappers Windows API exposées par `CWindow` généralement faciliter la gestion des fenêtres.|  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions sur la contenance de contrôles](../atl/atl-control-containment-faq.md)

