---
title: ATL_DRAWINFO Structure
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: fb50f49d387e8620f3d5bbb41263738adbd8b437
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748804"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO Structure

Contient des informations utilisées pour le rendu à diverses cibles, telles qu’une imprimante, un métadilile ou un contrôle ActiveX.

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
La taille de la structure, dans les octets.

`dwDrawAspect`<br/>
Précise comment la cible doit être représentée. Les représentations peuvent inclure du contenu, une icône, une vignette ou un document imprimé. Pour une liste de valeurs possibles, voir [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) et [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Partie de la cible qui est d’intérêt pour l’opération de tirage. Son interprétation varie en fonction `dwDrawAspect` de la valeur du membre.

`ptd`<br/>
Pointeur vers une structure [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) qui permet d’optimiser les dessins en fonction de l’aspect spécifié. Notez que les nouveaux objets et conteneurs qui prennent en charge les interfaces de dessin optimisées prennent en charge ce membre ainsi. Les objets et les conteneurs plus anciens qui ne prennent pas en charge les interfaces de dessin optimisées spécifient toujours NULL pour ce membre.

`hicTargetDev`<br/>
Contexte d’information pour le `ptd` dispositif cible indiqué par lequel l’objet peut extraire des mesures de périphérique et tester les capacités de l’appareil. S’il `ptd` est NULL, l’objet `hicTargetDev` doit ignorer la valeur dans le membre.

`hdcDraw`<br/>
Le contexte de l’appareil sur lequel dessiner. Pour un objet sans `hdcDraw` fenêtre, `MM_TEXT` le membre est en mode de cartographie avec ses coordonnées logiques correspondant aux coordonnées client de la fenêtre contenante. En outre, le contexte de l’appareil doit être dans `WM_PAINT` le même état que celui normalement passé par un message.

`prcBounds`<br/>
Pointeur vers une structure [RECTL](/windows/win32/api/windef/ns-windef-rectl) spécifiant le rectangle sur `hdcDraw` et dans lequel l’objet doit être dessiné. Ce membre contrôle le positionnement et l’étirement de l’objet. Ce membre doit être NULL pour dessiner un objet actif sans fenêtre en place. Dans toutes les autres situations, NULL n’est `E_INVALIDARG` pas une valeur juridique et devrait entraîner un code d’erreur. Si le conteneur passe une valeur non-NULL à un objet sans fenêtre, l’objet doit rendre l’aspect demandé dans le contexte et le rectangle spécifiés de l’appareil. Un conteneur peut le demander à partir d’un objet sans fenêtre pour rendre une deuxième vue non active de l’objet ou pour imprimer l’objet.

`prcWBounds`<br/>
S’il `hdcDraw` s’agit d’un contexte d’appareil métaafile (voir [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) dans le SDK Windows), il s’agit d’un pointeur vers une `RECTL` structure spécifiant le rectangle de délimitation dans le métaafile sous-jacent. La structure du rectangle contient l’étendue de la fenêtre et l’origine de la fenêtre. Ces valeurs sont utiles pour dessiner des métafiles. Le rectangle `prcBounds` indiqué par est `prcWBounds` imbriqué à l’intérieur de ce rectangle; ils sont dans le même espace de coordonnées.

`bOptimize`<br/>
Nonzero si le dessin du contrôle doit être optimisé, sinon 0. Si le dessin est optimisé, l’état du contexte de l’appareil est automatiquement restauré lorsque vous avez terminé le rendu.

`bZoomed`<br/>
Nonzero si la cible a un facteur de zoom, sinon 0. Le facteur zoom `ZoomNum`est stocké dans .

`bRectInHimetric`<br/>
Nonzero si les `prcBounds` dimensions de sont hiMETRIC, sinon 0.

`ZoomNum`<br/>
La largeur et la hauteur du rectangle dans lequel l’objet est rendu. Le facteur de zoom le long de l’axe x (la proportion de la taille `ZoomNum.cx` naturelle de `ZoomDen.cx`l’objet dans son étendue actuelle) de la cible est la valeur de divisé par la valeur de . Le facteur de zoom le long de l’axe y est réalisé de la même manière.

`ZoomDen`<br/>
La largeur et la hauteur réelles de la cible.

## <a name="remarks"></a>Notes

L’utilisation typique de cette structure serait la récupération d’informations lors du rendu de l’objet cible. Par exemple, vous pouvez récupérer des valeurs de ATL_DRAWINFO à l’intérieur de votre surcharge de [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Cette structure stocke les informations pertinentes utilisées pour rendre l’apparence d’un objet pour l’appareil cible. Les informations fournies peuvent être utilisées pour dessiner à l’écran, une imprimante ou même un métaafile.

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="see-also"></a>Voir aussi

[Classes et structs](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
