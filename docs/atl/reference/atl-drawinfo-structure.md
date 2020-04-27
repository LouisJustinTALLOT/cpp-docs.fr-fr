---
title: Structure ATL_DRAWINFO
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 00d93b3dd8b060a21b6ff4083bb9880d8d836a19
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168616"
---
# <a name="atl_drawinfo-structure"></a>Structure ATL_DRAWINFO

Contient des informations utilisées pour le rendu de différentes cibles, telles qu’une imprimante, un métafichier ou un contrôle ActiveX.

## <a name="syntax"></a>Syntaxe

```cpp
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
Taille de la structure en octets.

`dwDrawAspect`<br/>
Spécifie le mode de représentation de la cible. Les représentations peuvent inclure du contenu, une icône, une miniature ou un document imprimé. Pour obtenir la liste des valeurs possibles, consultez [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) et [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Partie de la cible qui présente un intérêt pour l’opération de dessin. Son interprétation varie en fonction de la valeur du `dwDrawAspect` membre.

`ptd`<br/>
Pointeur vers une structure [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) qui permet de dessiner des optimisations en fonction de l’aspect spécifié. Notez que les objets et les conteneurs les plus récents qui prennent en charge les interfaces de dessin optimisées prennent également en charge ce membre. Les objets et conteneurs plus anciens qui ne prennent pas en charge les interfaces de dessin optimisées spécifient toujours la valeur NULL pour ce membre.

`hicTargetDev`<br/>
Contexte d’informations de l’appareil cible vers `ptd` lequel l’objet peut extraire les métriques de l’appareil et tester les fonctionnalités de l’appareil. Si `ptd` a la valeur null, l’objet doit ignorer la valeur `hicTargetDev` dans le membre.

`hdcDraw`<br/>
Contexte de périphérique sur lequel dessiner. Pour un objet sans fenêtre, le `hdcDraw` membre est en mode `MM_TEXT` de mappage, avec ses coordonnées logiques correspondant aux coordonnées clientes de la fenêtre conteneur. En outre, le contexte de périphérique doit être dans le même État que celui normalement passé par un `WM_PAINT` message.

`prcBounds`<br/>
Pointeur vers une structure [Rect](/windows/win32/api/windef/ns-windef-rectl) qui spécifie le rectangle `hdcDraw` sur et dans lequel l’objet doit être dessiné. Ce membre contrôle le positionnement et l’étirement de l’objet. Ce membre doit avoir la valeur NULL pour dessiner un objet actif sur place sans fenêtre. Dans tous les autres cas, NULL n’est pas une valeur autorisée et doit générer `E_INVALIDARG` un code d’erreur. Si le conteneur passe une valeur non NULL à un objet sans fenêtre, l’objet doit restituer l’aspect demandé dans le contexte de périphérique et le rectangle spécifiés. Un conteneur peut demander cela à partir d’un objet sans fenêtre pour afficher une deuxième vue non active de l’objet ou pour imprimer l’objet.

`prcWBounds`<br/>
Si `hdcDraw` est un contexte de périphérique de métafichier (voir [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) dans le SDK Windows), il s’agit d' `RECTL` un pointeur vers une structure qui spécifie le rectangle englobant dans le métafichier sous-jacent. La structure rectangle contient l’étendue de la fenêtre et l’origine de la fenêtre. Ces valeurs sont utiles pour le dessin de recréations de fichiers. Le rectangle indiqué par `prcBounds` est imbriqué à l’intérieur `prcWBounds` de ce rectangle ; ils se trouvent dans le même espace de coordonnées.

`bOptimize`<br/>
Différent de zéro si le dessin du contrôle doit être optimisé ; sinon, 0. Si le dessin est optimisé, l’état du contexte de périphérique est automatiquement restauré lorsque vous avez terminé le rendu.

`bZoomed`<br/>
Différent de zéro si la cible a un facteur de zoom, sinon 0. Le facteur de zoom est stocké dans `ZoomNum`.

`bRectInHimetric`<br/>
Différent de zéro si les dimensions `prcBounds` de se trouvent dans HIMETRIC, sinon 0.

`ZoomNum`<br/>
Largeur et hauteur du rectangle dans lequel l’objet est rendu. Le facteur de zoom le long de l’axe x (la proportion de la taille naturelle de l’objet par rapport à son étendue actuelle) de la `ZoomNum.cx` cible est la valeur de `ZoomDen.cx`divisée par la valeur de. Le facteur de zoom sur l’axe y est obtenu de la même manière.

`ZoomDen`<br/>
Largeur et hauteur réelles de la cible.

## <a name="remarks"></a>Notes

L’utilisation classique de cette structure est la récupération d’informations pendant le rendu de l’objet cible. Par exemple, vous pouvez récupérer des valeurs à partir de ATL_DRAWINFO à l’intérieur de votre surcharge de [CComControlBase :: OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Cette structure stocke les informations pertinentes utilisées pour restituer l’apparence d’un objet pour l’appareil cible. Les informations fournies peuvent être utilisées pour dessiner à l’écran, une imprimante ou même un métafichier.

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)<br/>
[IViewObject ::D RAW](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
