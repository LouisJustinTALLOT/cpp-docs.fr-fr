---
title: Classe de CAxWindow2T | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
dev_langs:
- C++
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 077ecfe36e1ddf6c319f02bdabb89d660a5f22d8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360756"
---
# <a name="caxwindow2t-class"></a>Classe de CAxWindow2T
Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX et prend également en charge pour l’hébergement de contrôles ActiveX sous licence.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```  
  
#### <a name="parameters"></a>Paramètres  
 *TBase*  
 La classe à partir de laquelle `CAxWindowT` dérive.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Construit un objet `CAxWindow2T`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAxWindow2T::Create](#create)|Crée une fenêtre hôte.|  
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Crée un contrôle ActiveX sous licence, puis initialise et héberge ce dernier dans la fenêtre spécifiée.|  
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Crée un contrôle ActiveX sous licence, il initialise, héberge ce dernier dans la fenêtre spécifiée et récupère un pointeur d’interface (ou pointeurs) à partir du contrôle.|  
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Méthode statique qui Récupère le nom de la classe de fenêtre.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAxWindow2T::operator =](#operator_eq)|Affecte un `HWND` à un `CAxWindow2T` objet.|  
  
## <a name="remarks"></a>Notes  
 `CAxWindow2T` Fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX. `CAxWindow2T` a également la prise en charge pour l’hébergement de contrôles ActiveX sous licence. L’hébergement est fournie par « **AtlAxWinLic80**», qui est encapsulé par `CAxWindow2T`.  
  
 Classe `CAxWindow2` est implémenté comme une spécialisation de la `CAxWindow2T` classe. Cette spécialisation est déclarée en tant que :  
  
 `typedef CAxWindow2T <CWindow> CAxWindow2;`  
  
> [!NOTE]
> `CAxWindowT` les membres sont décrits dans [objet CAxWindow](../../atl/reference/caxwindow-class.md).  
  
 Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise les membres de cette classe.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `TBase`  
  
 `CAxWindowT`  
  
 `CAxWindow2T`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlwin.h  
  
##  <a name="caxwindow2t"></a>  CAxWindow2T::CAxWindow2T  
 Construit un objet `CAxWindow2T`.  
  
```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```  
  
### <a name="parameters"></a>Paramètres  
 `hWnd`  
 Un handle d’une fenêtre existante.  
  
##  <a name="create"></a>  CAxWindow2T::Create  
 Crée une fenêtre hôte.  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="remarks"></a>Notes  
 `CAxWindow2T::Create` appels [CWindow::Create](../../atl/reference/cwindow-class.md#create) avec la `LPCTSTR lpstrWndClass` paramètre défini sur la classe de fenêtre qui assure l’hébergement du contrôle ( **AtlAxWinLic80**).  
  
 Consultez `CWindow::Create` pour obtenir une description des paramètres et de la valeur de retour.  
  
 **Remarque** si 0 est utilisé comme valeur pour le `MenuOrID` paramètre, il doit être spécifié en tant que 0 u (valeur par défaut) pour éviter une erreur du compilateur.  
  
### <a name="example"></a>Exemple  
 Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `CAxWindow2T::Create`.  
  
##  <a name="createcontrollic"></a>  CAxWindow2T::CreateControlLic  
 Crée un contrôle ActiveX sous licence, puis initialise et héberge ce dernier dans la fenêtre spécifiée.  
  
```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `bstrLicKey`  
 La clé de licence pour le contrôle ; NULL si la création d’un contrôle sans licence.  
  
### <a name="remarks"></a>Notes  
 Consultez [CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) pour obtenir une description de la valeur de retour et de paramètres restants.  
  
### <a name="example"></a>Exemple  
 Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `CAxWindow2T::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>  CAxWindow2T::CreateControlLicEx  
 Crée un contrôle ActiveX sous licence, il initialise, héberge ce dernier dans la fenêtre spécifiée et récupère un pointeur d’interface (ou pointeurs) à partir du contrôle.  
  
```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `bstrLicKey`  
 La clé de licence pour le contrôle ; NULL si la création d’un contrôle sans licence.  
  
### <a name="remarks"></a>Notes  
 Consultez [CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) pour obtenir une description de la valeur de retour et de paramètres restants.  
  
### <a name="example"></a>Exemple  
 Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `CAxWindow2T::CreateControlLicEx`.  
  
##  <a name="getwndclassname"></a>  CAxWindow2T::GetWndClassName  
 Récupère le nom de la classe de fenêtre.  
  
```
static LPCTSTR GetWndClassName();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers une chaîne contenant le nom de la classe de fenêtre ( **AtlAxWinLic80**) qui peut héberger des contrôles ActiveX sous licence et sans licence.  
  
##  <a name="operator_eq"></a>  CAxWindow2T::operator =  
 Affecte un `HWND` à un `CAxWindow2T` objet.  
  
```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWnd`  
 Un handle d’une fenêtre existante.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Forum aux questions sur la contenance de contrôles](../../atl/atl-control-containment-faq.md)
