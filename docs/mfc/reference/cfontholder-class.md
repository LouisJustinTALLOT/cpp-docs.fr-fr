---
title: Classe de CFontHolder | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
dev_langs:
- C++
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5cb28b738822b3e35aa840c731eb11bc2c2b83d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367514"
---
# <a name="cfontholder-class"></a>Classe de CFontHolder
Implémente la propriété stock Font et encapsule les fonctionnalités d'un objet police Windows et de l'interface `IFont` .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFontHolder  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFontHolder::CFontHolder](#cfontholder)|Construit un objet `CFontHolder`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CFontHolder::GetDisplayString](#getdisplaystring)|Récupère la chaîne affichée dans l’Explorateur de propriétés d’un conteneur.|  
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Retourne la police `IDispatch` interface.|  
|[CFontHolder::GetFontHandle](#getfonthandle)|Retourne un handle vers une police de Windows.|  
|[CFontHolder::InitializeFont](#initializefont)|Initialise un `CFontHolder` objet.|  
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Récupère les informations pour la police connexe.|  
|[CFontHolder::ReleaseFont](#releasefont)|Déconnecte le `CFontHolder` de l’objet à partir de la `IFont` et `IFontNotification` interfaces.|  
|[CFontHolder::Select](#select)|Sélectionne une ressource de police dans un contexte de périphérique.|  
|[CFontHolder::SetFont](#setfont)|Se connecte le `CFontHolder` de l’objet à un `IFont` interface.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFontHolder::m_pFont](#m_pfont)|Un pointeur vers le `CFontHolder` l’objet `IFont` interface.|  
  
## <a name="remarks"></a>Notes  
 `CFontHolder` ne dispose pas d’une classe de base.  
  
 Utilisez cette classe pour implémenter les propriétés de police personnalisée pour votre contrôle. Pour plus d’informations sur la création de ces propriétés, consultez l’article [contrôles ActiveX : utilisation des polices](../../mfc/mfc-activex-controls-using-fonts.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CFontHolder`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxctl.h  
  
##  <a name="cfontholder"></a>  CFontHolder::CFontHolder  
 Construit un objet `CFontHolder`.  
  
```  
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```  
  
### <a name="parameters"></a>Paramètres  
 *pNotify*  
 Pointeur vers la police `IPropertyNotifySink` interface.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler `InitializeFont` pour initialiser l’objet obtenu avant de l’utiliser.  
  
##  <a name="getdisplaystring"></a>  CFontHolder::GetDisplayString  
 Récupère une chaîne qui peut être affichée dans l’Explorateur de propriétés d’un conteneur.  
  
```  
BOOL GetDisplayString(CString& strValue);
```  
  
### <a name="parameters"></a>Paramètres  
 `strValue`  
 Référence à la [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui doit contenir la chaîne d’affichage.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la chaîne est récupérée avec succès ; Sinon, 0.  
  
##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch  
 Appelez cette fonction pour récupérer un pointeur vers l’interface de dispatch de la police.  
  
```  
LPFONTDISP GetFontDispatch();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `CFontHolder` l’objet **IFontDisp** interface. Notez que la fonction qui appelle `GetFontDispatch` doit appeler `IUnknown::Release` sur ce pointeur d’interface lorsque vous avez terminé avec lui.  
  
### <a name="remarks"></a>Notes  
 Appelez `InitializeFont` avant d’appeler `GetFontDispatch`.  
  
##  <a name="getfonthandle"></a>  CFontHolder::GetFontHandle  
 Appelez cette fonction pour obtenir un handle à une police de Windows.  
  
```  
HFONT GetFontHandle();

 
HFONT GetFontHandle(
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>Paramètres  
 `cyLogical`  
 Hauteur, en unités logiques, du rectangle dans lequel le contrôle est dessiné.  
  
 `cyHimetric`  
 Hauteur, en `MM_HIMETRIC` unités, du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Un handle vers l’objet de police ; dans le cas contraire **NULL**.  
  
### <a name="remarks"></a>Notes  
 Le rapport entre `cyLogical` et `cyHimetric` est utilisé pour calculer la taille d’affichage approprié, en unités logiques, de la taille de police point exprimé en `MM_HIMETRIC` unités :  
  
 Afficher la taille = ( `cyLogical`  /  `cyHimetric`) X taille de police  
  
 La version sans paramètres retourne un handle vers une police adaptée pour l’écran.  
  
##  <a name="initializefont"></a>  CFontHolder::InitializeFont  
 Initialise un `CFontHolder` objet.  
  
```  
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,  
    LPDISPATCH pFontDispAmbient = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pFontDesc`  
 Pointeur vers une structure de description de police ( [FONTDESC](http://msdn.microsoft.com/library/windows/desktop/ms692782)) qui spécifie les caractéristiques de la police.  
  
 `pFontDispAmbient`  
 Pointeur vers la propriété de police ambiante du conteneur.  
  
### <a name="remarks"></a>Notes  
 Si `pFontDispAmbient` n’est pas **NULL**, le `CFontHolder` objet est connecté à un clone de le `IFont` interface utilisée par la propriété de police ambiante du conteneur.  
  
 Si `pFontDispAmbient` est **NULL**, un nouvel objet de police est créé à partir de la description de la police vers lequel pointée `pFontDesc` ou, si `pFontDesc` est **NULL**, à partir d’une description par défaut.  
  
 Appelez cette fonction après avoir construit un `CFontHolder` objet.  
  
##  <a name="m_pfont"></a>  CFontHolder::m_pFont  
 Un pointeur vers le `CFontHolder` l’objet `IFont` interface.  
  
```  
LPFONT m_pFont;  
```  
  
##  <a name="querytextmetrics"></a>  CFontHolder::QueryTextMetrics  
 Extrait des informations sur la police physique représentée par la `CFontHolder` objet.  
  
```  
void QueryTextMetrics(LPTEXTMETRIC lptm);
```  
  
### <a name="parameters"></a>Paramètres  
 `lptm`  
 Un pointeur vers un [TEXTMETRIC](http://msdn.microsoft.com/library/windows/desktop/dd145132) structure qui recevront les informations.  
  
##  <a name="releasefont"></a>  CFontHolder::ReleaseFont  
 Cette fonction se déconnecte le `CFontHolder` de l’objet à partir de son `IFont` interface.  
  
```  
void ReleaseFont();
```  
  
##  <a name="select"></a>  CFontHolder::Select  
 Appelez cette fonction pour sélectionner la police de votre contrôle dans le contexte de périphérique spécifié.  
  
```  
CFont* Select(
    CDC* pDC,  
    long cyLogical,  
    long cyHimetric);
```  
  
### <a name="parameters"></a>Paramètres  
 `pDC`  
 Contexte de périphérique dans lequel la police est sélectionnée.  
  
 `cyLogical`  
 Hauteur, en unités logiques, du rectangle dans lequel le contrôle est dessiné.  
  
 `cyHimetric`  
 Hauteur, en `MM_HIMETRIC` unités, du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers la police qui est remplacé.  
  
### <a name="remarks"></a>Notes  
 Consultez [GetFontHandle](#getfonthandle) pour en savoir plus sur les `cyLogical` et `cyHimetric` paramètres.  
  
##  <a name="setfont"></a>  CFontHolder::SetFont  
 Libère toutes les polices et se connecte le `CFontHolder` de l’objet à un `IFont` interface.  
  
```  
void SetFont(LPFONT pNewFont);
```  
  
### <a name="parameters"></a>Paramètres  
 *pNewFont*  
 Pointeur vers la nouvelle `IFont` interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CPropExchange, classe](../../mfc/reference/cpropexchange-class.md)
