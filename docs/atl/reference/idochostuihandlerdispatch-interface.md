---
title: IDocHostUIHandlerDispatch Interface
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: b7072b80b738aa12635427a2604b38fb3585b452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329725"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch Interface

Une interface pour le moteur microsoft d’analyse et de rendu HTML.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

> [!NOTE]
> Les liens dans le tableau suivant sont aux sujets de référence INet SDK pour les membres de [l’interface IDocUIHostHandler.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) `IDocHostUIHandlerDispatch`a la même `IDocUIHostHandler`fonctionnalité que , `IDocHostUIHandlerDispatch` avec la différence étant `IDocUIHostHandler` qui est un dispinterface alors qu’il s’agit d’une interface personnalisée.

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Appelé de la mise en œuvre MSHTML de [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Aussi appelé lorsque MSHTML affiche l’interface utilisateur modale.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Appelé à l’hôte par MSHTML pour permettre à l’hôte de remplacer l’objet de données de MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Appelé par MSHTML quand il est utilisé comme une cible de chute pour permettre à l’hôte de fournir une alternative [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[GetExternal GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Appelé par MSHTML pour obtenir l’interface IDispatch de l’hôte.|
|[GetHostInfo (en anglais)](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Récupère les capacités d’interface utilisateur de l’hôte MSHTML.|
|[GetOptionKeyPath (en)](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Retourne la clé de registre en vertu de laquelle MSHTML stocke les préférences des utilisateurs.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Appelé lorsque MSHTML supprime ses menus et ses barres d’outils.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Appelé de la mise en œuvre MSHTML de [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[SurFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Appelé de la mise en œuvre MSHTML de [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder (resizeBorder)](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Appelé de la mise en œuvre MSHTML de [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Appelé de MSHTML pour afficher un menu contextuelle.|
|[ShowUI ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Permet à l’hôte de remplacer les menus ET les barres d’outils MSHTML.|
|[DéfinitionAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Appelé par MSHTML quand [IOleInPlaceActiveObject:TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) ou [IOleControlSite::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) est appelé.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Appelé par MSHTML pour permettre à l’hôte d’avoir la possibilité de modifier l’URL à charger.|
|[Mise à jourUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Avertit l’hôte que l’état de la commande a changé.|

## <a name="remarks"></a>Notes

Un hôte peut remplacer les menus, les barres d’outils et les menus contextuels utilisés par le moteur microsoft d’analyse et de rendu HTML (MSHTML) en implémentant cette interface.

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible sous forme d’IDL ou de C, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (également inclus dans ATLBase.h)|

## <a name="see-also"></a>Voir aussi

[IDocUIHostHandler IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
