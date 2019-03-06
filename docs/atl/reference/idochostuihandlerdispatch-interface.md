---
title: Idochostuihandlerdispatch, Interface
ms.date: 11/04/2016
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 6ce3532e99dc1d0ff0151285766aa5d78c2b9e9d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421880"
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
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Également appelés quand MSHTML affiche l’interface utilisateur modale.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Appelé sur l’hôte par MSHTML pour permettre à l’hôte remplacer l’objet de données de MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Appelé par MSHTML quand il est utilisé comme cible de déplacement pour permettre à l’hôte de fournir un autre [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget).|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Appelé par MSHTML pour obtenir l’interface IDispatch de l’hôte.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Récupère les fonctionnalités de l’interface utilisateur de l’hôte MSHTML.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Retourne la clé de Registre sous laquelle MSHTML stocke les préférences utilisateur.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Appelé lorsque MSHTML supprime ses menus et les barres d’outils.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Appelée à partir de l’implémentation de MSHTML de [IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Appelée à partir de MSHTML pour afficher un menu contextuel.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Permet à l’hôte remplacer les barres d’outils et les menus MSHTML.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Appelé par MSHTML lorsque [IOleInPlaceActiveObject::TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) ou [IOleControlSite::TranslateAccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) est appelée.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Appelé par MSHTML pour permettre à l’hôte modifier l’URL à charger.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Avertit l’hôte que l’état de la commande a changé.|

## <a name="remarks"></a>Notes

Un hôte peut remplacer les menus, barres d’outils et les menus contextuels utilisés par le moteur de rendu (MSHTML) et de l’analyse HTML de Microsoft en implémentant cette interface.

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible en tant que fichier IDL ou C++, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (également inclus dans ATLBase.h)|

## <a name="see-also"></a>Voir aussi

[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)
