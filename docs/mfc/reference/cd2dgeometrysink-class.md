---
title: Classe de CD2DGeometrySink | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89286aaccd2c59efb2bac14978a2d8838af7a4e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink, classe
Wrapper pour ID2D1GeometrySink.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DGeometrySink;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Construit un objet CD2DGeometrySink à partir de l’objet de CD2DPathGeometry.|  
|[CD2DGeometrySink :: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|Destructeur. Appelé lorsqu’un objet récepteur de géométrie D2D est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](#addarc)|Ajoute un arc unique à la géométrie de tracé|  
|[CD2DGeometrySink::AddBezier](#addbezier)|Crée une courbe de Bézier cubique lissée entre le point actuel et le point de fin spécifié.|  
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Crée une séquence de courbes de Bézier cubiques et les ajoute au récepteur de la géométrie.|  
|[CD2DGeometrySink::AddLine](#addline)|Crée un segment de ligne entre le point actuel et le point de terminaison spécifié et l’ajoute au récepteur de la géométrie.|  
|[CD2DGeometrySink::AddLines](#addlines)|Crée une séquence de lignes à l’aide de points spécifiés et les ajoute au récepteur de la géométrie.|  
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Crée une courbe de Bézier quadratique lissée entre le point actuel et le point de fin spécifié.|  
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Ajoute une séquence de segments de Bézier quadratiques sous forme de tableau dans un seul appel.|  
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Démarre une nouvelle figure au point spécifié.|  
|[CD2DGeometrySink::Close](#close)|Ferme le récepteur de la géométrie|  
|[CD2DGeometrySink::EndFigure](#endfigure)|Termine la figure en cours ; Si vous le souhaitez, le ferme.|  
|[CD2DGeometrySink::Get](#get)|Renvoie l’interface ID2D1GeometrySink|  
|[CD2DGeometrySink::IsValid](#isvalid)|Vérifie la validité du récepteur de géométrie|  
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Spécifie la méthode utilisée pour déterminer les points situés à l’intérieur de la géométrie décrite par ce récepteur de la géométrie et les points situés à l’extérieur.|  
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Spécifie les options de trait et de jointure à appliquer aux nouveaux segments ajoutés au récepteur de la géométrie.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|Renvoie l’interface ID2D1GeometrySink|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CD2DGeometrySink::m_pSink](#m_psink)|Pointeur vers un ID2D1GeometrySink.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CD2DGeometrySink`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink :: ~ CD2DGeometrySink  
 Destructeur. Appelé lorsqu’un objet récepteur de géométrie D2D est détruit.  
  
```  
virtual ~CD2DGeometrySink();
```  
  
##  <a name="addarc"></a>CD2DGeometrySink::AddArc  
 Ajoute un arc unique à la géométrie de tracé  
  
```  
void AddArc(const D2D1_ARC_SEGMENT& arc);
```  
  
### <a name="parameters"></a>Paramètres  
 `arc`  
 Le segment d’arc à ajouter à la figure  
  
##  <a name="addbezier"></a>CD2DGeometrySink::AddBezier  
 Crée une courbe de Bézier cubique lissée entre le point actuel et le point de fin spécifié.  
  
```  
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>Paramètres  
 `bezier`  
 Structure qui décrit les points de contrôle et le point de terminaison de la courbe de Bézier à ajouter.  
  
##  <a name="addbeziers"></a>CD2DGeometrySink::AddBeziers  
 Crée une séquence de courbes de Bézier cubiques et les ajoute au récepteur de la géométrie.  
  
```  
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,  
    D2D1_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>Paramètres  
 `beziers`  
 Tableau des segments de Bézier qui décrit les courbes Bézier à créer. Une courbe est tracée à partir du point d’actuel du récepteur de la géométrie (le point de terminaison du dernier segment dessiné ou l’emplacement spécifié par BeginFigure) au point de terminaison du premier segment de Bézier dans le tableau. Si le tableau contient des segments de Bézier supplémentaires, chaque segment de Bézier consécutif utilise le point de terminaison du segment de Bézier précédent comme son point de départ.  
  
##  <a name="addline"></a>CD2DGeometrySink::AddLine  
 Crée un segment de ligne entre le point actuel et le point de terminaison spécifié et l’ajoute au récepteur de la géométrie.  
  
```  
void AddLine(CD2DPointF point);
```  
  
### <a name="parameters"></a>Paramètres  
 `point`  
 Le point de terminaison de la ligne à dessiner.  
  
##  <a name="addlines"></a>CD2DGeometrySink::AddLines  
 Crée une séquence de lignes à l’aide de points spécifiés et les ajoute au récepteur de la géométrie.  
  
```  
void AddLines(
    const CArray<CD2DPointF,  
    CD2DPointF>& points);
```  
  
### <a name="parameters"></a>Paramètres  
 `points`  
 Tableau d’un ou plusieurs points qui décrivent les lignes à tracer. Une ligne est tracée à partir du point d’actuel du récepteur de la géométrie (le point de terminaison du dernier segment dessiné ou l’emplacement spécifié par BeginFigure) et le premier point dans le tableau. Si le tableau contient des points supplémentaires, une ligne est dessinée à partir du premier point et le deuxième point dans le tableau, à partir du deuxième point pour le troisième point et ainsi de suite. Tableau d’une séquence de points de terminaison des lignes à tracer.  
  
##  <a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier  
 Crée une courbe de Bézier quadratique lissée entre le point actuel et le point de fin spécifié.  
  
```  
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>Paramètres  
 `bezier`  
 Une structure qui décrit le point de contrôle et le point de terminaison de la courbe de Bézier quadratique à ajouter.  
  
##  <a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers  
 Ajoute une séquence de segments de Bézier quadratiques sous forme de tableau dans un seul appel.  
  
```  
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,  
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>Paramètres  
 `beziers`  
 Tableau d’une séquence de segments de Bézier quadratiques.  
  
##  <a name="beginfigure"></a>CD2DGeometrySink::BeginFigure  
 Démarre une nouvelle figure au point spécifié.  
  
```  
void BeginFigure(
    CD2DPointF startPoint,  
    D2D1_FIGURE_BEGIN figureBegin);
```  
  
### <a name="parameters"></a>Paramètres  
 `startPoint`  
 Le point à partir duquel commencer la nouvelle figure.  
  
 `figureBegin`  
 Indique si la nouvelle figure doit être creuse ou remplie.  
  
##  <a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink  
 Construit un objet CD2DGeometrySink à partir de l’objet de CD2DPathGeometry.  
  
```  
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```  
  
### <a name="parameters"></a>Paramètres  
 `pathGeometry`  
 Objet CD2DPathGeometry existant.  
  
##  <a name="close"></a>CD2DGeometrySink::Close  
 Ferme le récepteur de la géométrie  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi ; Sinon, FALSE.  
  
##  <a name="endfigure"></a>CD2DGeometrySink::EndFigure  
 Termine la figure en cours ; Si vous le souhaitez, le ferme.  
  
```  
void EndFigure(D2D1_FIGURE_END figureEnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `figureEnd`  
 Une valeur qui indique si la figure est fermée. Si la figure est fermée, une ligne est dessinée entre le point actuel et le point de départ spécifié par BeginFigure.  
  
##  <a name="get"></a>CD2DGeometrySink::Get  
 Renvoie l’interface ID2D1GeometrySink  
  
```  
ID2D1GeometrySink* Get();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de ID2D1GeometrySink ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="isvalid"></a>CD2DGeometrySink::IsValid  
 Vérifie la validité du récepteur de géométrie  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le récepteur de la géométrie est valide ; Sinon, FALSE.  
  
##  <a name="m_psink"></a>CD2DGeometrySink::m_pSink  
 Pointeur vers un ID2D1GeometrySink.  
  
```  
ID2D1GeometrySink* m_pSink;  
```  
  
##  <a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operator ID2D1GeometrySink *  
 Renvoie l’interface ID2D1GeometrySink  
  
```  
operator ID2D1GeometrySink*();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de ID2D1GeometrySink ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="setfillmode"></a>CD2DGeometrySink::SetFillMode  
 Spécifie la méthode utilisée pour déterminer les points situés à l’intérieur de la géométrie décrite par ce récepteur de la géométrie et les points situés à l’extérieur.  
  
```  
void SetFillMode(D2D1_FILL_MODE fillMode);
```  
  
### <a name="parameters"></a>Paramètres  
 `fillMode`  
 La méthode utilisée pour déterminer si un point donné fait partie de la géométrie.  
  
##  <a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags  
 Spécifie les options de trait et de jointure à appliquer aux nouveaux segments ajoutés au récepteur de la géométrie.  
  
```  
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```  
  
### <a name="parameters"></a>Paramètres  
 `vertexFlags`  
 Options de trait et de jointure à appliquer aux nouveaux segments ajoutés à la géométrie du récepteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
