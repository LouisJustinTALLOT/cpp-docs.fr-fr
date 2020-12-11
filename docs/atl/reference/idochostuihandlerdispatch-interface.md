---
description: 'En savoir plus sur : interface IDocHostUIHandlerDispatch'
title: Interface IDocHostUIHandlerDispatch
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 59f9975f48a7ae63d5820a9c05f9baa49b8a5f25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158372"
---
# <a name="idochostuihandlerdispatch-interface"></a>Interface IDocHostUIHandlerDispatch

Interface au moteur d’analyse et de rendu HTML de Microsoft.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

> [!NOTE]
> Les liens figurant dans le tableau suivant concernent les rubriques de référence du kit de développement logiciel (SDK) INet pour les membres de l’interface [IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\)) . `IDocHostUIHandlerDispatch` a la même fonctionnalité que `IDocUIHostHandler` , à la différence qu’il `IDocHostUIHandlerDispatch` s’agit d’une dispinterface, tandis que `IDocUIHostHandler` est une interface personnalisée.

|Nom|Description|
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|Appelé à partir de l’implémentation MSHTML de [IOleInPlaceActiveObject :: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless). Également appelé lorsque MSHTML affiche l’interface utilisateur modale.|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|Appelé sur l’hôte par MSHTML pour permettre à l’hôte de remplacer l’objet de données de MSHTML.|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|Appelée par MSHTML quand il est utilisé comme cible de déplacement pour permettre à l’hôte de fournir un autre [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget).|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|Appelée par MSHTML pour obtenir l’interface IDispatch de l’hôte.|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|Récupère les fonctionnalités d’interface utilisateur de l’hôte MSHTML.|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|Retourne la clé de Registre sous laquelle MSHTML stocke les préférences de l’utilisateur.|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|Appelé lorsque MSHTML supprime ses menus et barres d’outils.|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|Appelé à partir de l’implémentation MSHTML de [IOleInPlaceActiveObject :: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate).|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|Appelé à partir de l’implémentation MSHTML de [IOleInPlaceActiveObject :: OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate).|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|Appelé à partir de l’implémentation MSHTML de [IOleInPlaceActiveObject :: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder).|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|Appelé à partir de MSHTML pour afficher un menu contextuel.|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|Permet à l’hôte de remplacer des menus et des barres d’outils MSHTML.|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|Appelée par MSHTML quand [IOleInPlaceActiveObject :: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) ou [IOleControlSite :: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator) est appelé.|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|Appelée par MSHTML pour permettre à l’hôte de modifier l’URL à charger.|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|Avertit l’hôte que l’état de la commande a changé.|

## <a name="remarks"></a>Notes

Un hôte peut remplacer les menus, les barres d’outils et les menus contextuels utilisés par le moteur d’analyse et de rendu HTML de Microsoft (MSHTML) en implémentant cette interface.

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible en tant que IDL ou C++, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|MIDL|ATLIFace. idl|
|C++|ATLIFace. h (également inclus dans ATLBase. h)|

## <a name="see-also"></a>Voir aussi

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
