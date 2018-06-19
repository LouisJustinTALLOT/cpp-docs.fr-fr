---
title: Classe CComCompositeControl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
dev_langs:
- C++
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 592eb6c897f47bede5aa0a09149aaf791e8cfbce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365407"
---
# <a name="ccomcompositecontrol-class"></a>Classe CComCompositeControl
Cette classe fournit les méthodes requises pour implémenter un contrôle composite.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que d’autres interfaces souhaitées prendre en charge pour votre contrôle composite.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|Constructeur.|  
|[CComCompositeControl :: ~ CComCompositeControl](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Appelez cette méthode pour conseiller ou déconseiller tous les contrôles hébergés par le contrôle composite.|  
|[CComCompositeControl::CalcExtent](#calcextent)|Appelez cette méthode pour calculer la taille en **HIMETRIC** unités de la ressource de boîte de dialogue utilisée pour héberger le contrôle composite.|  
|[CComCompositeControl::Create](#create)|Cette méthode est appelée pour créer la fenêtre de contrôle pour le contrôle composite.|  
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Appelez cette méthode pour créer la fenêtre de contrôle et de conseiller n’importe quel contrôle hébergé.|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Appelez cette méthode pour définir la couleur d’arrière-plan du contrôle composite à l’aide de la couleur d’arrière-plan du conteneur.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Le pinceau d’arrière-plan.|  
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|Le handle de la fenêtre qui a actuellement le focus.|  
  
## <a name="remarks"></a>Notes  
 Classes dérivées de la classe `CComCompositeControl` hériter des fonctionnalités d’un contrôle composite ActiveX. Contrôles ActiveX dérivés `CComCompositeControl` sont hébergés par une boîte de dialogue standard. Ces types de contrôles sont appelés contrôles composites, car ils sont capables d’héberger d’autres contrôles (contrôles Windows natifs et les contrôles ActiveX).  
  
 `CComCompositeControl` identifie la ressource de boîte de dialogue à utiliser pour créer le contrôle composite en recherchant un membre de données énumérés dans la classe enfant. Le membre IDD de cette classe enfant est défini pour l’ID de ressource de la ressource de boîte de dialogue qui sera utilisée en tant que la fenêtre du contrôle. Voici un exemple du membre de données que la classe dérivée de `CComCompositeControl` doit contenir pour identifier la ressource de boîte de dialogue à utiliser pour la fenêtre du contrôle :  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  Contrôles composites sont toujours contrôles fenêtrés, même si elles peuvent contenir des contrôles sans fenêtre.  
  
 Un contrôle implémenté par un `CComCompositeControl`-classe dérivée a intégré de comportement de tabulation par défaut. Lorsque le contrôle reçoit le focus par en cours à onglets pour dans une application conteneur, successivement en appuyant sur la touche TAB provoque le focus puisse passer tous des contrôles de contenu d' un contrôle composite, puis en dehors du contrôle composite et une session sur l’élément suivant dans la ordre de tabulation du conteneur. L’ordre de tabulation des contrôles hébergés est déterminé par la ressource de boîte de dialogue et détermine l’ordre dans les tabulation se produit.  
  
> [!NOTE]
>  Dans l’ordre des accélérateurs de fonctionner correctement avec un `CComCompositeControl`, il est nécessaire de charger une table d’accélérateurs en tant que le contrôle est créé, de transmettre le handle et le nombre d’accélérateurs dans [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), et détruire enfin la table lorsque le contrôle est libéré.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="advisesinkmap"></a>  CComCompositeControl::AdviseSinkMap  
 Appelez cette méthode pour conseiller ou déconseiller tous les contrôles hébergés par le contrôle composite.  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>Paramètres  
 `bAdvise`  
 True si tous les contrôles doivent être avertie ; Sinon, false.  
  
### <a name="return-value"></a>Valeur de retour  
 `S_OK`  
 Tous les contrôles de table de récepteur ont été connecté ou déconnecté avec succès à partir de leur source d’événements.  
  
 **E_FAIL**  
 Pas tous les contrôles table réceptrice pourrait connecté ou déconnecté avec succès à partir de leur source d’événements.  
  
 `E_POINTER`  
 Cette erreur indique généralement un problème avec une entrée dans la table de récepteur d’événements du contrôle ou un problème avec un argument de modèle utilisé dans une `IDispEventImpl` ou `IDispEventSimpleImpl` classe de base.  
  
 **CONNECT_E_ADVISELIMIT**  
 Le point de connexion a déjà atteint sa limite de connexions et ne peut pas accepter d’autres.  
  
 **CONNECT_E_CANNOTCONNECT**  
 Le récepteur ne prend pas en charge l’interface requise par ce point de connexion.  
  
 **CONNECT_E_NOCONNECTION**  
 La valeur du cookie ne représente pas une connexion valide. Cette erreur indique généralement un problème avec une entrée dans la table de récepteur d’événements du contrôle ou un problème avec un argument de modèle utilisé dans une `IDispEventImpl` ou `IDispEventSimpleImpl` classe de base.  
  
### <a name="remarks"></a>Notes  
 L’implémentation de base de cette méthode recherche via les entrées de table de récepteur de l’événement. Ensuite, il indique qu’il contient ou avertit les points de connexion pour les objets COM décrites par les entrées de récepteurs de la table récepteur d’événements. Cette méthode membre s’appuie également sur le fait que la classe dérivée hérite d’une instance de `IDispEventImpl` pour chaque contrôle dans la table de récepteur doit être conseillées ou cessent d’être averties.  
  
##  <a name="calcextent"></a>  CComCompositeControl::CalcExtent  
 Appelez cette méthode pour calculer la taille en **HIMETRIC** unités de la ressource de boîte de dialogue utilisée pour héberger le contrôle composite.  
  
```
BOOL CalcExtent(SIZE& size);
```  
  
### <a name="parameters"></a>Paramètres  
 `size`  
 Une référence à un **taille** structure doivent être remplis par cette méthode.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le contrôle est hébergé par une boîte de dialogue ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 La taille est retournée dans le `size` paramètre.  
  
##  <a name="create"></a>  CComCompositeControl::Create  
 Cette méthode est appelée pour créer la fenêtre de contrôle pour le contrôle composite.  
  
```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 Handle vers la fenêtre parente du contrôle.  
  
 `rcPos`  
 Réservé.  
  
 `dwInitParam`  
 Données à passer au contrôle lors de la création du contrôle. Les données transmises en tant que `dwInitParam` apparaît comme le **LPARAM** paramètre de la [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) message, qui est envoyée au contrôle composite lorsque celui-ci est créé.  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers la boîte de dialogue contrôle composite nouvellement créé.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est généralement appelée pendant l’activation sur place du contrôle.  
  
##  <a name="ccomcompositecontrol"></a>  CComCompositeControl::CComCompositeControl  
 Constructeur.  
  
```
CComCompositeControl();
```  
  
### <a name="remarks"></a>Notes  
 Initialise le [CComCompositeControl::m_hbrBackground](#m_hbrbackground) et [CComCompositeControl::m_hWndFocus](#m_hwndfocus) les membres de données avec la valeur NULL.  
  
##  <a name="dtor"></a>  CComCompositeControl :: ~ CComCompositeControl  
 Destructeur.  
  
```
~CComCompositeControl();
```  
  
### <a name="remarks"></a>Notes  
 Supprime l’objet en arrière-plan, si elle existe.  
  
##  <a name="createcontrolwindow"></a>  CComCompositeControl::CreateControlWindow  
 Appelez cette méthode pour créer la fenêtre de contrôle et de signaler tous les contrôles hébergés.  
  
```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 Handle vers la fenêtre parente du contrôle.  
  
 `rcPos`  
 La valeur position rectangle du contrôle composite dans client coordonne relatif à `hWndParent`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un handle vers la boîte de dialogue contrôle composite nouvellement créé.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [CComCompositeControl::Create](#create) et [CComCompositeControl::AdviseSinkMap](#advisesinkmap).  
  
##  <a name="m_hbrbackground"></a>  CComCompositeControl::m_hbrBackground  
 Le pinceau d’arrière-plan.  
  
```
HBRUSH m_hbrBackground;
```  
  
##  <a name="m_hwndfocus"></a>  CComCompositeControl::m_hWndFocus  
 Le handle de la fenêtre qui a actuellement le focus.  
  
```
HWND m_hWndFocus;
```  
  
##  <a name="setbackgroundcolorfromambient"></a>  CComCompositeControl::SetBackgroundColorFromAmbient  
 Appelez cette méthode pour définir la couleur d’arrière-plan du contrôle composite à l’aide de la couleur d’arrière-plan du conteneur.  
  
```
HRESULT SetBackgroundColorFromAmbient();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Principes de base des contrôles composites](../../atl/atl-composite-control-fundamentals.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
