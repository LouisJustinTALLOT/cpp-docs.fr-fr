---
description: 'En savoir plus sur : CBindStatusCallback, classe'
title: CBindStatusCallback, classe
ms.date: 11/04/2016
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 8c57328be0cb2678e671f68ac5bb44471056f457
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146976"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback, classe

Cette classe implémente l'interface `IBindStatusCallback` .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe contenant la fonction qui sera appelée lors de la réception des données.

*nBindFlags*<br/>
Spécifie les indicateurs de liaison qui sont retournés par [GetBindInfo](#getbindinfo). L’implémentation par défaut définit la liaison pour qu’elle soit asynchrone, récupère la version la plus récente des données/objets et ne stocke pas les données récupérées dans le cache disque.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback :: CBindStatusCallback](#cbindstatuscallback)|Constructeur.|
|[CBindStatusCallback :: ~ CBindStatusCallback](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback ::D lécharger](#download)|Méthode statique qui démarre le processus de téléchargement, crée un `CBindStatusCallback` objet et appelle `StartAsyncDownload` .|
|[CBindStatusCallback :: GetBindInfo](#getbindinfo)|Appelée par le moniker asynchrone pour demander des informations sur le type de liaison à créer.|
|[CBindStatusCallback :: getPriority,](#getpriority)|Appelée par le moniker asynchrone pour connaître la priorité de l’opération de liaison. L’implémentation ATL retourne `E_NOTIMPL` .|
|[CBindStatusCallback :: OnDataAvailable](#ondataavailable)|Appelé pour fournir des données à votre application lorsqu’elle est disponible. Lit les données, puis appelle la fonction qui lui est transmise pour utiliser les données.|
|[CBindStatusCallback :: OnLowResource](#onlowresource)|Appelé lorsque les ressources sont insuffisantes. L’implémentation ATL retourne S_OK.|
|[CBindStatusCallback :: OnObjectAvailable](#onobjectavailable)|Appelée par le moniker asynchrone pour passer un pointeur d’interface d’objet à votre application. L’implémentation ATL retourne S_OK.|
|[CBindStatusCallback :: OnProgress](#onprogress)|Appelé pour indiquer la progression d’un processus de téléchargement de données. L’implémentation ATL retourne S_OK.|
|[CBindStatusCallback :: OnStartBinding](#onstartbinding)|Appelé lorsque la liaison est démarrée.|
|[CBindStatusCallback :: OnStopBinding](#onstopbinding)|Appelé lorsque le transfert de données asynchrones est arrêté.|
|[CBindStatusCallback :: StartAsyncDownload](#startasyncdownload)|Initialise les octets disponibles et les octets lus à zéro, crée un objet de flux de type push à partir d’une URL et appelle `OnDataAvailable` chaque fois que des données sont disponibles.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback :: m_dwAvailableToRead](#m_dwavailabletoread)|Nombre d’octets disponibles pour la lecture.|
|[CBindStatusCallback :: m_dwTotalRead](#m_dwtotalread)|Nombre total d’octets lus.|
|[CBindStatusCallback :: m_pFunc](#m_pfunc)|Pointeur vers la fonction appelée lorsque des données sont disponibles.|
|[CBindStatusCallback :: m_pT](#m_pt)|Pointeur vers l’objet qui demande le transfert de données asynchrone.|
|[CBindStatusCallback :: m_spBindCtx](#m_spbindctx)|Pointeur vers l’interface [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) pour l’opération de liaison en cours.|
|[CBindStatusCallback :: m_spBinding](#m_spbinding)|Pointeur vers l' `IBinding` interface pour l’opération de liaison en cours.|
|[CBindStatusCallback :: m_spMoniker](#m_spmoniker)|Pointeur vers l’interface [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pour l’URL à utiliser.|
|[CBindStatusCallback :: m_spStream](#m_spstream)|Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) pour le transfert de données.|

## <a name="remarks"></a>Notes

La classe `CBindStatusCallback` implémente l'interface `IBindStatusCallback`. `IBindStatusCallback` doit être implémenté par votre application afin de pouvoir recevoir des notifications d’un transfert de données asynchrone. Le moniker asynchrone fourni par le système utilise des `IBindStatusCallback` méthodes pour envoyer et recevoir des informations sur le transfert de données asynchrone vers et à partir de votre objet.

En général, l' `CBindStatusCallback` objet est associé à une opération de liaison spécifique. Par exemple, dans l’exemple [Async](../../overview/visual-cpp-samples.md) , lorsque vous définissez la propriété URL, elle crée un `CBindStatusCallback` objet dans l’appel à `Download` :

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Le moniker asynchrone utilise la fonction `OnData` de rappel pour appeler votre application lorsqu’elle contient des données. Le moniker asynchrone est fourni par le système.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a> CBindStatusCallback :: CBindStatusCallback

Constructeur.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Notes

Crée un objet pour recevoir des notifications concernant le transfert de données asynchrones. En général, un objet est créé pour chaque opération de liaison.

Le constructeur initialise également [m_pT](#m_pt) et [m_pFunc](#m_pfunc) à null.

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a> CBindStatusCallback :: ~ CBindStatusCallback

Destructeur.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a> CBindStatusCallback ::D lécharger

Crée un `CBindStatusCallback` objet et appelle `StartAsyncDownload` pour commencer à télécharger des données de façon asynchrone à partir de l’URL spécifiée.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Paramètres

*Unis*<br/>
dans Pointeur vers l’objet qui demande le transfert de données asynchrone. L' `CBindStatusCallback` objet est mis en classe sur la classe de cet objet.

*pFunc*<br/>
dans Pointeur vers la fonction qui reçoit les données lues. La fonction est un membre de la classe de votre objet de type `T` . Pour obtenir la syntaxe et un exemple, consultez [StartAsyncDownload](#startasyncdownload) .

*bstrURL*<br/>
dans URL à partir de laquelle obtenir des données. Peut être n’importe quel nom d’URL ou de fichier valide. Ne peut pas avoir la valeur NULL. Par exemple :

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
dans `IUnknown` Du conteneur. NULL par défaut.

*bRelative*<br/>
dans Indicateur qui spécifie si l’URL est relative ou absolue. FALSe par défaut, ce qui signifie que l’URL est absolue.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Chaque fois que des données sont disponibles, elles sont envoyées à l’objet via `OnDataAvailable` . `OnDataAvailable` lit les données et appelle la fonction vers laquelle pointe *pFunc* (par exemple, pour stocker les données ou les imprimer à l’écran).

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a> CBindStatusCallback :: GetBindInfo

Appelé pour indiquer au moniker comment établir une liaison.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Paramètres

*pgrfBSCF*<br/>
à Pointeur vers des valeurs d’énumération BINDF indiquant comment l’opération de liaison doit se produire. Par défaut, définissez avec les valeurs d’énumération suivantes :

BINDF_ASYNCHRONOUS le téléchargement asynchrone.

BINDF_ASYNCSTORAGE `OnDataAvailable` renvoie E_PENDING lorsque les données ne sont pas encore disponibles au lieu de se bloquer jusqu’à ce que les données soient disponibles.

BINDF_GETNEWESTVERSION l’opération de liaison doit récupérer la version la plus récente des données.

BINDF_NOWRITECACHE l’opération de liaison ne doit pas stocker les données récupérées dans le cache disque.

*pbindinfo*<br/>
[in, out] Pointeur vers la `BINDINFO` structure qui donne plus d’informations sur la façon dont l’objet souhaite une liaison.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

L’implémentation par défaut définit la liaison pour qu’elle soit asynchrone et utilise le modèle de transmission de données. Dans le modèle de transmission de données, le moniker pilote l’opération de liaison asynchrone et notifie en continu au client chaque fois que de nouvelles données sont disponibles.

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a> CBindStatusCallback :: getPriority,

Appelée par le moniker asynchrone pour connaître la priorité de l’opération de liaison.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Paramètres

*pnPriority*<br/>
à Adresse de la variable **longue** qui, en cas de réussite, reçoit la priorité.

### <a name="return-value"></a>Valeur renvoyée

Retourne E_NOTIMPL.

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a> CBindStatusCallback :: m_dwAvailableToRead

Peut être utilisé pour stocker le nombre d’octets disponibles à lire.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Notes

Initialisé à zéro dans `StartAsyncDownload` .

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a> CBindStatusCallback :: m_dwTotalRead

Total cumulé d’octets lus dans le transfert de données asynchrones.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Notes

Incrémenté à chaque fois `OnDataAvailable` est appelé par le nombre d’octets réellement lus. Initialisé à zéro dans `StartAsyncDownload` .

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a> CBindStatusCallback :: m_pFunc

La fonction vers laquelle pointe le `m_pFunc` est appelée par `OnDataAvailable` après avoir lu les données disponibles (par exemple, pour stocker les données ou les imprimer à l’écran).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Notes

La fonction vers laquelle pointe `m_pFunc` est un membre de la classe de votre objet et possède la syntaxe suivante :

```cpp
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a> CBindStatusCallback :: m_pT

Pointeur vers l’objet qui demande le transfert de données asynchrone.

```
T* m_pT;
```

### <a name="remarks"></a>Notes

L' `CBindStatusCallback` objet est mis en classe sur la classe de cet objet.

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a> CBindStatusCallback :: m_spBindCtx

Pointeur vers une interface [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) qui fournit l’accès au contexte de liaison (un objet qui stocke des informations sur une opération de liaison de moniker particulière).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Notes

Initialisé dans `StartAsyncDownload` .

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a> CBindStatusCallback :: m_spBinding

Pointeur vers l' `IBinding` interface de l’opération de liaison actuelle.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Notes

Initialisé dans `OnStartBinding` et libéré dans `OnStopBinding` .

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a> CBindStatusCallback :: m_spMoniker

Pointeur vers l’interface [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pour l’URL à utiliser.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Notes

Initialisé dans `StartAsyncDownload` .

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a> CBindStatusCallback :: m_spStream

Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) de l’opération de liaison actuelle.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Notes

Initialisé dans `OnDataAvailable` à partir de la `STGMEDIUM` structure lorsque l’indicateur BCSF est BCSF_FIRSTDATANOTIFICATION et libéré lorsque l’indicateur BCSF est BCSF_LASTDATANOTIFICATION.

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a> CBindStatusCallback :: OnDataAvailable

Le moniker asynchrone fourni par le système appelle `OnDataAvailable` pour fournir des données à l’objet dès qu’il est disponible.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Paramètres

*grfBSCF*<br/>
dans Valeur d’énumération BSCF. Une ou plusieurs des valeurs suivantes : BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION ou BSCF_LASTDATANOTIFICATION.

*dwSize nul*<br/>
dans Quantité cumulée (en octets) des données disponibles depuis le début de la liaison. Peut être égal à zéro, ce qui indique que la quantité de données n’est pas pertinente ou qu’aucune quantité spécifique n’est devenue disponible.

*pformatetc*<br/>
dans Pointeur vers la structure [FORMATETC](/windows/win32/com/the-formatetc-structure) qui contient le format des données disponibles. S’il n’existe aucun format, peut être CF_NULL.

*pstgmed*<br/>
dans Pointeur vers la structure [STGMEDIUM](/windows/win32/com/the-stgmedium-structure) qui contient les données réelles maintenant disponibles.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`OnDataAvailable` lit les données, puis appelle une méthode de la classe de votre objet (par exemple, pour stocker les données ou les imprimer à l’écran). Pour plus d’informations, consultez [CBindStatusCallback :: StartAsyncDownload](#startasyncdownload) .

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a> CBindStatusCallback :: OnLowResource

Appelé lorsque les ressources sont insuffisantes.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a> CBindStatusCallback :: OnObjectAvailable

Appelée par le moniker asynchrone pour passer un pointeur d’interface d’objet à votre application.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
Identificateur d’interface de l’interface demandée. Inutilisé.

*Punk*<br/>
Adresse de l’interface IUnknown. Inutilisé.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a> CBindStatusCallback :: OnProgress

Appelé pour indiquer la progression d’un processus de téléchargement de données.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Paramètres

*ulProgress*<br/>
Entier long non signé. Inutilisé.

*ulProgressMax*<br/>
Entier long non signé inutilisé.

*ulStatusCode*<br/>
Entier long non signé. Inutilisé.

*szStatusText*<br/>
Adresse d’une valeur de chaîne. Inutilisé.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK.

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a> CBindStatusCallback :: OnStartBinding

Définit le membre de données [m_spBinding](#m_spbinding) sur le `IBinding` pointeur dans *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé à un usage ultérieur.

*pBinding*<br/>
dans Adresse de l’interface IBinding de l’opération de liaison actuelle. La valeur ne peut pas être NULL. Le client doit appeler AddRef sur ce pointeur pour conserver une référence à l’objet de liaison.

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a> CBindStatusCallback :: OnStopBinding

Libère le `IBinding` pointeur dans le membre de données [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Paramètres

*signé*<br/>
Code d’état retourné par l’opération de liaison.

*szError*<br/>
Adresse d’une valeur de chaîne. Inutilisé.

### <a name="remarks"></a>Notes

Appelé par le moniker fourni par le système pour indiquer la fin de l’opération de liaison.

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a> CBindStatusCallback :: StartAsyncDownload

Démarre le téléchargement de données de façon asynchrone à partir de l’URL spécifiée.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Paramètres

*Unis*<br/>
dans Pointeur vers l’objet qui demande le transfert de données asynchrone. L' `CBindStatusCallback` objet est mis en classe sur la classe de cet objet.

*pFunc*<br/>
dans Pointeur vers la fonction qui reçoit les données lues. La fonction est un membre de la classe de votre objet de type `T` . Pour obtenir la syntaxe et un exemple, consultez la **section Notes** .

*bstrURL*<br/>
dans URL à partir de laquelle obtenir des données. Peut être n’importe quel nom d’URL ou de fichier valide. Ne peut pas avoir la valeur NULL. Par exemple :

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
dans `IUnknown` Du conteneur. NULL par défaut.

*bRelative*<br/>
dans Indicateur qui spécifie si l’URL est relative ou absolue. FALSe par défaut, ce qui signifie que l’URL est absolue.

### <a name="return-value"></a>Valeur renvoyée

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Chaque fois que des données sont disponibles, elles sont envoyées à l’objet via `OnDataAvailable` . `OnDataAvailable` lit les données et appelle la fonction vers laquelle pointe *pFunc* (par exemple, pour stocker les données ou les imprimer à l’écran).

La fonction vers laquelle pointe *pFunc* est un membre de la classe de votre objet et possède la syntaxe suivante :

```cpp
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

Dans l’exemple suivant (extrait de l’exemple [Async](../../overview/visual-cpp-samples.md) ), la fonction `OnData` écrit les données reçues dans une zone de texte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
