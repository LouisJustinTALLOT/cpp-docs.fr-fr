---
title: Idochostuihandlerdispatch, Interface
ms.date: 11/04/2016
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 5bf405f66bdef54f354f9e6c230207d2933ee352
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483630"
---
# <a name="idochostuihandlerdispatch-interface"></a>Idochostuihandlerdispatch, Interface

Une interface pour le moteur de rendu et de l’analyse HTML de Microsoft.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

> [!NOTE]
>  Les liens dans le tableau suivant sont INet SDK rubriques de référence pour les membres de la [IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx) interface. `IDocHostUIHandlerDispatch` a les mêmes fonctionnalités que `IDocUIHostHandler`, la différence étant que `IDocHostUIHandlerDispatch` est une dispinterface tandis que `IDocUIHostHandler` est une interface personnalisée.

|||
|-|-|
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Également appelés quand MSHTML affiche l’interface utilisateur modale.|
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|Appelé sur l’hôte par MSHTML pour permettre à l’hôte remplacer l’objet de données de MSHTML.|
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|Appelé par MSHTML quand il est utilisé comme cible de déplacement pour permettre à l’hôte de fournir un autre [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|Appelé par MSHTML pour obtenir l’interface IDispatch de l’hôte.|
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|Récupère les fonctionnalités de l’interface utilisateur de l’hôte MSHTML.|
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|Retourne la clé de Registre sous laquelle MSHTML stocke les préférences utilisateur.|
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|Appelé lorsque MSHTML supprime ses menus et les barres d’outils.|
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|Appelée à partir de MSHTML pour afficher un menu contextuel.|
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|Permet à l’hôte remplacer les barres d’outils et les menus MSHTML.|
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|Appelé par MSHTML lorsque [IOleInPlaceActiveObject::TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) ou [IOleControlSite::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) est appelée.|
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|Appelé par MSHTML pour permettre à l’hôte modifier l’URL à charger.|
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|Avertit l’hôte que l’état de la commande a changé.|

## <a name="remarks"></a>Notes

Un hôte peut remplacer les menus, barres d’outils et les menus contextuels utilisés par le moteur de rendu (MSHTML) et de l’analyse HTML de Microsoft en implémentant cette interface.

## <a name="requirements"></a>Configuration requise

La définition de cette interface est disponible en tant que fichier IDL ou C++, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (également inclus dans ATLBase.h)|

## <a name="see-also"></a>Voir aussi

[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)

