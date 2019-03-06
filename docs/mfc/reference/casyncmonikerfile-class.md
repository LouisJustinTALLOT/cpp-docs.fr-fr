---
title: CAsyncMonikerFile, classe
ms.date: 11/04/2016
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
ms.openlocfilehash: b86cba0c2e8f7991902a552d404355d6c1474138
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425820"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile, classe

Fournit les fonctionnalités nécessaires à l'utilisation de monikers asynchrones dans les contrôles ActiveX (anciennement contrôles OLE).

## <a name="syntax"></a>Syntaxe

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|Construit un objet `CAsyncMonikerFile`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAsyncMonikerFile::Close](#close)|Ferme et libère toutes les ressources.|
|[CAsyncMonikerFile::GetBinding](#getbinding)|Récupère un pointeur vers la liaison de transfert asynchrone.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Récupère le format des données dans le flux de données.|
|[CAsyncMonikerFile::Open](#open)|Ouvre un fichier de façon asynchrone.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Crée un objet COM qui implémente `IBindStatusCallback`.|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Appelée par la bibliothèque du système OLE pour demander des informations sur le type de liaison doit être créé.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Appelée par la bibliothèque du système OLE pour obtenir la priorité de la liaison.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Appelé pour fournir des données dès qu’elles sont disponible pour le client lors des opérations de liaison asynchrone.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Appelé lorsque les ressources sont insuffisantes.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Appelé pour indiquer la progression sur les processus de téléchargement de données.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Appelé lorsque la liaison démarre.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Appelé lorsque le transfert asynchrone est arrêté.|

## <a name="remarks"></a>Notes

Dérivé de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), qui, à son tour, est dérivée de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` utilise le [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker) interface pour accéder à n’importe quel flux de données en mode asynchrone, y compris le chargement asynchrone de fichiers à partir d’une URL. Les fichiers peuvent être des propriétés de chemin de données des contrôles ActiveX.

Monikers asynchrones sont utilisés principalement dans les applications compatibles avec Internet et les contrôles ActiveX pour fournir une interface utilisateur réactive pendant les transferts de fichiers. Un parfait exemple de ceci est l’utilisation de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) pour fournir des propriétés asynchrones pour les contrôles ActiveX. Le `CDataPathProperty` objet obtenez à plusieurs reprises un rappel pour indiquer la disponibilité de nouvelles données lors d’un processus d’exchange de propriété de longue durée.

Pour plus d’informations sur l’utilisation des monikers asynchrones et des contrôles ActiveX dans les applications Internet, consultez les articles suivants :

- [Internet premières étapes : Monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Internet premières étapes : Contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Spécifications

**En-tête :** afxole.h

##  <a name="casyncmonikerfile"></a>  CAsyncMonikerFile::CAsyncMonikerFile

Construit un objet `CAsyncMonikerFile`.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Notes

Il ne crée pas le `IBindHost` interface. `IBindHost` est utilisé uniquement si vous fournissez dans le `Open` fonction membre.

Pour obtenir une description de le `IBindHost` l’interface, consultez le kit SDK Windows.

##  <a name="close"></a>  CAsyncMonikerFile::Close

Appelez cette fonction pour fermer et libérer toutes les ressources.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Peut être appelée sur des fichiers non ouverts ou déjà fermés.

##  <a name="createbindstatuscallback"></a>  CAsyncMonikerFile::CreateBindStatusCallback

Crée un objet COM qui implémente `IBindStatusCallback`.

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Paramètres

*pUnkControlling*<br/>
Un pointeur vers l’inconnu de contrôle (externe `IUnknown`) ou NULL si l’agrégation n’est pas utilisée.

### <a name="return-value"></a>Valeur de retour

Si *pUnkControlling* n’est pas NULL, la fonction retourne un pointeur à l’exception interne `IUnknown` sur un nouvel objet COM prenant en charge `IBindStatusCallback`. Si `pUnkControlling` est NULL, la fonction retourne un pointeur vers un `IUnknown` sur un nouvel objet COM prenant en charge `IBindStatusCallback`.

### <a name="remarks"></a>Notes

`CAsyncMonikerFile` nécessite un objet COM qui implémente `IBindStatusCallback`. MFC implémente ce type d’objet, et il ne peut être agrégée. Vous pouvez remplacer `CreateBindStatusCallback` pour retourner votre propre objet COM. Votre objet COM peut agréger l’implémentation MFC en appelant `CreateBindStatusCallback` avec inconnu de contrôle de votre objet COM. Les objets COM implémentées à l’aide de la `CCmdTarget` prise en charge COM peut récupérer le contrôle inconnu à l’aide de `CCmdTarget::GetControllingUnknown`.

Ou bien, votre objet COM peut déléguer à l’implémentation MFC en appelant `CreateBindStatusCallback( NULL )`.

[CAsyncMonikerFile::Open](#open) appels `CreateBindStatusCallback`.

Pour plus d’informations sur les monikers asynchrones et liaison asynchrone, consultez le [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) interface et [comment une liaison asynchrone et travail de stockage](/windows/desktop/Stg/how-asynchronous-binding-and-storage-work). Pour une présentation d’agrégation, consultez [agrégation](/windows/desktop/com/aggregation). Tous les trois rubriques sont dans le SDK Windows.

##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo

Appelée à partir du client d’un moniker asynchrone pour indiquer le moniker asynchrone comment elles souhaitent se lier.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Valeur de retour

Récupère les paramètres pour `IBindStatusCallBack`. Pour obtenir une description de le `IBindStatusCallback` l’interface, consultez le kit SDK Windows.

### <a name="remarks"></a>Notes

L’implémentation par défaut définit la liaison asynchrone, pour utiliser un support de stockage (un flux) et à utiliser le modèle d’émission de données. Remplacez cette fonction si vous souhaitez modifier le comportement de la liaison.

L’une des raisons pour y parvenir consisterait à lier à l’aide du modèle d’extraction de données au lieu du modèle push de données. Dans un modèle d’extraction de données, le client gère l’opération de liaison et le moniker fournit des données au client lorsqu’il est lu. Dans un modèle d’émission de données, le moniker pilote l’opération de liaison asynchrone et en permanence informe le client chaque fois que les nouvelles données sont disponibles.

##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding

Appelez cette fonction pour récupérer un pointeur vers la liaison de transfert asynchrone.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le `IBinding` interface fournie lorsque le transfert asynchrone commence. Retourne NULL si pour une raison quelconque le transfert ne peut pas être effectuées de façon asynchrone.

### <a name="remarks"></a>Notes

Cela vous permet de contrôler les transferts de données processus via le `IBinding` de l’interface, par exemple, avec `IBinding::Abort`, `IBinding::Pause`, et `IBinding::Resume`.

Pour obtenir une description de le `IBinding` l’interface, consultez le kit SDK Windows.

##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc

Appelez cette fonction pour récupérer le format des données dans le flux de données.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la structure Windows [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) pour le flux de données actuellement ouverte. Retourne NULL si le moniker n’a pas été lié, si elle n’est pas asynchrone, ou si l’opération asynchrone n’a pas commencé.

##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority

Appelée à partir du client d’un moniker asynchrone que le processus de liaison commence à recevoir de la priorité donnée au thread pour l’opération de liaison.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Valeur de retour

La priorité à laquelle le transfert asynchrone a lieu. Un des indicateurs de priorité de thread standard : THREAD_PRIORITY_ABOVE_NORMAL THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL et THREAD_PRIORITY_TIME_CRITICAL. Consultez la fonction Windows [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) pour obtenir une description de ces valeurs.

### <a name="remarks"></a>Notes

`GetPriority` doit pas être appelée directement. THREAD_PRIORITY_NORMAL est retournée par l’implémentation par défaut.

##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable

Un moniker asynchrone appelle `OnDataAvailable` pour fournir des données au client dès que possible, au cours d’asynchrone lier des opérations.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Paramètres

*dwSize*<br/>
La quantité cumulée (en octets) de données disponibles depuis le début de la liaison. Peut être égal à zéro, indiquant que la quantité de données n’est pas pertinente pour l’opération, ou qu’aucune quantité spécifique est devenue disponible.

*bscfFlag*<br/>
Une valeur d’énumération BSCF. Peut être une ou plusieurs des valeurs suivantes :

- BSCF_FIRSTDATANOTIFICATION identifie le premier appel à `OnDataAvailable` pour une opération de liaison donné.

- BSCF_INTERMEDIATEDATANOTIFICATION identifie un appel intermédiaire à `OnDataAvailable` pour une opération de liaison.

- BSCF_LASTDATANOTIFICATION identifie le dernier appel à `OnDataAvailable` pour une opération de liaison.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Consultez l’exemple suivant pour un exemple d’implémentation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource

Appelé par le moniker lorsque les ressources sont insuffisantes.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle `GetBinding( )-> Abort( )`.

##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress

Appelé par le moniker à plusieurs reprises pour indiquer la progression actuelle de cette opération de liaison, généralement à des intervalles raisonnables pendant une longue opération.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Paramètres

*ulProgress*<br/>
Indique la progression actuelle de l’opération de liaison par rapport à la valeur maximale attendue indiquée dans *ulProgressMax*.

*ulProgressMax*<br/>
Indique la valeur maximale attendue de *ulProgress* pour la durée des appels à `OnProgress` pour cette opération.

*ulStatusCode*<br/>
Fournit des informations supplémentaires concernant la progression de l’opération de liaison. Les valeurs valides sont tirés du `BINDSTATUS` énumération. Consultez la section Notes pour les valeurs possibles.

*szStatusText*<br/>
Plus d’informations sur la progression actuelle, selon la valeur de *ulStatusCode*. Consultez la section Notes pour les valeurs possibles.

### <a name="remarks"></a>Notes

Les valeurs possibles pour *ulStatusCode* (et le *szStatusText* pour chaque valeur) sont :

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |L’opération de liaison recherche la ressource qui contient l’objet ou le stockage en cours de liaison. Le *szStatusText* fournit le nom complet de la ressource recherchée (par exemple, « www.Microsoft.com »).  |
|BINDSTATUS_CONNECTING  |L’opération de liaison se connecte à la ressource qui renferme l’objet ou le stockage en cours de liaison. Le *szStatusText* fournit le nom complet de la ressource qui est connecté à (par exemple, une adresse IP).  |
|BINDSTATUS_SENDINGREQUEST|L’opération de liaison demande l’objet ou le stockage en cours de liaison. Le *szStatusText* fournit le nom complet de l’objet (par exemple, un nom de fichier).|
|BINDSTATUS_REDIRECTING  |L’opération de liaison a été redirigée vers un autre emplacement de données. Le *szStatusText* fournit le nom complet du nouvel emplacement de données.  |
|BINDSTATUS_USINGCACHEDCOPY  |L’opération de liaison récupère l’objet demandé ou le stockage à partir d’une copie mise en cache. Le *szStatusText* a la valeur NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |L’opération de liaison a commencé à recevoir l’objet ou le stockage en cours de liaison. Le *szStatusText* fournit le nom complet de l’emplacement de données.|
|BINDSTATUS_DOWNLOADINGDATA  |L’opération de liaison continue à recevoir de l’objet ou le stockage en cours de liaison. Le *szStatusText* fournit le nom complet de l’emplacement de données.  |
|BINDSTATUS_ENDDOWNLOADDATA  |L’opération de liaison a fini de recevoir l’objet ou le stockage en cours de liaison. Le *szStatusText* fournit le nom complet de l’emplacement de données.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Une instance de l’objet en cours de liaison est sur le point d’être créé. Le *szStatusText* fournit le CLSID du nouvel objet au format de chaîne, permettant au client d’annuler l’opération de liaison, si vous le souhaitez.  |

##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding

Remplacez cette fonction dans vos classes dérivées pour effectuer des actions lors de la liaison démarre.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Notes

Cette fonction est rappelée par le moniker. L'implémentation par défaut n'exécute aucune opération.

##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding

Appelé par le moniker à la fin de l’opération de liaison.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Paramètres

*hresult*<br/>
HRESULT qui est l’erreur ou la valeur de l’avertissement.

*szErrort*<br/>
Une chaîne de caractères décrivant l’erreur.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour effectuer des actions lorsque le transfert est arrêté. Par défaut, la fonction libère `IBinding`.

Pour obtenir une description de le `IBinding` l’interface, consultez le kit SDK Windows.

##  <a name="open"></a>  CAsyncMonikerFile::Open

Appelez cette fonction membre pour ouvrir un fichier de façon asynchrone.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszURL*<br/>
Pointeur vers le fichier à ouvrir en mode asynchrone. Le fichier peut être n’importe quel URL ou le nom de fichier valide.

*pError*<br/>
Pointeur vers les exceptions de fichier. En cas d’erreur, il est fixé à la cause.

*pMoniker*<br/>
Un pointeur vers l’interface de moniker asynchrone `IMoniker`, un moniker précis qui est la combinaison du moniker du document, que vous pouvez récupérer avec `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`et un moniker créé à partir du nom de chemin d’accès. Le contrôle peut utiliser ce moniker à lier, mais ce n’est pas le moniker que le contrôle doit enregistrer.

*pBindHost*<br/>
Un pointeur vers le `IBindHost` interface permettant de créer le moniker à partir d’un chemin d’accès potentiellement relatif. Si l’hôte de liaison n’est pas valide ou ne fournit pas d’un moniker, l’appel par défaut est `Open(lpszFileName,pError)`. Pour obtenir une description de le `IBindHost` l’interface, consultez le kit SDK Windows.

*pServiceProvider*<br/>
Un pointeur vers le `IServiceProvider` interface. Si le fournisseur de services n’est pas valide ou ne parvient pas à fournir le service pour `IBindHost`, l’appel par défaut est `Open(lpszFileName,pError)`.

*pUnknown*<br/>
Un pointeur vers le `IUnknown` interface. Si `IServiceProvider` est trouvée, les requêtes de fonction pour `IBindHost`. Si le fournisseur de services n’est pas valide ou ne parvient pas à fournir le service pour `IBindHost`, l’appel par défaut est `Open(lpszFileName,pError)`.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le fichier est ouvert avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Cet appel lance le processus de liaison.

Vous pouvez utiliser une URL ou un nom de fichier pour le *lpszURL* paramètre. Exemple :

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- ou -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[CMonikerFile, classe](../../mfc/reference/cmonikerfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile, classe](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty, classe](../../mfc/reference/cdatapathproperty-class.md)
