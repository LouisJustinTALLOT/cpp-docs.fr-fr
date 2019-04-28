---
title: CAxWindow2T classe
ms.date: 11/04/2016
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
ms.openlocfilehash: 0d5991dcbf79d1c2415594636a09908586d1dc2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260026"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T classe

Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX et prend également en charge pour l’hébergement de contrôles ActiveX sous licence.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Paramètres

*TBase*<br/>
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
|[CAxWindow2T::operator =](#operator_eq)|Assigne un HWND à un existant `CAxWindow2T` objet.|

## <a name="remarks"></a>Notes

`CAxWindow2T` Fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX. `CAxWindow2T` a également la prise en charge pour l’hébergement de contrôles ActiveX sous licence. L’hébergement est fournie par « **AtlAxWinLic80**», qui est encapsulé par `CAxWindow2T`.

Classe `CAxWindow2` est implémentée comme une spécialisation de la `CAxWindow2T` classe. Cette spécialisation est déclarée en tant que :

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` les membres sont documentées sous [objet CAxWindow](../../atl/reference/caxwindow-class.md).

Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise les membres de cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlwin.h

##  <a name="caxwindow2t"></a>  CAxWindow2T::CAxWindow2T

Construit un objet `CAxWindow2T`.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Handle d’une fenêtre existante.

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

`CAxWindow2T::Create` appels [CWindow::Create](../../atl/reference/cwindow-class.md#create) avec le LPCTSTR *lpstrWndClass* paramètre défini sur la classe de fenêtre qui fournit l’hébergement de contrôle (`AtlAxWinLic80`).

Consultez `CWindow::Create` pour obtenir une description des paramètres et de la valeur de retour.

**Remarque** si 0 est utilisé comme valeur pour le *MenuOrID* paramètre, il doit être spécifié en tant que 0 u (valeur par défaut) pour éviter une erreur du compilateur.

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

*bstrLicKey*<br/>
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

*bstrLicKey*<br/>
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

Un pointeur vers une chaîne contenant le nom de la classe de fenêtre (`AtlAxWinLic80`) qui peut héberger des contrôles ActiveX sous licence et sans licence.

##  <a name="operator_eq"></a>  CAxWindow2T::operator =

Assigne un HWND à un existant `CAxWindow2T` objet.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Handle d’une fenêtre existante.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Forum aux questions sur la contenance de contrôles](../../atl/atl-control-containment-faq.md)
