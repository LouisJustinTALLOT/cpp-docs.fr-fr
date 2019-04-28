---
title: Atl_drawinfo, Structure
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 70329d3b2c18c8cd8e94854f40ff971c0b39a8f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261063"
---
# <a name="atldrawinfo-structure"></a>Atl_drawinfo, Structure

Contient des informations utilisées pour le rendu à différentes cibles, comme une imprimante, un métafichier ou un contrôle ActiveX.

## <a name="syntax"></a>Syntaxe

```
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```

## <a name="members"></a>Membres

`cbSize`<br/>
La taille de la structure, en octets.

`dwDrawAspect`<br/>
Spécifie la manière dont la cible doit être représenté. Représentations peuvent inclure contenu, une icône, une miniature ou un document imprimé. Pour obtenir la liste des valeurs possibles, consultez [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) et [DVASPECT2](/windows/desktop/api/ocidl/ne-ocidl-tagdvaspect2).

`lindex`<br/>
Partie de la cible présente un intérêt pour l’opération de dessin. Son interprétation varie en fonction de la valeur dans la `dwDrawAspect` membre.

`ptd`<br/>
Pointeur vers un [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) structure qui permet des optimisations de dessins selon l’aspect spécifié. Notez que les plus récentes des objets et des conteneurs qui prennent en charge les interfaces de dessins optimisés prend en charge également ce membre. Anciens objets et conteneurs qui ne prennent pas en charge les interfaces de dessins optimisés toujours spécifient NULL pour ce membre.

`hicTargetDev`<br/>
Contexte d’informations pour l’appareil cible vers lequel pointe `ptd` à partir duquel l’objet peut extraire les métriques du périphérique et tester les fonctions du périphérique. Si `ptd` est NULL, l’objet doit ignorer la valeur dans la `hicTargetDev` membre.

`hdcDraw`<br/>
Le contexte de périphérique sur lequel dessiner. Pour un objet sans fenêtre, le `hdcDraw` membre ne figure dans la `MM_TEXT` mode de mappage avec ses coordonnées logiques mise en correspondance les coordonnées clientes de la fenêtre conteneur. En outre, le contexte de périphérique doit être dans le même état que celui normalement passé par un `WM_PAINT` message.

`prcBounds`<br/>
Pointeur vers un [RECTL](https://msdn.microsoft.com/library/windows/desktop/dd162907) structure qui spécifie le rectangle sur `hdcDraw` et dans lequel l’objet doit être dessiné. Ce membre contrôle le positionnement et l’étirement de l’objet. Ce membre doit être NULL pour dessiner un objet actif sur place sans fenêtre. Dans tous les autres cas, la valeur NULL n’est pas une valeur autorisée et doit aboutir à un `E_INVALIDARG` code d’erreur. Si le conteneur passe une valeur non NULL à un objet sans fenêtre, l’objet doit restituer l’aspect demandée dans le contexte de périphérique spécifié et le rectangle. Un conteneur peut demander ce à partir d’un objet sans fenêtre pour restituer une vue deuxième, non actif de l’objet ou pour imprimer l’objet.

`prcWBounds`<br/>
Si `hdcDraw` est un contexte de périphérique de métafichier (consultez [GetDeviceCaps](/windows/desktop/api/wingdi/nf-wingdi-getdevicecaps) dans le SDK Windows), il s’agit d’un pointeur vers un `RECTL` structure qui spécifie le rectangle englobant dans le métafichier sous-jacent. La structure rectangle contient l’étendue de la fenêtre et l’origine de la fenêtre. Ces valeurs sont utiles pour dessiner des métafichiers. Le rectangle indiqué par `prcBounds` est imbriqué au sein de cet `prcWBounds` rectangle ; elles se trouvent dans le même espace de coordonnées.

`bOptimize`<br/>
Différent de zéro si le dessin du contrôle soit optimisé, sinon 0. Si le dessin est optimisé, l’état du contexte de périphérique est automatiquement restauré lorsque vous avez terminé le rendu.

`bZoomed`<br/>
Différent de zéro si la cible a un facteur de zoom, sinon 0. Le facteur de zoom est stocké dans `ZoomNum`.

`bRectInHimetric`<br/>
Différent de zéro si les dimensions de `prcBounds` se trouvent dans HIMETRIC, sinon 0.

`ZoomNum`<br/>
La largeur et la hauteur du rectangle dans lequel l’objet est affiché. Le facteur de zoom sur l’axe x (la proportion de la taille naturelle de l’objet à son étendue actuelle) de la cible est la valeur de `ZoomNum.cx` divisée par la valeur de `ZoomDen.cx`. Le facteur de zoom le long de l’axe des ordonnées s’effectue de manière similaire.

`ZoomDen`<br/>
La largeur réelle et la hauteur de la cible.

## <a name="remarks"></a>Notes

Une utilisation typique de cette structure serait la récupération d’informations pendant le rendu de l’objet cible. Par exemple, Impossible de récupérer des valeurs à partir de ATL_DRAWINFO à l’intérieur de votre surcharge de [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Cette structure stocke des informations pertinentes permettant de restituer l’apparence d’un objet pour l’appareil cible. Les informations fournies peuvent être utilisées dans un dessin à l’écran, une imprimante ou même un métafichier.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

## <a name="see-also"></a>Voir aussi

[Les classes et structs](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
