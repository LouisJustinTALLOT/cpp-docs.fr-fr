---
title: Classe CAsyncMonikerFile
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
ms.openlocfilehash: 57ab463445f249b4e9393f19af103b7588962d5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376994"
---
# <a name="casyncmonikerfile-class"></a>Classe CAsyncMonikerFile

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
|[CAsyncMonikerFile::GetBinding](#getbinding)|Récupère un pointeur à la fixation de transfert asynchrone.|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Récupère le format des données dans le flux.|
|[CAsyncMonikerFile::Ouvert](#open)|Ouvre un fichier asynchronement.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Crée un objet COM `IBindStatusCallback`qui implémente .|
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Appelé par la bibliothèque du système OLE pour demander des informations sur le type de liaison à créer.|
|[CAsyncMonikerFile::GetPriority](#getpriority)|Appelé par la bibliothèque du système OLE pour obtenir la priorité de la liaison.|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Appelé à fournir des données dès qu’elles deviennent disponibles pour le client pendant les opérations de liaison asynchrone.|
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Appelé quand les ressources sont faibles.|
|[CAsyncMonikerFile::OnProgress](#onprogress)|Appelé pour indiquer des progrès sur le processus de téléchargement de données.|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Appelé lorsque la liaison démarre.|
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Appelé quand le transfert asynchrone est arrêté.|

## <a name="remarks"></a>Notes

Dérivé de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), qui à son tour `CAsyncMonikerFile` est dérivé de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), utilise l’interface [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pour accéder à n’importe quel flux de données asynchrone, y compris le chargement des fichiers asynchronement à partir d’une URL. Les fichiers peuvent être des propriétés de datapath des contrôles ActiveX.

Les surnoms asynchrones sont utilisés principalement dans les applications Internet et les contrôles ActiveX pour fournir une interface utilisateur réactive lors des transferts de fichiers. Un excellent exemple de ceci est l’utilisation de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) pour fournir des propriétés asynchrones pour les contrôles ActiveX. L’objet `CDataPathProperty` recevra à plusieurs reprises un rappel pour indiquer la disponibilité de nouvelles données au cours d’un long processus d’échange de propriété.

Pour plus d’informations sur la façon d’utiliser les surnoms asynchrones et les contrôles ActiveX dans les applications Internet, voir les articles suivants:

- [Les premiers pas d’Internet : des monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Les premières étapes d’Internet : contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile

Construit un objet `CAsyncMonikerFile`.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Notes

Il ne crée `IBindHost` pas l’interface. `IBindHost`n’est utilisé que si `Open` vous le fournissez dans la fonction membre.

Pour une description `IBindHost` de l’interface, voir le SDK Windows.

## <a name="casyncmonikerfileclose"></a><a name="close"></a>CAsyncMonikerFile::Close

Appelez cette fonction pour fermer et libérer toutes les ressources.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Peut être appelé sur les fichiers non ouverts ou déjà fermés.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback

Crée un objet COM `IBindStatusCallback`qui implémente .

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Paramètres

*pUnkControlling (en)*<br/>
Un pointeur à l’inconnu `IUnknown`de contrôle (l’extérieur ) ou NULL si l’agrégation n’est pas utilisée.

### <a name="return-value"></a>Valeur de retour

Si *pUnkControlling n’est* pas NULL, la `IUnknown` fonction renvoie `IBindStatusCallback`un pointeur à l’intérieur sur un nouvel objet COM support . Si `pUnkControlling` est NULL, la fonction `IUnknown` renvoie un pointeur à un sur un nouvel objet COM support `IBindStatusCallback`.

### <a name="remarks"></a>Notes

`CAsyncMonikerFile`nécessite un objet COM `IBindStatusCallback`qui implémente . MFC implémente un tel objet, et il est aggregatable. Vous pouvez `CreateBindStatusCallback` remplacer pour retourner votre propre objet COM. Votre objet COM peut agréger `CreateBindStatusCallback` la mise en œuvre de MFC en appelant avec le contrôle inconnu de votre objet COM. Les objets COM `CCmdTarget` implémenté à l’aide du support COM peuvent récupérer le contrôle inconnu à l’aide `CCmdTarget::GetControllingUnknown`de .

Alternativement, votre objet COM peut déléguer `CreateBindStatusCallback( NULL )`à la mise en œuvre de MFC en appelant .

[CAsyncMonikerFile::Appels](#open) `CreateBindStatusCallback`ouverts .

Pour plus d’informations sur les surnoms asynchrones et la liaison asynchrone, voir [l’interface IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) et [How Asynchrone Binding and Storage Work](/windows/win32/Stg/how-asynchronous-binding-and-storage-work). Pour une discussion sur l’agrégation, voir [Agrégation](/windows/win32/com/aggregation). Les trois sujets sont dans le Windows SDK.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a>CAsyncMonikerFile::GetBindInfo

Appelé par le client d’un surnom asynchrone pour dire au surnom asynchrone comment il veut lier.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Valeur de retour

Récupère les paramètres `IBindStatusCallBack`pour . Pour une description `IBindStatusCallback` de l’interface, voir le SDK Windows.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut définit la liaison comme étant asynchrone, pour utiliser un support de stockage (un flux), et pour utiliser le modèle de données-poussée. Remplacez cette fonction si vous voulez changer le comportement de la liaison.

Une des raisons pour cela serait de lier l’utilisation du modèle de data-pull au lieu du modèle de données-poussée. Dans un modèle de collecte de données, le client conduit le fonctionnement de liaison, et le surnom ne fournit des données au client que lorsqu’il est lu. Dans un modèle de transmission de données, le surnom conduit le fonctionnement de lier asynchrone et informe continuellement le client chaque fois que de nouvelles données sont disponibles.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a>CAsyncMonikerFile::GetBinding

Appelez cette fonction pour récupérer un pointeur à la liaison de transfert asynchrone.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `IBinding` à l’interface fournie lorsque le transfert asynchrone commence. Retourne NULL si, pour quelque raison que ce soit, le transfert ne peut pas être effectué de façon asynchrone.

### <a name="remarks"></a>Notes

Cela vous permet de contrôler le `IBinding` processus de transfert `IBinding::Abort` `IBinding::Pause`de `IBinding::Resume`données à travers l’interface, par exemple, avec , , et .

Pour une description `IBinding` de l’interface, voir le SDK Windows.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a>CAsyncMonikerFile::GetFormatEtc

Appelez cette fonction pour récupérer le format des données dans le flux.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la structure Windows [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) pour le flux actuellement ouvert. Retourne NULL si le surnom n’a pas été lié, s’il n’est pas asynchrone, ou si l’opération asynchrone n’a pas commencé.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a>CAsyncMonikerFile::GetPriority

Appelé par le client d’un surnom asynchrone que le processus de liaison commence à recevoir la priorité donnée au fil pour l’opération de liaison.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Valeur de retour

La priorité à laquelle le transfert asynchrone aura lieu. Un des drapeaux prioritaires de thread standard : THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL et THREAD_PRIORITY_TIME_CRITICAL. Consultez la fonction [Windows SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) pour une description de ces valeurs.

### <a name="remarks"></a>Notes

`GetPriority`ne doit pas être appelé directement. THREAD_PRIORITY_NORMAL est retournée par la implémentation par défaut.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a>CAsyncMonikerFile::OnDataAvailable

Un surnom asynchrone appelle `OnDataAvailable` à fournir des données au client dès qu’elles sont disponibles, pendant les opérations de liaison asynchrone.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Paramètres

*dwSize dwSize*<br/>
Le montant cumulatif (dans les octets) des données disponibles depuis le début de la liaison. Peut être nul, ce qui indique que la quantité de données n’est pas pertinente pour l’opération, ou qu’aucun montant spécifique n’est devenu disponible.

*bscfFlag*<br/>
Une valeur de recensement BSCF. Peut être une ou plusieurs des valeurs suivantes :

- BSCF_FIRSTDATANOTIFICATION identifie le premier appel `OnDataAvailable` à une opération de liaison donnée.

- BSCF_INTERMEDIATEDATANOTIFICATION identifie un appel intermédiaire `OnDataAvailable` pour une opération de liaison.

- BSCF_LASTDATANOTIFICATION identifie le dernier appel `OnDataAvailable` à une opération de liaison.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Voir l’exemple suivant pour une mise en œuvre d’échantillon.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a>CAsyncMonikerFile::OnLowResource

Appelé par le surnom lorsque les ressources sont faibles.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Notes

Les appels `GetBinding( )-> Abort( )`de mise en œuvre par défaut .

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a>CAsyncMonikerFile::OnProgress

Appelé par le surnom à plusieurs reprises pour indiquer les progrès actuels de cette opération de liaison, généralement à intervalles raisonnables au cours d’une longue opération.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Paramètres

*ulProgress*<br/>
Indique les progrès actuels de l’opération de liaison par rapport au maximum prévu indiqué dans *ulProgressMax*.

*ulProgressMax*<br/>
Indique la valeur maximale prévue de *ulProgress* pour la durée des appels à `OnProgress` cette opération.

*ulStatusCode ulStatusCode ulStatusCode ulStat*<br/>
Fournit des informations supplémentaires sur l’avancement de l’opération de liaison. Les valeurs valides `BINDSTATUS` sont tirées de l’énumération. Consultez Notes pour connaitre les valeurs possibles.

*szStatusText*<br/>
Informations sur les progrès actuels, en fonction de la valeur de *ulStatusCode*. Consultez Notes pour connaitre les valeurs possibles.

### <a name="remarks"></a>Notes

Les valeurs possibles pour *ulStatusCode* (et le *szStatusText* pour chaque valeur) sont les :

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |L’opération de liaison consiste à trouver la ressource qui contient l’objet ou le stockage lié à. Le *szStatusText* fournit le nom d’affichage de la ressource recherchée (par exemple, "www.microsoft.com").  |
|BINDSTATUS_CONNECTING  |L’opération de liaison se connecte à la ressource qui contient l’objet ou le stockage lié à. Le *szStatusText* fournit le nom d’affichage de la ressource connectée (par exemple, une adresse IP).  |
|BINDSTATUS_SENDINGREQUEST|L’opération de liaison demande l’objet ou le stockage lié à. Le *szStatusText* fournit le nom d’affichage de l’objet (par exemple, un nom de fichier).|
|BINDSTATUS_REDIRECTING  |L’opération de liaison a été redirigée vers un emplacement de données différent. Le *szStatusText* fournit le nom d’affichage du nouvel emplacement de données.  |
|BINDSTATUS_USINGCACHEDCOPY  |L’opération de liaison consiste à récupérer l’objet demandé ou le stockage à partir d’une copie mise en cache. Le *szStatusText* est NULL.  |
|BINDSTATUS_BEGINDOWNLOADDATA  |L’opération de liaison a commencé à recevoir l’objet ou le stockage lié à. Le *szStatusText* fournit le nom d’affichage de l’emplacement des données.|
|BINDSTATUS_DOWNLOADINGDATA  |L’opération de liaison continue de recevoir l’objet ou le stockage lié à. Le *szStatusText* fournit le nom d’affichage de l’emplacement des données.  |
|BINDSTATUS_ENDDOWNLOADDATA  |L’opération de liaison a fini de recevoir l’objet ou le stockage lié à. Le *szStatusText* fournit le nom d’affichage de l’emplacement des données.  |
|BINDSTATUS_CLASSIDAVAILABLE  |Une instance de l’objet lié à est sur le point d’être créé. Le *szStatusText* fournit le CLSID du nouvel objet en format de chaîne, ce qui permet au client d’annuler l’opération de liaison, si désiré.  |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a>CAsyncMonikerFile::OnStartBinding

Remplacez cette fonction dans vos classes dérivées pour effectuer des actions lorsque la liaison démarre.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Notes

Cette fonction est rappelée par le surnom. L'implémentation par défaut n'exécute aucune opération.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a>CAsyncMonikerFile::OnStopBinding

Appelé par le surnom à la fin de l’opération de liaison.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Paramètres

*Hresult*<br/>
Un HRESULT qui est la valeur d’erreur ou d’avertissement.

*szErrort*<br/>
Une chaîne de caractère décrivant l’erreur.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour effectuer des actions lorsque le transfert est arrêté. Par défaut, la `IBinding`fonction libère .

Pour une description `IBinding` de l’interface, voir le SDK Windows.

## <a name="casyncmonikerfileopen"></a><a name="open"></a>CAsyncMonikerFile::Ouvert

Appelez cette fonction de membre pour ouvrir un fichier asynchrone.

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
Un pointeur à déposer à ouvrir asynchronement. Le fichier peut être n’importe quelle URL ou nom de fichier valide.

*Perror*<br/>
Un pointeur aux exceptions de fichier. En cas d’erreur, il sera réglé sur la cause.

*pMoniker (en anglais)*<br/>
Un pointeur à l’interface `IMoniker`de surnom asynchrone , un surnom précis qui est la combinaison du `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`propre surnom du document, que vous pouvez récupérer avec , et un surnom créé à partir du nom de chemin. Le contrôle peut utiliser ce surnom pour lier, mais ce n’est pas le surnom que le contrôle devrait enregistrer.

*pBindHost (en)*<br/>
Un pointeur `IBindHost` à l’interface qui sera utilisé pour créer le surnom à partir d’un nom de chemin potentiellement relatif. Si l’hôte de liaison est invalide ou ne fournit `Open(lpszFileName,pError)`pas un surnom, l’appel par défaut à . Pour une description `IBindHost` de l’interface, voir le SDK Windows.

*pServiceProvider*<br/>
Pointeur vers l'interface `IServiceProvider`. Si le fournisseur de services est invalide ou ne fournit pas le service pour `IBindHost`, l’appel par défaut à `Open(lpszFileName,pError)`.

*pUnknown (en)*<br/>
Pointeur vers l'interface `IUnknown`. Si `IServiceProvider` elle est trouvée, `IBindHost`la fonction requête pour . Si le fournisseur de services est invalide ou ne fournit pas le service pour `IBindHost`, l’appel par défaut à `Open(lpszFileName,pError)`.

### <a name="return-value"></a>Valeur de retour

Nonzero si le fichier est ouvert avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cet appel initie le processus contraignant.

Vous pouvez utiliser une URL ou un nom de fichier pour le paramètre *lpszURL.* Par exemple :

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- ou -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CMonikerFile](../../mfc/reference/cmonikerfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CMonikerFile](../../mfc/reference/cmonikerfile-class.md)<br/>
[Classe CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
