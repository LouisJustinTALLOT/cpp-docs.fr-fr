---
title: Classe CBindStatusCallback
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
ms.openlocfilehash: 0ae7f4fcdba18be84d99140e395b6f2ac3db792a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748202"
---
# <a name="cbindstatuscallback-class"></a>Classe CBindStatusCallback

Cette classe implémente l’interface `IBindStatusCallback`.

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
Votre classe contenant la fonction qui sera appelée au fur et à mesure que les données seront reçues.

*nBindFlags (en)*<br/>
Spécifie les drapeaux de liaison qui sont retournés par [GetBindInfo](#getbindinfo). L’implémentation par défaut définit la liaison comme étant asynchrone, récupère la version la plus récente des données/objet, et ne stocke pas les données récupérées dans le cache du disque.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Constructeur.|
|[CBindStatusCallback: :CBindStatusCallback](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Méthode statique qui démarre le `CBindStatusCallback` processus de `StartAsyncDownload`téléchargement, crée un objet, et appelle .|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Appelé par le surnom asynchrone pour demander des informations sur le type de liaison à créer.|
|[CBindStatusCallback::GetPriority](#getpriority)|Appelé par le surnom asynchrone pour obtenir la priorité de l’opération de liaison. La mise en `E_NOTIMPL`œuvre ATL revient .|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|Appelé à fournir des données à votre application dès qu’elles deviennent disponibles. Lit les données, puis appelle la fonction qui lui est transmise pour utiliser les données.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Appelé quand les ressources sont faibles. La mise en œuvre d’ATL S_OK.|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|Appelé par le surnom asynchrone pour passer un pointeur d’interface objet à votre application. La mise en œuvre d’ATL S_OK.|
|[CBindStatusCallback::OnProgress](#onprogress)|Appelé pour indiquer l’avancement d’un processus de téléchargement de données. La mise en œuvre d’ATL S_OK.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Appelé lorsque la liaison est commencée.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Appelé lorsque le transfert de données asynchrone est arrêté.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Initialise les octets disponibles et les octets lus à zéro, crée `OnDataAvailable` un objet de flux de type push à partir d’une URL, et appelle chaque fois que des données sont disponibles.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Nombre d’octets disponibles à lire.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Nombre total d’octets lus.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Pointeur vers la fonction appelée lorsque les données sont disponibles.|
|[CBindStatusCallback::m_pT](#m_pt)|Pointeur vers l’objet demandant le transfert de données asynchrone.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Pointeur vers l’interface [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) pour le fonctionnement actuel de liaison.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Pointeur `IBinding` vers l’interface pour le fonctionnement actuel de liaison.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Pointeur vers l’interface [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pour l’URL à utiliser.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Pointeur vers l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) pour le transfert de données.|

## <a name="remarks"></a>Notes

La classe `CBindStatusCallback` implémente l’interface `IBindStatusCallback`. `IBindStatusCallback`doit être implémenté par votre application afin qu’elle puisse recevoir des notifications d’un transfert de données asynchrone. Le surnom asynchrone fourni par le `IBindStatusCallback` système utilise des méthodes pour envoyer et recevoir des informations sur le transfert de données asynchrones à et depuis votre objet.

Typiquement, `CBindStatusCallback` l’objet est associé à une opération de liaison spécifique. Par exemple, dans l’échantillon [ASYNC,](../../overview/visual-cpp-samples.md) lorsque vous `CBindStatusCallback` définissez la `Download`propriété URL, il crée un objet dans l’appel à :

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Le surnom asynchrone utilise la fonction `OnData` de rappel pour appeler votre application quand il a des données. Le surnom asynchrone est fourni par le système.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

Constructeur.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Notes

Crée un objet pour recevoir des notifications concernant le transfert de données asynchrone. Typiquement, un objet est créé pour chaque opération de liaison.

Le constructeur est également en train [d’initialiser m_pT](#m_pt) et [m_pFunc](#m_pfunc) à NULL.

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a>CBindStatusCallback: :CBindStatusCallback

Destructeur.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a>CBindStatusCallback::Download

Crée `CBindStatusCallback` un objet `StartAsyncDownload` et des appels pour commencer à télécharger des données asynchronement à partir de l’URL spécifiée.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
[dans] Un pointeur de l’objet demandant le transfert de données asynchrone. L’objet `CBindStatusCallback` est templatisé sur la classe de cet objet.

*pFunc (pFunc)*<br/>
[dans] Un pointeur à la fonction qui reçoit les données qui sont lues. La fonction est un membre de la `T`classe de type de votre objet . Voir [StartAsyncDownload](#startasyncdownload) pour la syntaxe et un exemple.

*bstrURL*<br/>
[dans] L’URL pour obtenir des données à partir. Peut être n’importe quelle URL valide ou nom de fichier. Ne peut pas avoir la valeur NULL. Par exemple :

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer (en)*<br/>
[dans] Le `IUnknown` conteneur. NULL par défaut.

*bRelative*<br/>
[dans] Un drapeau indiquant si l’URL est relative ou absolue. FALSE par défaut, ce qui signifie que l’URL est absolue.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Chaque fois que des données sont `OnDataAvailable`disponibles, elles sont envoyées à l’objet par l’intermédiaire . `OnDataAvailable`lit les données et appelle la fonction pointée par *pFunc* (par exemple, pour stocker les données ou les imprimer à l’écran).

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a>CBindStatusCallback::GetBindInfo

Appelé pour dire au surnom comment lier.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Paramètres

*pgrfBSCF*<br/>
[out] Un pointeur sur les valeurs de recensement BINDF indiquant comment le fonctionnement de liaison devrait se produire. Par défaut, défini avec les valeurs d’énumération suivantes :

BINDF_ASYNCHRONOUS téléchargement Asynchrone.

BINDF_ASYNCSTORAGE `OnDataAvailable` renvoie E_PENDING lorsque les données ne sont pas encore disponibles plutôt que de bloquer jusqu’à ce que les données soient disponibles.

BINDF_GETNEWESTVERSION L’opération de liaison doit récupérer la version la plus récente des données.

BINDF_NOWRITECACHE L’opération de liaison ne doit pas stocker les données récupérées dans le cache du disque.

*pbindinfo (en anglais)*<br/>
[dans, dehors] Un pointeur `BINDINFO` à la structure donnant plus d’informations sur la façon dont l’objet veut la liaison de se produire.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

La implémentation par défaut définit la liaison comme étant asynchrone et à utiliser le modèle de données-poussée. Dans le modèle de transmission de données, le surnom conduit le fonctionnement asynchrone de liaison et informe continuellement le client chaque fois que de nouvelles données sont disponibles.

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a>CBindStatusCallback::GetPriority

Appelé par le surnom asynchrone pour obtenir la priorité de l’opération de liaison.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Paramètres

*pnPriorité*<br/>
[out] Adresse de la variable **LONG** qui, sur le succès, reçoit la priorité.

### <a name="return-value"></a>Valeur de retour

Retourne E_NOTIMPL.

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead

Peut être utilisé pour stocker le nombre d’octets disponibles pour être lus.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Notes

Initialisé à `StartAsyncDownload`zéro en .

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead

Le total cumulatif des octets lue dans le transfert de données asynchrone.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Notes

Incrémenté chaque `OnDataAvailable` fois est appelé par le nombre d’octets effectivement lu. Initialisé à `StartAsyncDownload`zéro en .

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a>CBindStatusCallback::m_pFunc

La fonction pointée `m_pFunc` par `OnDataAvailable` est appelée par après qu’il lit les données disponibles (par exemple, pour stocker les données ou les imprimer à l’écran).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Notes

La fonction indiquée par `m_pFunc` est un membre de la classe de votre objet et a la syntaxe suivante:

```cpp
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a>CBindStatusCallback::m_pT

Un pointeur de l’objet demandant le transfert de données asynchrone.

```
T* m_pT;
```

### <a name="remarks"></a>Notes

L’objet `CBindStatusCallback` est templatisé sur la classe de cet objet.

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx

Un pointeur vers une interface [IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) qui donne accès au contexte de liaison (un objet qui stocke des informations sur une opération de liaison de surnom particulier).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Notes

Initialisé `StartAsyncDownload`dans .

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

Un pointeur `IBinding` à l’interface de l’opération de liaison actuelle.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Notes

Initialisé `OnStartBinding` et publié `OnStopBinding`dans .

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker

Un pointeur à l’interface [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pour l’URL à utiliser.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Notes

Initialisé `StartAsyncDownload`dans .

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a>CBindStatusCallback::m_spStream

Un pointeur à l’interface [IStream](/windows/win32/api/objidl/nn-objidl-istream) de l’opération de liaison actuelle.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Notes

Initialisé `OnDataAvailable` à `STGMEDIUM` partir de la structure lorsque le drapeau BCSF est BCSF_FIRSTDATANOTIFICATION et libéré lorsque le drapeau BCSF est BCSF_LASTDATANOTIFICATION.

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a>CBindStatusCallback::OnDataAvailable

Le surnom asynchrone fourni par `OnDataAvailable` le système appelle à fournir des données à l’objet dès qu’il devient disponible.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Paramètres

*grfBSCF*<br/>
[dans] Une valeur de recensement BSCF. Un ou plusieurs des éléments suivants : BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION ou BSCF_LASTDATANOTIFICATION.

*dwSize dwSize*<br/>
[dans] Le montant cumulatif (dans les octets) des données disponibles depuis le début de la liaison. Peut être nul, ce qui indique que la quantité de données n’est pas pertinente ou qu’aucun montant spécifique n’est devenu disponible.

*pformatetc*<br/>
[dans] Pointeur vers la structure [FORMATETC](/windows/win32/com/the-formatetc-structure) qui contient le format des données disponibles. S’il n’y a pas de format, peut être CF_NULL.

*pstgmed*<br/>
[dans] Pointeur vers la structure [STGMEDIUM](/windows/win32/com/the-stgmedium-structure) qui contient les données réelles maintenant disponibles.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

`OnDataAvailable`lit les données, puis appelle une méthode de la classe de votre objet (par exemple, pour stocker les données ou les imprimer à l’écran). Voir [CBindStatusCallback:StartAsyncDownload](#startasyncdownload) pour plus de détails.

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a>CBindStatusCallback::OnLowResource

Appelé quand les ressources sont faibles.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a>CBindStatusCallback::OnObjectAvailable

Appelé par le surnom asynchrone pour passer un pointeur d’interface objet à votre application.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
Identifiant d’interface de l’interface demandée. Inutilisé.

*Punk*<br/>
Adresse de l’interface IUnknown. Inutilisé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a>CBindStatusCallback::OnProgress

Appelé pour indiquer l’avancement d’un processus de téléchargement de données.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Paramètres

*ulProgress*<br/>
Unsigned long integer. Inutilisé.

*ulProgressMax*<br/>
Insigné longtemps integer inutilisé.

*ulStatusCode ulStatusCode ulStatusCode ulStat*<br/>
Unsigned long integer. Inutilisé.

*szStatusText*<br/>
Adresse d’une valeur de chaîne. Inutilisé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK.

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding

Définit le [m_spBinding](#m_spbinding) membre de données `IBinding` m_spBinding au pointeur dans *pBinding*.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé pour un usage futur.

*pBinding (en)*<br/>
[dans] Adresse de l’interface IBinding de l’opération de liaison actuelle. Cela ne peut pas être NULL. Le client doit appeler AddRef sur ce pointeur pour garder une référence à l’objet de liaison.

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding

Libère `IBinding` le pointeur dans le membre de données [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Paramètres

*Hresult*<br/>
Code d’état retourné de l’opération de liaison.

*szError*<br/>
Adresse d’une valeur de chaîne. Inutilisé.

### <a name="remarks"></a>Notes

Appelé par le surnom asynchrone fourni par le système pour indiquer la fin de l’opération de liaison.

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

Commence à télécharger des données asynchronement à partir de l’URL spécifiée.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
[dans] Un pointeur de l’objet demandant le transfert de données asynchrone. L’objet `CBindStatusCallback` est templatisé sur la classe de cet objet.

*pFunc (pFunc)*<br/>
[dans] Un pointeur à la fonction qui reçoit les données lues. La fonction est un membre de la `T`classe de type de votre objet . Voir **Remarques** pour la syntaxe et un exemple.

*bstrURL*<br/>
[dans] L’URL pour obtenir des données à partir. Peut être n’importe quelle URL valide ou nom de fichier. Ne peut pas avoir la valeur NULL. Par exemple :

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer (en)*<br/>
[dans] Le `IUnknown` conteneur. NULL par défaut.

*bRelative*<br/>
[dans] Un drapeau indiquant si l’URL est relative ou absolue. FALSE par défaut, ce qui signifie que l’URL est absolue.

### <a name="return-value"></a>Valeur de retour

L’une des valeurs HRESULT standard.

### <a name="remarks"></a>Notes

Chaque fois que des données sont `OnDataAvailable`disponibles, elles sont envoyées à l’objet par l’intermédiaire . `OnDataAvailable`lit les données et appelle la fonction pointée par *pFunc* (par exemple, pour stocker les données ou les imprimer à l’écran).

La fonction indiquée par *pFunc* est un membre de la classe de votre objet et a la syntaxe suivante:

```cpp
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

Dans l’exemple suivant (tiré de l’échantillon [ASYNC),](../../overview/visual-cpp-samples.md) la fonction `OnData` écrit les données reçues dans une boîte de texte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
