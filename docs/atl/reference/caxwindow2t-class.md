---
title: CAxWindow2T, classe
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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417991"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T, classe

Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX et prend également en charge l’hébergement de contrôles ActiveX sous licence.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Paramètres

*TBase*<br/>
Classe à partir de laquelle `CAxWindowT` dérive.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Construit un objet `CAxWindow2T`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CAxWindow2T :: Create](#create)|Crée une fenêtre hôte.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Crée un contrôle ActiveX sous licence, puis initialise et héberge ce dernier dans la fenêtre spécifiée.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Crée un contrôle ActiveX sous licence, l’initialise, l’héberge dans la fenêtre spécifiée et récupère un pointeur d’interface (ou des pointeurs) du contrôle.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Méthode statique qui récupère le nom de la classe de fenêtre.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|----------|-----------------|
|[CAxWindow2T :: Operator =](#operator_eq)|Assigne un HWND à un objet `CAxWindow2T` existant.|

## <a name="remarks"></a>Notes

`CAxWindow2T` fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX. `CAxWindow2T` prend également en charge l’hébergement de contrôles ActiveX sous licence. L’hébergement est fourni par « **AtlAxWinLic80**», qui est encapsulé par `CAxWindow2T`.

La classe `CAxWindow2` est implémentée comme une spécialisation de la classe `CAxWindow2T`. Cette spécialisation est déclarée comme suit :

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` membres sont documentés sous [CAxWindow](../../atl/reference/caxwindow-class.md).

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise les membres de cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

##  <a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

Construit un objet `CAxWindow2T`.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Handle d’une fenêtre existante.

##  <a name="create"></a>CAxWindow2T :: Create

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

`CAxWindow2T::Create` appelle [CWindow :: Create](../../atl/reference/cwindow-class.md#create) avec le paramètre *lpstrWndClass* LPCTSTR défini sur la classe de fenêtre qui fournit l’hébergement de contrôle (`AtlAxWinLic80`).

Pour obtenir une description des paramètres et de la valeur de retour, consultez `CWindow::Create`.

**Remarque** Si 0 est utilisé comme valeur pour le paramètre *MenuOrID* , il doit être spécifié sous la forme de 0U (valeur par défaut) pour éviter une erreur du compilateur.

### <a name="example"></a>Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `CAxWindow2T::Create`.

##  <a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

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
Clé de licence du contrôle ; NULL si vous créez un contrôle sans licence.

### <a name="remarks"></a>Notes

Pour obtenir une description des paramètres restants et de la valeur de retour, consultez [CAxWindow :: CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) .

### <a name="example"></a>Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `CAxWindow2T::CreateControlLic`.

##  <a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

Crée un contrôle ActiveX sous licence, l’initialise, l’héberge dans la fenêtre spécifiée et récupère un pointeur d’interface (ou des pointeurs) du contrôle.

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
Clé de licence du contrôle ; NULL si vous créez un contrôle sans licence.

### <a name="remarks"></a>Notes

Pour obtenir une description des paramètres restants et de la valeur de retour, consultez [CAxWindow :: CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) .

### <a name="example"></a>Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `CAxWindow2T::CreateControlLicEx`.

##  <a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

Récupère le nom de la classe de fenêtre.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers une chaîne contenant le nom de la classe de fenêtre (`AtlAxWinLic80`) qui peut héberger des contrôles ActiveX sous licence et sans licence.

##  <a name="operator_eq"></a>CAxWindow2T :: Operator =

Assigne un HWND à un objet `CAxWindow2T` existant.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Handle d’une fenêtre existante.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[FAQ sur la relation contenant-contenu des contrôles](../../atl/atl-control-containment-faq.md)
