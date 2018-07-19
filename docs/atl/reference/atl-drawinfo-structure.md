---
title: Atl_drawinfo, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa45822d51d704022e773f6c8220db34b010a805
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885820"
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
 `cbSize`  
 La taille de la structure, en octets.  
  
 `dwDrawAspect`  
 Spécifie la manière dont la cible doit être représenté. Représentations peuvent inclure contenu, une icône, une miniature ou un document imprimé. Pour obtenir la liste des valeurs possibles, consultez [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) et [DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644).  
  
 `lindex`  
 Partie de la cible présente un intérêt pour l’opération de dessin. Son interprétation varie en fonction de la valeur dans la `dwDrawAspect` membre.  
  
 `ptd`  
 Pointeur vers un [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) structure qui permet des optimisations de dessins selon l’aspect spécifié. Notez que les plus récentes des objets et des conteneurs qui prennent en charge les interfaces de dessins optimisés prend en charge également ce membre. Anciens objets et conteneurs qui ne prennent pas en charge les interfaces de dessins optimisés toujours spécifient NULL pour ce membre.  
  
 `hicTargetDev`  
 Contexte d’informations pour l’appareil cible vers lequel pointe `ptd` à partir duquel l’objet peut extraire les métriques du périphérique et tester les fonctions du périphérique. Si `ptd` est NULL, l’objet doit ignorer la valeur dans la `hicTargetDev` membre.  
  
 `hdcDraw`  
 Le contexte de périphérique sur lequel dessiner. Pour un objet sans fenêtre, le `hdcDraw` membre ne figure dans la `MM_TEXT` mode de mappage avec ses coordonnées logiques mise en correspondance les coordonnées clientes de la fenêtre conteneur. En outre, le contexte de périphérique doit être dans le même état que celui normalement passé par un `WM_PAINT` message.  
  
 `prcBounds`  
 Pointeur vers un [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) structure qui spécifie le rectangle sur `hdcDraw` et dans lequel l’objet doit être dessiné. Ce membre contrôle le positionnement et l’étirement de l’objet. Ce membre doit être NULL pour dessiner un objet actif sur place sans fenêtre. Dans tous les autres cas, la valeur NULL n’est pas une valeur autorisée et doit aboutir à un `E_INVALIDARG` code d’erreur. Si le conteneur passe une valeur non NULL à un objet sans fenêtre, l’objet doit restituer l’aspect demandée dans le contexte de périphérique spécifié et le rectangle. Un conteneur peut demander ce à partir d’un objet sans fenêtre pour restituer une vue deuxième, non actif de l’objet ou pour imprimer l’objet.  
  
 `prcWBounds`  
 Si `hdcDraw` est un contexte de périphérique de métafichier (consultez [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) dans le SDK Windows), il s’agit d’un pointeur vers un `RECTL` structure qui spécifie le rectangle englobant dans le métafichier sous-jacent. La structure rectangle contient l’étendue de la fenêtre et l’origine de la fenêtre. Ces valeurs sont utiles pour dessiner des métafichiers. Le rectangle indiqué par `prcBounds` est imbriqué au sein de cet `prcWBounds` rectangle ; elles se trouvent dans le même espace de coordonnées.  
  
 `bOptimize`  
 Différent de zéro si le dessin du contrôle soit optimisé, sinon 0. Si le dessin est optimisé, l’état du contexte de périphérique est automatiquement restauré lorsque vous avez terminé le rendu.  
  
 `bZoomed`  
 Différent de zéro si la cible a un facteur de zoom, sinon 0. Le facteur de zoom est stocké dans `ZoomNum`.  
  
 `bRectInHimetric`  
 Différent de zéro si les dimensions de `prcBounds` se trouvent dans HIMETRIC, sinon 0.  
  
 `ZoomNum`  
 La largeur et la hauteur du rectangle dans lequel l’objet est affiché. Le facteur de zoom sur l’axe x (la proportion de la taille naturelle de l’objet à son étendue actuelle) de la cible est la valeur de `ZoomNum.cx` divisée par la valeur de `ZoomDen.cx`. Le facteur de zoom le long de l’axe des ordonnées s’effectue de manière similaire.  
  
 `ZoomDen`  
 La largeur réelle et la hauteur de la cible.  
  
## <a name="remarks"></a>Notes  
 Une utilisation typique de cette structure serait la récupération d’informations pendant le rendu de l’objet cible. Par exemple, Impossible de récupérer des valeurs à partir de ATL_DRAWINFO à l’intérieur de votre surcharge de [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).  
  
 Cette structure stocke des informations pertinentes permettant de restituer l’apparence d’un objet pour l’appareil cible. Les informations fournies peuvent être utilisées dans un dessin à l’écran, une imprimante ou même un métafichier.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlctl.h  
  
## <a name="see-also"></a>Voir aussi  
  [Les classes et structs](../../atl/reference/atl-classes.md) [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





