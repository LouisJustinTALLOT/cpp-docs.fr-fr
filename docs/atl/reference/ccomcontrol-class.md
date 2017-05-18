---
title: Classe de CComControl | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
dev_langs:
- C++
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 387d38f89e8d783c7ae85c2ab960d5e59c1c4009
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="ccomcontrol-class"></a>CComControl (classe)
Cette classe fournit des méthodes pour créer et gérer des contrôles ATL.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class WinBase = CWindowImpl<T>>  
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 La classe qui implémente le contrôle.  
  
 *WinBase*  
 La classe de base qui implémente les fonctions de fenêtrage. Valeur par défaut est [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComControl::CComControl](#ccomcontrol)|Constructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Récupère un pointeur vers l'interface demandée.|  
|[CComControl::CreateControlWindow](#createcontrolwindow)|Crée une fenêtre pour le contrôle.|  
|[CComControl::FireOnChanged](#fireonchanged)|Notifie le récepteur du conteneur qu’une propriété de contrôle a changé.|  
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Notifie les récepteurs du conteneur qu’une propriété de contrôle est sur le point de modifier et que l’objet et demande le récepteur de la marche à suivre.|  
|[CComControl::MessageBox](#messagebox)|Appelez cette méthode pour créer, afficher et utiliser une zone de message.|  
  
## <a name="remarks"></a>Remarques  
 `CComControl`est un ensemble de fonctions d’assistance de contrôle pratique et les membres de données essentielles pour des contrôles ATL. Lorsque vous créez un contrôle standard ou un contrôle DHTML Edit à l’aide de l’Assistant contrôle ATL, l’Assistant dérivera automatiquement votre classe à partir de `CComControl`. `CComControl`dérive la plupart de ses méthodes à partir de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).  
  
 Pour plus d’informations sur la création d’un contrôle, consultez la [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Pour une démonstration de `CComControl` méthodes et les membres de données, consultez la [CERC](../../visual-cpp-samples.md) exemple.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="ccomcontrol"></a>CComControl::CComControl  
 Constructeur.  
  
```
CComControl();
```  
  
### <a name="remarks"></a>Remarques  
 Appelle le [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) constructeur, en passant le `m_hWnd` membre de données héritées via [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Le GUID de l’interface demandée.  
  
 `ppv`  
 [out] Un pointeur vers le pointeur d’interface identifié par `iid`, ou **NULL** si l’interface est introuvable.  
  
### <a name="remarks"></a>Notes  
 Gère seulement des interfaces dans la table de mappage COM.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM&#15;](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]  
  
##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow  
 Par défaut, crée une fenêtre pour le contrôle en appelant `CWindowImpl::Create`.  
  
```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 [in] Handle de la fenêtre parente ou propriétaire. Un handle de fenêtre valide doit être fourni. La fenêtre de contrôle se limite à la zone de la fenêtre parente.  
  
 `rcPos`  
 [in] La taille initiale et la position de la fenêtre doit être créé.  
  
### <a name="remarks"></a>Remarques  
 Substituez cette méthode si vous souhaitez effectuer une opération autre que de créer une fenêtre unique, par exemple, pour créer deux fenêtres, qui devient une barre d’outils pour votre contrôle.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM&#16;](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]  
  
##  <a name="fireonchanged"></a>CComControl::FireOnChanged  
 Notifie le récepteur du conteneur qu’une propriété de contrôle a changé.  
  
```
HRESULT FireOnChanged(DISPID dispID);
```  
  
### <a name="parameters"></a>Paramètres  
 *dispID*  
 [in] Identificateur de la propriété qui a changé.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Si votre classe de contrôle dérive [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), cette méthode appelle [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) pour notifier tous connectés `IPropertyNotifySink` interfaces que la propriété du contrôle spécifié a changé. Si votre classe de contrôle ne dérive pas de `IPropertyNotifySink`, cette méthode retourne `S_OK`. 
  
 Cette méthode peut appeler, même si votre contrôle ne prend pas en charge les points de connexion.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM&#17;](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]  
  
##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit  
 Notifie les récepteurs du conteneur qu’une propriété de contrôle est sur le point de modifier et que l’objet et demande le récepteur de la marche à suivre.  
  
```
HRESULT FireOnRequestEdit(DISPID dispID);
```  
  
### <a name="parameters"></a>Paramètres  
 *dispID*  
 [in] Identificateur de la propriété va être modifiée.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Remarques  
 Si votre classe de contrôle dérive [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), cette méthode appelle [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) pour notifier tous connectés `IPropertyNotifySink` interfaces que la propriété du contrôle spécifié est sur le point de changer. Si votre classe de contrôle ne dérive pas de `IPropertyNotifySink`, cette méthode retourne `S_OK`.  

  
 Cette méthode peut appeler, même si votre contrôle ne prend pas en charge les points de connexion.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM&#18;](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]  
  
##  <a name="messagebox"></a>CComControl::MessageBox  
 Appelez cette méthode pour créer, afficher et utiliser une zone de message.  
  
```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszText`  
 Texte à afficher dans la boîte de message.  
  
 `lpszCaption`  
 Le titre de la boîte de dialogue. Si NULL (valeur par défaut), le titre « Erreur » est utilisé.  
  
 `nType`  
 Spécifie le contenu et le comportement de la boîte de dialogue. Consultez le [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) entrée dans le [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] documentation pour obtenir la liste des différents les messages disponibles. La valeur par défaut fournit un simple **OK** bouton.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur entière spécifiant l’une des valeurs d’élément de menu apparaît sous [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) dans les [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] documentation.  
  
### <a name="remarks"></a>Notes  
 `MessageBox`est utile lors du développement et comme un moyen simple pour afficher une erreur ou un message d’avertissement à l’utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [CWindowImpl (classe)](../../atl/reference/cwindowimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Classe CComControlBase](../../atl/reference/ccomcontrolbase-class.md)   
 [Classe CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)

