---
title: Interface de IDocHostUIHandlerDispatch | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
dev_langs:
- C++
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07d6d861bfa4a41d7d9ee6697dd72cba0da2ceda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364243"
---
# <a name="idochostuihandlerdispatch-interface"></a>Interface de IDocHostUIHandlerDispatch
Interface utilisée pour l’analyse Microsoft HTML et de moteur de rendu.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IDocHostUIHandlerDispatch : IDispatch
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
> [!NOTE]
>  Les liens dans le tableau suivant sont INet SDK rubriques de référence pour les membres de la [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx) interface. `IDocHostUIHandlerDispatch` a les mêmes fonctionnalités que **IDocUIHostHandler**, la différence étant que `IDocHostUIHandlerDispatch` est une dispinterface alors que **IDocUIHostHandler** est une interface personnalisée.  
  
|||  
|-|-|  
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115). Également appelé lorsque MSHTML affiche l’interface utilisateur modale.|  
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|Appelé sur l’ordinateur hôte par MSHTML pour permettre à l’hôte remplacer l’objet de données de MSHTML.|  
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|Appelée par MSHTML quand il est utilisé comme cible de dépôt pour permettre à l’hôte de fournir un autre [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679).|  
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|Appelé par MSHTML pour obtenir l’interface IDispatch de l’ordinateur hôte.|  
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|Récupère les fonctionnalités de l’interface utilisateur de l’hôte MSHTML.|  
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|Retourne la clé de Registre sous laquelle MSHTML stocke les préférences de l’utilisateur.|  
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|Appelé lorsque MSHTML supprime ses menus et les barres d’outils.|  
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281).|  
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969).|  
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053).|  
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|Appelée à partir de MSHTML pour afficher un menu contextuel.|  
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|Permet à l’hôte remplacer les barres d’outils et les menus MSHTML.|  
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|Appelée par MSHTML lorsque [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) ou [IOleControlSite::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693756) est appelée.|  
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|Appelé par MSHTML pour permettre à l’hôte modifier l’URL à charger.|  
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|Avertit l’hôte que l’état de la commande a changé.|  
  
## <a name="remarks"></a>Notes  
 Un hôte peut remplacer les menus, barres d’outils et les menus contextuels utilisés par le moteur de rendu (MSHTML) et de l’analyse Microsoft HTML en implémentant cette interface.  
  
## <a name="requirements"></a>Spécifications  
 La définition de cette interface est disponible en tant que fichier IDL ou C++, comme indiqué ci-dessous.  
  
|Type de définition|Fichier|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (également inclus dans ATLBase.h)|  
  
## <a name="see-also"></a>Voir aussi  
 [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)









