---
title: Classe de CComControl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6017d06715146a0440887a2a2e10828398d5044b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365548"
---
# <a name="ccomcontrol-class"></a>Classe de CComControl
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
 La classe implémentant le contrôle.  
  
 *WinBase*  
 La classe de base qui implémente des fonctions de fenêtrage. Valeur par défaut est [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
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
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Notifie les récepteurs du conteneur qu’une propriété de contrôle est sur le point de modifier et que l’objet demande le récepteur de la marche à suivre.|  
|[CComControl::MessageBox](#messagebox)|Appelez cette méthode pour créer, afficher et utiliser une boîte de message.|  
  
## <a name="remarks"></a>Notes  
 `CComControl` est un ensemble de fonctions d’assistance de contrôle pratique et les membres de données essentielles pour les contrôles ATL. Lorsque vous créez un contrôle standard ou un contrôle DHTML à l’aide de l’Assistant contrôle ATL, l’Assistant dérivera automatiquement votre classe de `CComControl`. `CComControl` dérive la plupart de ses méthodes de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).  
  
 Pour plus d’informations sur la création d’un contrôle, consultez la [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md). Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Pour une démonstration de `CComControl` méthodes et les membres de données, consultez la [CIRC](../../visual-cpp-samples.md) exemple.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="ccomcontrol"></a>  CComControl::CComControl  
 Constructeur.  
  
```
CComControl();
```  
  
### <a name="remarks"></a>Notes  
 Appelle le [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) constructeur, en passant le `m_hWnd` membre de données héritée via [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface  
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
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]  
  
##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow  
 Par défaut, crée une fenêtre pour le contrôle en appelant `CWindowImpl::Create`.  
  
```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 [in] Handle vers la fenêtre parente ou propriétaire. Un handle de fenêtre valide doit être fourni. La fenêtre de contrôle est limitée à la zone de sa fenêtre parente.  
  
 `rcPos`  
 [in] La taille initiale et la position de la fenêtre doit être créé.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode si vous souhaitez effectuer une opération autre que de créer une fenêtre unique, par exemple, pour créer deux fenêtres, qui devient une barre d’outils pour votre contrôle.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]  
  
##  <a name="fireonchanged"></a>  CComControl::FireOnChanged  
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
 Si votre classe de contrôle dérive [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), cette méthode appelle [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) pour notifier tous connectés `IPropertyNotifySink` les interfaces que le contrôle spécifié propriété a changé. Si votre classe de contrôle ne dérive pas de `IPropertyNotifySink`, cette méthode retourne `S_OK`. 
  
 Cette méthode peut appeler, même si votre contrôle ne prend pas en charge les points de connexion.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]  
  
##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit  
 Notifie les récepteurs du conteneur qu’une propriété de contrôle est sur le point de modifier et que l’objet demande le récepteur de la marche à suivre.  
  
```
HRESULT FireOnRequestEdit(DISPID dispID);
```  
  
### <a name="parameters"></a>Paramètres  
 *dispID*  
 [in] Identificateur de la propriété va être modifiée.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Si votre classe de contrôle dérive [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), cette méthode appelle [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) pour notifier tous connectés `IPropertyNotifySink` interfaces spécifié propriété du contrôle est sur le point de changer. Si votre classe de contrôle ne dérive pas de `IPropertyNotifySink`, cette méthode retourne `S_OK`.  

  
 Cette méthode peut appeler, même si votre contrôle ne prend pas en charge les points de connexion.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]  
  
##  <a name="messagebox"></a>  CComControl::MessageBox  
 Appelez cette méthode pour créer, afficher et utiliser une boîte de message.  
  
```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszText`  
 Le texte à afficher dans la boîte de message.  
  
 `lpszCaption`  
 Le titre de la boîte de dialogue. Si NULL (la valeur par défaut), le titre « Error » est utilisé.  
  
 `nType`  
 Spécifie le contenu et le comportement de la boîte de dialogue. Consultez le [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) entrée dans la documentation du Kit de développement logiciel Windows pour obtenir la liste des zones de message différents disponibles. La valeur par défaut fournit un simple **OK** bouton.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur entière spécifiant l’une des valeurs d’élément de menu répertoriés sous [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) dans la documentation du Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 `MessageBox` est utile lors du développement et comme un moyen simple pour afficher un message d’erreur ou avertissement à l’utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CWindowImpl](../../atl/reference/cwindowimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Classe CComControlBase](../../atl/reference/ccomcontrolbase-class.md)   
 [CComCompositeControl, classe](../../atl/reference/ccomcompositecontrol-class.md)
