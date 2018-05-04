---
title: Classe de IPropertyPageImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f86b93bad181fdbac5763bd215b0ec28ab50296
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl (classe)
Cette classe implémente **IUnknown** et fournit une implémentation par défaut de la [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) interface.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IPropertyPageImpl
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IPropertyPageImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IPropertyPageImpl::Activate](#activate)|Crée la fenêtre de boîte de dialogue de la page de propriétés.|  
|[IPropertyPageImpl::Apply](#apply)|Applique des valeurs de page de propriétés actuelles aux objets sous-jacents spécifiés par le biais `SetObjects`. L’implémentation ATL retourne `S_OK`.|  
|[IPropertyPageImpl::Deactivate](#deactivate)|Détruit la fenêtre créée avec **activer**.|  
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Récupère des informations sur la page de propriétés.|  
|[IPropertyPageImpl::Help](#help)|Appelle l’aide de Windows pour la page de propriétés.|  
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Indique si la page de propriétés a changé dans la mesure où il a été activé.|  
|[IPropertyPageImpl::Move](#move)|Positionne et redimensionne la boîte de dialogue de page de propriétés.|  
|[IPropertyPageImpl::SetDirty](#setdirty)|Indicateurs d’état de la page de propriétés comme étant modifié ou inchangé.|  
|[IPropertyPageImpl::SetObjects](#setobjects)|Fournit un tableau de **IUnknown** des pointeurs pour les objets associés à la page de propriétés. Ces objets recevront les valeurs de page de propriété actuelles via un appel à **appliquer**.|  
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Fournit la page de propriétés avec un `IPropertyPageSite` pointeur, par laquelle la page de propriétés communique avec le frame de propriété.|  
|[IPropertyPageImpl::Show](#show)|Rend la boîte de dialogue de page de propriété visible ou invisible.|  
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Traite une combinaison de touches spécifiée.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Indique si l’état de la page de propriété a changé.|  
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Stocke l’identificateur de ressource associé à la chaîne de texte décrivant la page de propriétés.|  
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Stocke l’identificateur de contexte pour la rubrique d’aide associée à la page de propriétés.|  
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Stocke l’identificateur de ressource associée au nom du fichier d’aide décrivant la page de propriétés.|  
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Stocke l’identificateur de ressource associé à la chaîne de texte qui apparaît dans l’onglet de la page de propriétés.|  
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Stocke le nombre d’objets associés à la page de propriétés.|  
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Pointe vers le `IPropertyPageSite` interface par laquelle la page de propriétés communique avec le frame de propriété.|  
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Pointe vers un tableau de **IUnknown** des pointeurs vers les objets associés à la page de propriétés.|  
|[IPropertyPageImpl::m_size](#m_size)|Stocke la hauteur et la largeur de la boîte de dialogue de la page de propriétés, en pixels.|  
  
## <a name="remarks"></a>Notes  
 Le [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) interface permet à un objet gérer une page de propriétés particulière dans une feuille de propriétés. Classe `IPropertyPageImpl` fournit une implémentation par défaut de cette interface et implémente **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="activate"></a>  IPropertyPageImpl::Activate  
 Crée la fenêtre de boîte de dialogue de la page de propriétés.  
  
```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```  
  
### <a name="remarks"></a>Notes  
 Par défaut, la boîte de dialogue est toujours non modale, quelle que soit la valeur de la *bModal* paramètre.  
  
 Consultez [IPropertyPage::Activate](http://msdn.microsoft.com/library/windows/desktop/ms682250) dans le Kit de développement logiciel Windows.  
  
##  <a name="apply"></a>  IPropertyPageImpl::Apply  
 Applique des valeurs de page de propriétés actuelles aux objets sous-jacents spécifiés par le biais `SetObjects`.  
  
```
HRESULT Apply();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage::Apply](http://msdn.microsoft.com/library/windows/desktop/ms691284) dans le Kit de développement logiciel Windows.  
  
##  <a name="deactivate"></a>  IPropertyPageImpl::Deactivate  
 Détruit la fenêtre de boîte de dialogue créée avec [activer](#activate).  
  
```
HRESULT Deactivate();
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage::Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms682504) dans le Kit de développement logiciel Windows.  
  
##  <a name="getpageinfo"></a>  IPropertyPageImpl::GetPageInfo  
 Remplit le *pPageInfo* structure avec les informations contenues dans les membres de données.  
  
```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Notes  
 `GetPageInfo` charge les ressources de chaîne associées [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile), et [m_dwTitle](#m_dwtitle).  
  
 Consultez [IPropertyPage::GetPageInfo](http://msdn.microsoft.com/library/windows/desktop/ms680714) dans le Kit de développement logiciel Windows.  
  
##  <a name="help"></a>  IPropertyPageImpl::Help  
 Appelle l’aide de Windows pour la page de propriétés.  
  
```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage::Help](http://msdn.microsoft.com/library/windows/desktop/ms691504) dans le Kit de développement logiciel Windows.  
  
##  <a name="ipropertypageimpl"></a>  IPropertyPageImpl::IPropertyPageImpl  
 Constructeur.  
  
```
IPropertyPageImpl();
```  
  
### <a name="remarks"></a>Notes  
 Initialise tous les membres de données.  
  
##  <a name="ispagedirty"></a>  IPropertyPageImpl::IsPageDirty  
 Indique si la page de propriétés a changé dans la mesure où il a été activé.  
  
```
HRESULT IsPageDirty(void);
```  
  
### <a name="remarks"></a>Notes  
 `IsPageDirty` Retourne `S_OK` si la page a été modifié, car il a été activé.  
  
##  <a name="m_bdirty"></a>  IPropertyPageImpl::m_bDirty  
 Indique si l’état de la page de propriété a changé.  
  
```
BOOL m_bDirty;
```  
  
##  <a name="m_nobjects"></a>  IPropertyPageImpl::m_nObjects  
 Stocke le nombre d’objets associés à la page de propriétés.  
  
```
ULONG m_nObjects;
```  
  
##  <a name="m_dwhelpcontext"></a>  IPropertyPageImpl::m_dwHelpContext  
 Stocke l’identificateur de contexte pour la rubrique d’aide associée à la page de propriétés.  
  
```
DWORD m_dwHelpContext;
```  
  
##  <a name="m_dwdocstring"></a>  IPropertyPageImpl::m_dwDocString  
 Stocke l’identificateur de ressource associé à la chaîne de texte décrivant la page de propriétés.  
  
```
UINT m_dwDocString;
```  
  
##  <a name="m_dwhelpfile"></a>  IPropertyPageImpl::m_dwHelpFile  
 Stocke l’identificateur de ressource associée au nom du fichier d’aide décrivant la page de propriétés.  
  
```
UINT m_dwHelpFile;
```  
  
##  <a name="m_dwtitle"></a>  IPropertyPageImpl::m_dwTitle  
 Stocke l’identificateur de ressource associé à la chaîne de texte qui apparaît dans l’onglet de la page de propriétés.  
  
```
UINT m_dwTitle;
```  
  
##  <a name="m_ppagesite"></a>  IPropertyPageImpl::m_pPageSite  
 Pointe vers le [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) interface par laquelle la page de propriétés communique avec le frame de propriété.  
  
```
IPropertyPageSite* m_pPageSite;
```  
  
##  <a name="m_ppunk"></a>  IPropertyPageImpl::m_ppUnk  
 Pointe vers un tableau de **IUnknown** des pointeurs vers les objets associés à la page de propriétés.  
  
```
IUnknown** m_ppUnk;
```  
  
##  <a name="m_size"></a>  IPropertyPageImpl::m_size  
 Stocke la hauteur et la largeur de la boîte de dialogue de la page de propriétés, en pixels.  
  
```
SIZE m_size;
```  
  
##  <a name="move"></a>  IPropertyPageImpl::Move  
 Positionne et redimensionne la boîte de dialogue de page de propriétés.  
  
```
HRESULT Move(LPCRECT pRect);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage::Move](http://msdn.microsoft.com/library/windows/desktop/ms680118) dans le Kit de développement logiciel Windows.  
  
##  <a name="setdirty"></a>  IPropertyPageImpl::SetDirty  
 Indicateurs d’état de la page de propriétés comme étant modifié ou inchangé, selon la valeur de `bDirty`.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Paramètres  
 `bDirty`  
 [in] Si **TRUE**, état de la page de propriété est marquée comme étant modifiée. Dans le cas contraire, il est marqué comme non modifié.  
  
### <a name="remarks"></a>Notes  
 Si nécessaire, `SetDirty` informe le frame de la page de propriétés a changé.  
  
##  <a name="setobjects"></a>  IPropertyPageImpl::SetObjects  
 Fournit un tableau de **IUnknown** des pointeurs pour les objets associés à la page de propriétés.  
  
```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage::SetObjects](http://msdn.microsoft.com/library/windows/desktop/ms678529) dans le Kit de développement logiciel Windows.  
  
##  <a name="setpagesite"></a>  IPropertyPageImpl::SetPageSite  
 Fournit la page de propriétés avec un [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) pointeur, par laquelle la page de propriétés communique avec le frame de propriété.  
  
```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage::SetPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690413) dans le Kit de développement logiciel Windows.  
  
##  <a name="show"></a>  IPropertyPageImpl::Show  
 Rend la boîte de dialogue de page de propriété visible ou invisible.  
  
```
HRESULT Show(UINT nCmdShow);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage::Show](http://msdn.microsoft.com/library/windows/desktop/ms694467) dans le Kit de développement logiciel Windows.  
  
##  <a name="translateaccelerator"></a>  IPropertyPageImpl::TranslateAccelerator  
 Traite la séquence de touches spécifiée dans `pMsg`.  
  
```
HRESULT TranslateAccelerator(MSG* pMsg);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IPropertyPage::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms686603) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)   
 [Classe de IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Classe de ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
