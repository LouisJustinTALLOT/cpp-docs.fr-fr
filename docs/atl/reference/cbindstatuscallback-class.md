---
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
ms.openlocfilehash: 6e5e55a23ee678bbedf76f608bc4fdf562cc1822
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773123"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback, classe

Cette classe implémente l'interface `IBindStatusCallback` .

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe qui contient la fonction est appelée lorsque les données sont reçues.

*nBindFlags*<br/>
Spécifie les indicateurs de liaison qui sont retournés par [GetBindInfo](#getbindinfo). L’implémentation par défaut définit la liaison asynchrone récupère la dernière version de l’objet de données/et ne stocke pas les données récupérées dans le cache disque.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Constructeur.|
|[CBindStatusCallback::~CBindStatusCallback](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Méthode statique qui démarre le processus de téléchargement, crée un `CBindStatusCallback` objet et appelle `StartAsyncDownload`.|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Appelé par le moniker asynchrone pour demander des informations sur le type de liaison doit être créé.|
|[CBindStatusCallback::GetPriority](#getpriority)|Appelé par le moniker asynchrone pour obtenir la priorité de l’opération de liaison. Retourne l’implémentation ATL `E_NOTIMPL`.|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Appelé pour fournir des données à votre application dès que possible. Lit les données, puis appelle la fonction qui lui est passée à utiliser les données.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Appelé lorsque les ressources sont insuffisantes. L’implémentation de ATL retourne S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Appelé par le moniker asynchrone à passer un pointeur d’interface objet à votre application. L’implémentation de ATL retourne S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Appelé pour indiquer la progression d’un processus de téléchargement de données. L’implémentation de ATL retourne S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Appelé lorsque la liaison est démarrée.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Appelée lorsque le transfert de données asynchrone est arrêté.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Initialise les octets disponibles et les octets lus à zéro, crée un objet de flux de données de type push à partir d’une URL et les appels `OnDataAvailable` chaque fois que les données sont disponibles.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Nombre d’octets à lire.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Nombre total d’octets lus.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Pointeur vers la fonction appelée lorsque les données sont disponibles.|
|[CBindStatusCallback::m_pT](#m_pt)|Pointeur vers l’objet qui demande le transfert de données asynchrone.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Pointeur vers le [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) interface pour l’opération de liaison actuel.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Pointeur vers le `IBinding` interface pour l’opération de liaison actuel.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Pointeur vers le [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker) interface pour l’URL à utiliser.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Pointeur vers le [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interface pour le transfert de données.|

## <a name="remarks"></a>Notes

La classe `CBindStatusCallback` implémente l'interface `IBindStatusCallback`. `IBindStatusCallback` doit être implémentée par votre application afin qu’il peut recevoir des notifications à partir d’un transfert de données asynchrone. Utilise le moniker asynchrone fourni par le système `IBindStatusCallback` méthodes pour envoyer et recevoir des informations sur les données asynchrones de transfert vers et à partir de votre objet.

En règle générale, le `CBindStatusCallback` objet est associé à une opération de liaison spécifique. Par exemple, dans le [ASYNC](../../overview/visual-cpp-samples.md) exemple, lorsque vous définissez la propriété URL, il crée un `CBindStatusCallback` objet dans l’appel à `Download`:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Le moniker asynchrone utilise la fonction de rappel `OnData` pour appeler votre application lorsqu’elle comporte des données. Le moniker asynchrone est fourni par le système.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="cbindstatuscallback"></a>  CBindStatusCallback::CBindStatusCallback

Constructeur.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Notes

Crée un objet pour recevoir des notifications concernant le transfert de données asynchrone. En règle générale, un objet est créé pour chaque opération de liaison.

Le constructeur initialise également [m_pT](#m_pt) et [m_pFunc](#m_pfunc) avec la valeur NULL.

##  <a name="dtor"></a>  CBindStatusCallback::~CBindStatusCallback

Destructeur.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="download"></a>  CBindStatusCallback::Download

Crée un `CBindStatusCallback` objet et appelle `StartAsyncDownload` pour démarrer le téléchargement des données de façon asynchrone à partir de l’URL spécifiée.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Paramètres

*pT*<br/>
[in] Pointeur vers l’objet qui demande le transfert de données asynchrone. Le `CBindStatusCallback` transformer en modèle d’objet de cette classe de l’objet.

*pFunc*<br/>
[in] Pointeur vers la fonction qui reçoit les données sont lues. La fonction est un membre de classe de l’objet de type `T`. Consultez [StartAsyncDownload](#startasyncdownload) pour la syntaxe et un exemple.

*bstrURL*<br/>
[in] L’URL pour obtenir des données à partir de. Peut être n’importe quel nom de fichier ou URL valide. Ne peut pas être Null. Exemple :

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] Le `IUnknown` du conteneur. NULL par défaut.

*bRelative*<br/>
[in] Un indicateur qui spécifie si l’URL est relative ou absolue. FALSE par défaut, ce qui signifie que l’URL est absolue.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Chaque fois que les données sont disponibles, il est envoyé à l’objet via `OnDataAvailable`. `OnDataAvailable` lit les données et appelle la fonction vers laquelle pointée *pFunc* (par exemple, pour stocker les données ou l’imprimer à l’écran).

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

Appelé pour indiquer le moniker de la liaison.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Paramètres

*pgrfBSCF*<br/>
[out] Pointeur vers les valeurs d’énumération BINDF indiquant comment l’opération de liaison doit se produire. Par défaut, définie avec les valeurs d’énumération suivantes :

Téléchargement asynchrone BINDF_ASYNCHRONOUS.

BINDF_ASYNCSTORAGE `OnDataAvailable` renvoie E_PENDING lorsque les données ne sont pas encore disponibles au lieu de bloquer jusqu'à ce que les données sont disponibles.

L’opération de liaison BINDF_GETNEWESTVERSION doit récupérer la version la plus récente des données.

BINDF_NOWRITECACHE l’opération de liaison ne doit pas stocker les données dans le cache disque récupérées.

*pbindinfo*<br/>
[in, out] Un pointeur vers le `BINDINFO` structure, ce qui donne plus d’informations sur la façon dont l’objet souhaite liaison se produise.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

L’implémentation par défaut définit la liaison asynchrone et à utiliser le modèle d’émission de données. Dans le modèle d’émission de données, le moniker pilote l’opération de liaison asynchrone et en permanence informe le client chaque fois que les nouvelles données sont disponibles.

##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority

Appelé par le moniker asynchrone pour obtenir la priorité de l’opération de liaison.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Paramètres

*pnPriority*<br/>
[out] Adresse de la **LONG** variable qui, en cas de réussite, reçoit la priorité.

### <a name="return-value"></a>Valeur de retour

Returns E_NOTIMPL.

##  <a name="m_dwavailabletoread"></a>  CBindStatusCallback::m_dwAvailableToRead

Peut être utilisé pour stocker le nombre d’octets disponibles pour la lecture.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Notes

Initialisé à zéro `StartAsyncDownload`.

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

Le total cumulé d’octets lus dans le transfert de données asynchrone.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Notes

Incrémenté à chaque modification `OnDataAvailable` est appelée par le nombre d’octets réellement lus. Initialisé à zéro `StartAsyncDownload`.

##  <a name="m_pfunc"></a>  CBindStatusCallback::m_pFunc

La fonction vers laquelle pointe `m_pFunc` est appelée par `OnDataAvailable` après avoir lu les données disponibles (par exemple, pour stocker les données ou l’imprimer à l’écran).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Notes

La fonction vers laquelle pointe `m_pFunc` est un membre de classe de l’objet et présente la syntaxe suivante :

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

Pointeur vers l’objet qui demande le transfert de données asynchrone.

```
T* m_pT;
```

### <a name="remarks"></a>Notes

Le `CBindStatusCallback` transformer en modèle d’objet de cette classe de l’objet.

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

Un pointeur vers un [IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx) interface qui fournit l’accès au contexte de liaison (un objet qui stocke des informations sur une opération de liaison de moniker particulier).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Notes

Initialisé dans `StartAsyncDownload`.

##  <a name="m_spbinding"></a>  CBindStatusCallback::m_spBinding

Un pointeur vers le `IBinding` interface de l’opération de liaison actuel.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Notes

Initialisé dans `OnStartBinding` et publiées dans `OnStopBinding`.

##  <a name="m_spmoniker"></a>  CBindStatusCallback::m_spMoniker

Un pointeur vers le [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker) interface pour l’URL à utiliser.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Notes

Initialisé dans `StartAsyncDownload`.

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

Un pointeur vers le [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interface de l’opération de liaison actuel.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Notes

Initialisé dans `OnDataAvailable` à partir de la `STGMEDIUM` structure lors de l’indicateur BCSF est BCSF_FIRSTDATANOTIFICATION et libérée lorsque l’indicateur BCSF est BCSF_LASTDATANOTIFICATION.

##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable

Les appels de système de moniker asynchrone `OnDataAvailable` pour fournir des données à l’objet qu’il est disponible.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Paramètres

*grfBSCF*<br/>
[in] Une valeur d’énumération BSCF. Un ou plusieurs des opérations suivantes : BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION, or BSCF_LASTDATANOTIFICATION.

*dwSize*<br/>
[in] La quantité cumulée (en octets) de données disponibles depuis le début de la liaison. Peut être égal à zéro, indiquant que la quantité de données n’est pas pertinente ou qu’aucune quantité spécifique est devenue disponible.

*pformatetc*<br/>
[in] Pointeur vers le [FORMATETC](/windows/desktop/com/the-formatetc-structure) structure qui contient le format des données disponibles. S’il n’existe aucun format, peut être CF_NULL.

*pstgmed*<br/>
[in] Pointeur vers le [STGMEDIUM](/windows/desktop/com/the-stgmedium-structure) structure qui contient les données réelles désormais disponibles.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

`OnDataAvailable` lit les données, puis appelle une méthode de classe de l’objet (par exemple, pour stocker les données ou l’imprimer à l’écran). Consultez [CBindStatusCallback::StartAsyncDownload à laquelle sont](#startasyncdownload) pour plus d’informations.

##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource

Appelé lorsque les ressources sont insuffisantes.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="onobjectavailable"></a>  CBindStatusCallback::OnObjectAvailable

Appelé par le moniker asynchrone à passer un pointeur d’interface objet à votre application.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
Identificateur d’interface de l’interface demandée. Non utilisé.

*punk*<br/>
Adresse de l’interface IUnknown. Non utilisé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="onprogress"></a>  CBindStatusCallback::OnProgress

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
Entier long non signé. Non utilisé.

*ulProgressMax*<br/>
Entier long non signé n’est pas utilisé.

*ulStatusCode*<br/>
Entier long non signé. Non utilisé.

*szStatusText*<br/>
Adresse d’une valeur de chaîne. Non utilisé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding

Définit le membre de données [m_spBinding](#m_spbinding) à la `IBinding` pointeur dans *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé à un usage ultérieur.

*pBinding*<br/>
[in] Adresse de l’interface IBinding d’actuel une opération de liaison. Cela ne peut pas être NULL. Le client doit appeler AddRef sur ce pointeur pour conserver une référence à l’objet de liaison.

##  <a name="onstopbinding"></a>  CBindStatusCallback::OnStopBinding

Versions le `IBinding` pointeur dans le membre de données [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Paramètres

*hresult*<br/>
Code d’état retourné à partir de l’opération de liaison.

*szError*<br/>
Adresse d’une valeur de chaîne. Non utilisé.

### <a name="remarks"></a>Notes

Appelé par le moniker asynchrone fourni par le système pour indiquer la fin de l’opération de liaison.

##  <a name="startasyncdownload"></a>  CBindStatusCallback::StartAsyncDownload

Démarre le téléchargement des données de façon asynchrone à partir de l’URL spécifiée.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Paramètres

*pT*<br/>
[in] Pointeur vers l’objet qui demande le transfert de données asynchrone. Le `CBindStatusCallback` transformer en modèle d’objet de cette classe de l’objet.

*pFunc*<br/>
[in] Pointeur vers la fonction qui reçoit les données en cours de lecture. La fonction est un membre de classe de l’objet de type `T`. Consultez **remarques** pour la syntaxe et un exemple.

*bstrURL*<br/>
[in] L’URL pour obtenir des données à partir de. Peut être n’importe quel nom de fichier ou URL valide. Ne peut pas être Null. Exemple :

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] Le `IUnknown` du conteneur. NULL par défaut.

*bRelative*<br/>
[in] Un indicateur qui spécifie si l’URL est relative ou absolue. FALSE par défaut, ce qui signifie que l’URL est absolue.

### <a name="return-value"></a>Valeur de retour

Une des valeurs HRESULT standards.

### <a name="remarks"></a>Notes

Chaque fois que les données sont disponibles, il est envoyé à l’objet via `OnDataAvailable`. `OnDataAvailable` lit les données et appelle la fonction vers laquelle pointée *pFunc* (par exemple, pour stocker les données ou l’imprimer à l’écran).

La fonction vers laquelle pointe *pFunc* est un membre de classe de l’objet et présente la syntaxe suivante :

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

Dans l’exemple suivant (provenant du [ASYNC](../../overview/visual-cpp-samples.md) exemple), la fonction `OnData` écrit les données reçues dans une zone de texte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
