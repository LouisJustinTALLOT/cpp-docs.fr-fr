---
title: Classe CAxWindow2T
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
ms.openlocfilehash: 14080b624132979df533135bc1eef108dc793398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318695"
---
# <a name="caxwindow2t-class"></a>Classe CAxWindow2T

Cette classe fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX, et a également le soutien pour l’hébergement des contrôles ActiveX sous licence.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Paramètres

*TBase (TBase)*<br/>
La classe `CAxWindowT` dont dérive la classe.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Construit un objet `CAxWindow2T`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAxWindow2T::Créer](#create)|Crée une fenêtre d’hôte.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Crée un contrôle ActiveX sous licence, puis initialise et héberge ce dernier dans la fenêtre spécifiée.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Crée un contrôle ActiveX sous licence, l’initialise, l’héberge dans la fenêtre spécifiée et récupère un pointeur d’interface (ou des pointeurs) du contrôle.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Méthode statique qui récupère le nom de la classe de fenêtre.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAxWindow2T::opérateur](#operator_eq)|Assigne un HWND `CAxWindow2T` à un objet existant.|

## <a name="remarks"></a>Notes

`CAxWindow2T`fournit des méthodes pour manipuler une fenêtre qui héberge un contrôle ActiveX. `CAxWindow2T`a également un support pour l’hébergement de contrôles ActiveX sous licence. L’hébergement est fourni par " **AtlAxWinLic80**", qui est enveloppé par `CAxWindow2T`.

La `CAxWindow2` classe est mise en `CAxWindow2T` œuvre comme une spécialisation de la classe. Cette spécialisation est déclarée comme :

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT`membres sont documentés sous [CAxWindow](../../atl/reference/caxwindow-class.md).

Voir [Les contrôles Hosting ActiveX à l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise les membres de cette classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

Construit un objet `CAxWindow2T`.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Une poignée d’une fenêtre existante.

## <a name="caxwindow2tcreate"></a><a name="create"></a>CAxWindow2T::Créer

Crée une fenêtre d’hôte.

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

`CAxWindow2T::Create`appelle [CWindow::Créer](../../atl/reference/cwindow-class.md#create) avec le paramètre *LPCTSTR lpstrWndClass* réglé`AtlAxWinLic80`à la classe de fenêtre qui fournit l’hébergement de contrôle ( ).

Voir `CWindow::Create` pour une description des paramètres et de la valeur de retour.

**Note** Si 0 est utilisé comme valeur pour le paramètre *MenuOrID,* il doit être spécifié comme 0U (la valeur par défaut) pour éviter une erreur de compilateur.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `CAxWindow2T::Create`.

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

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

*bstrLicKey (en)*<br/>
La clé de licence pour le contrôle; NULL si la création d’un contrôle non autorisé.

### <a name="remarks"></a>Notes

Voir [CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) pour une description des paramètres restants et la valeur de retour.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `CAxWindow2T::CreateControlLic`.

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

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

*bstrLicKey (en)*<br/>
La clé de licence pour le contrôle; NULL si la création d’un contrôle non autorisé.

### <a name="remarks"></a>Notes

Voir [CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) pour une description des paramètres restants et de la valeur de retour.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `CAxWindow2T::CreateControlLicEx`.

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

Récupère le nom de la classe de fenêtre.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à une chaîne contenant`AtlAxWinLic80`le nom de la classe de fenêtre ( ) qui peut accueillir des commandes ActiveX sous licence et non autorisées.

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a>CAxWindow2T::opérateur

Assigne un HWND `CAxWindow2T` à un objet existant.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Une poignée d’une fenêtre existante.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[FAQ sur la relation contenant-contenu des contrôles](../../atl/atl-control-containment-faq.md)
