---
title: Quelle est la bibliothèque ATL API d’hébergement de contrôle ? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30b104e21259006da41c236c168431d85b43e0d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363244"
---
# <a name="what-is-the-atl-control-hosting-api"></a>Quelle est la bibliothèque ATL API d’hébergement de contrôle ?
ATL qui héberge le contrôle de l’API est l’ensemble de fonctions qui permet de n’importe quelle fenêtre d’agir comme un conteneur de contrôles ActiveX. Ces fonctions peuvent être statiquement ou dynamiquement liées dans votre projet, car elles sont disponibles en tant que code source et exposées par ATL90.dll. Les fonctions de contrôle d’hébergement sont répertoriées dans le tableau ci-dessous.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Crée un objet hôte, il se connecte à la fenêtre fournie, puis attache un contrôle existant.|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Crée un objet hôte, il se connecte à la fenêtre fournie, puis charge un contrôle.|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Crée un contrôle ActiveX sous licence, il initialise et héberge ce dernier dans la fenêtre spécifiée, semblable à [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Crée un objet hôte, il se connecte à la fenêtre fournie, puis charge un contrôle (permet également de configurer des récepteurs d’événements).|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Crée un contrôle ActiveX sous licence, il initialise et héberge ce dernier dans la fenêtre spécifiée, semblable à [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|  
|[API AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Crée une boîte de dialogue non modale à partir d’une ressource de boîte de dialogue et retourne le handle de fenêtre.|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Crée une boîte de dialogue modale à partir d’une ressource de boîte de dialogue.|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Retourne le **IUnknown** pointeur d’interface du contrôle hébergé dans une fenêtre.|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Retourne le **IUnknown** pointeur d’interface de l’objet hôte connecté à une fenêtre.|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Initialise le code d’hébergement du contrôle.|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|N’initialise pas le code d’hébergement du contrôle.|  
  
 Le `HWND` paramètres dans les trois premières fonctions doivent être une fenêtre existante de (presque) n’importe quel type. Si vous appelez une de ces trois fonctions explicitement (en règle générale, vous ne devez), ne passez pas un handle de fenêtre qui fait déjà Office en tant qu’hôte (dans ce cas, l’objet hôte existant ne serait pas libéré).  
  
 Les sept premières fonctions appellent [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implicitement.  
  
> [!NOTE]
>  L’API d’hébergement de contrôle constitue la base de prise en charge d’ATL pour les contrôles ActiveX. Toutefois, il est généralement pas nécessaire d’appeler ces fonctions directement si tirer parti d’ou de tirer pleinement parti des classes wrapper d’ATL. Pour plus d’informations, consultez [qui ATL Classes faciliter les contrôles ActiveX](which-atl-classes-facilitate-activex-control-containment-q.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Forum aux questions sur la contenance de contrôles](which-atl-classes-facilitate-activex-control-containment-q.md)
