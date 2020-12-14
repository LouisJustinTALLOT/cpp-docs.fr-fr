---
description: 'En savoir plus sur : classe CAsyncMonikerFile'
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
ms.openlocfilehash: 559ffd5ed3a8b7100d9901dc70fe4f5349c05f7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343527"
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
|[CAsyncMonikerFile :: CAsyncMonikerFile](#casyncmonikerfile)|Construit un objet `CAsyncMonikerFile`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAsyncMonikerFile :: Close](#close)|Ferme et libère toutes les ressources.|
|[CAsyncMonikerFile :: GetBinding](#getbinding)|Récupère un pointeur vers la liaison de transfert asynchrone.|
|[CAsyncMonikerFile :: GetFormatEtc](#getformatetc)|Récupère le format des données dans le flux.|
|[CAsyncMonikerFile :: Open](#open)|Ouvre un fichier de façon asynchrone.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAsyncMonikerFile :: CreateBindStatusCallback](#createbindstatuscallback)|Crée un objet COM qui implémente `IBindStatusCallback` .|
|[CAsyncMonikerFile :: GetBindInfo](#getbindinfo)|Appelé par la bibliothèque système OLE pour demander des informations sur le type de liaison à créer.|
|[CAsyncMonikerFile :: getPriority,](#getpriority)|Appelé par la bibliothèque système OLE pour connaître la priorité de la liaison.|
|[CAsyncMonikerFile :: OnDataAvailable](#ondataavailable)|Appelé pour fournir des données à mesure qu’elles deviennent disponibles pour le client lors des opérations de liaison asynchrones.|
|[CAsyncMonikerFile :: OnLowResource](#onlowresource)|Appelé lorsque les ressources sont insuffisantes.|
|[CAsyncMonikerFile :: OnProgress](#onprogress)|Appelée pour indiquer la progression du processus de téléchargement des données.|
|[CAsyncMonikerFile :: OnStartBinding](#onstartbinding)|Appelé lorsque la liaison démarre.|
|[CAsyncMonikerFile :: OnStopBinding](#onstopbinding)|Appelé lorsque le transfert asynchrone est arrêté.|

## <a name="remarks"></a>Notes

Dérivé de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), qui, à son tour, est dérivé de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` utilise l’interface [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) pour accéder à n’importe quel flux de données de façon asynchrone, y compris le chargement asynchrone de fichiers à partir d’une URL. Les fichiers peuvent être des propriétés chemin des contrôles ActiveX.

Les monikers asynchrones sont principalement utilisés dans les applications Internet et les contrôles ActiveX pour fournir une interface utilisateur réactive lors des transferts de fichiers. L’utilisation de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) pour fournir des propriétés asynchrones pour les contrôles ActiveX est un exemple premier. L' `CDataPathProperty` objet obtient à plusieurs reprises un rappel pour indiquer la disponibilité de nouvelles données au cours d’un processus d’échange de propriétés long.

Pour plus d’informations sur l’utilisation des monikers asynchrones et des contrôles ActiveX dans les applications Internet, consultez les articles suivants :

- [Premières étapes Internet : monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)

- [Premières étapes Internet : contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a> CAsyncMonikerFile :: CAsyncMonikerFile

Construit un objet `CAsyncMonikerFile`.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Notes

Elle ne crée pas l' `IBindHost` interface. `IBindHost` est utilisé uniquement si vous le fournissez dans la `Open` fonction membre.

Pour obtenir une description de l' `IBindHost` interface, consultez le SDK Windows.

## <a name="casyncmonikerfileclose"></a><a name="close"></a> CAsyncMonikerFile :: Close

Appelez cette fonction pour fermer et libérer toutes les ressources.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Peut être appelé sur des fichiers qui ne sont pas ouverts ou déjà fermés.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a> CAsyncMonikerFile :: CreateBindStatusCallback

Crée un objet COM qui implémente `IBindStatusCallback` .

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>Paramètres

*pUnkControlling*<br/>
Pointeur vers le contrôle Unknown (externe `IUnknown` ) ou null si l’agrégation n’est pas utilisée.

### <a name="return-value"></a>Valeur renvoyée

Si *pUnkControlling* n’a pas la valeur null, la fonction retourne un pointeur vers le interne `IUnknown` sur un nouvel objet com qui prend en charge `IBindStatusCallback` . Si `pUnkControlling` a la valeur null, la fonction retourne un pointeur vers un `IUnknown` sur un nouvel objet com qui prend en charge `IBindStatusCallback` .

### <a name="remarks"></a>Notes

`CAsyncMonikerFile` requiert un objet COM qui implémente `IBindStatusCallback` . MFC implémente un tel objet et peut être agrégé. Vous pouvez remplacer `CreateBindStatusCallback` pour retourner votre propre objet com. Votre objet COM peut agréger l’implémentation de MFC en appelant `CreateBindStatusCallback` avec le contrôle inconnu de votre objet com. Les objets COM implémentés à l’aide de la `CCmdTarget` prise en charge de com peuvent récupérer le contrôle inconnu à l’aide de `CCmdTarget::GetControllingUnknown` .

Votre objet COM peut également déléguer à l’implémentation de MFC en appelant `CreateBindStatusCallback( NULL )` .

Appels [CAsyncMonikerFile :: Open](#open) `CreateBindStatusCallback` .

Pour plus d’informations sur les monikers asynchrones et la liaison asynchrone, consultez l’interface [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) et fonctionnement de la [liaison asynchrone et du stockage](/windows/win32/Stg/how-asynchronous-binding-and-storage-work). Pour plus d’informations sur l’agrégation, consultez [agrégation](/windows/win32/com/aggregation). Les trois rubriques se trouvent dans la SDK Windows.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a> CAsyncMonikerFile :: GetBindInfo

Appelée à partir du client d’un moniker asynchrone pour indiquer au moniker asynchrone comment il souhaite effectuer une liaison.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>Valeur renvoyée

Récupère les paramètres pour `IBindStatusCallBack` . Pour obtenir une description de l' `IBindStatusCallback` interface, consultez le SDK Windows.

### <a name="remarks"></a>Notes

L’implémentation par défaut définit la liaison pour qu’elle soit asynchrone, pour utiliser un support de stockage (un flux) et pour utiliser le modèle d’envoi de données. Substituez cette fonction si vous souhaitez modifier le comportement de la liaison.

Cela peut être dû à une liaison à l’aide du modèle d’extraction de données au lieu du modèle de transmission de données. Dans un modèle d’extraction de données, le client pilote l’opération de liaison et le moniker fournit uniquement des données au client lorsqu’il est lu. Dans un modèle de transmission de données, le moniker pilote l’opération de liaison asynchrone et notifie en continu au client chaque fois que de nouvelles données sont disponibles.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a> CAsyncMonikerFile :: GetBinding

Appelez cette fonction pour récupérer un pointeur vers la liaison de transfert asynchrone.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l' `IBinding` interface fournie au début du transfert asynchrone. Retourne la valeur NULL si, pour une raison quelconque, le transfert ne peut pas être effectué de manière asynchrone.

### <a name="remarks"></a>Notes

Cela vous permet de contrôler le processus de transfert de données via l' `IBinding` interface, par exemple, avec `IBinding::Abort` , `IBinding::Pause` et `IBinding::Resume` .

Pour obtenir une description de l' `IBinding` interface, consultez le SDK Windows.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a> CAsyncMonikerFile :: GetFormatEtc

Appelez cette fonction pour récupérer le format des données dans le flux.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la structure Windows [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) pour le flux actuellement ouvert. Retourne la valeur NULL si le moniker n’a pas été lié, s’il n’est pas asynchrone, ou si l’opération asynchrone n’a pas commencé.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a> CAsyncMonikerFile :: getPriority,

Appelée à partir du client d’un moniker asynchrone à mesure que le processus de liaison commence à recevoir la priorité donnée au thread pour l’opération de liaison.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>Valeur renvoyée

Priorité à laquelle le transfert asynchrone aura lieu. L’un des indicateurs de priorité de thread standard : THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL et THREAD_PRIORITY_TIME_CRITICAL. Pour obtenir une description de ces valeurs, consultez la fonction Windows [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) .

### <a name="remarks"></a>Notes

`GetPriority` ne doit pas être appelé directement. THREAD_PRIORITY_NORMAL est retourné par l’implémentation par défaut.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a> CAsyncMonikerFile :: OnDataAvailable

Un moniker asynchrone appelle `OnDataAvailable` pour fournir des données au client dès qu’il est disponible, pendant les opérations de liaison asynchrones.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>Paramètres

*dwSize nul*<br/>
Quantité cumulée (en octets) des données disponibles depuis le début de la liaison. Peut être égal à zéro, ce qui indique que la quantité de données n’est pas pertinente pour l’opération, ou qu’aucune quantité spécifique n’est devenue disponible.

*bscfFlag*<br/>
Valeur d’énumération BSCF. Il peut s’agir d’une ou plusieurs des valeurs suivantes :

- BSCF_FIRSTDATANOTIFICATION identifie le premier appel à `OnDataAvailable` pour une opération de liaison donnée.

- BSCF_INTERMEDIATEDATANOTIFICATION identifie un appel intermédiaire à `OnDataAvailable` pour une opération de liaison.

- BSCF_LASTDATANOTIFICATION identifie le dernier appel à `OnDataAvailable` pour une opération de liaison.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Pour obtenir un exemple d’implémentation, consultez l’exemple suivant.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a> CAsyncMonikerFile :: OnLowResource

Appelé par le moniker lorsque les ressources sont faibles.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle `GetBinding( )-> Abort( )` .

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a> CAsyncMonikerFile :: OnProgress

Appelée par le moniker à plusieurs reprises pour indiquer la progression actuelle de cette opération de liaison, généralement à des intervalles raisonnables au cours d’une opération de longue durée.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>Paramètres

*ulProgress*<br/>
Indique la progression actuelle de l’opération de liaison par rapport au maximum attendu indiqué dans *ulProgressMax*.

*ulProgressMax*<br/>
Indique la valeur maximale attendue de *ulProgress* pour la durée des appels à `OnProgress` pour cette opération.

*ulStatusCode*<br/>
Fournit des informations supplémentaires concernant la progression de l’opération de liaison. Les valeurs valides sont extraites de l' `BINDSTATUS` énumération. Consultez Notes pour connaitre les valeurs possibles.

*szStatusText*<br/>
Informations sur la progression actuelle, en fonction de la valeur de *ulStatusCode*. Consultez Notes pour connaitre les valeurs possibles.

### <a name="remarks"></a>Notes

Les valeurs possibles pour *ulStatusCode* (et *szStatusText* pour chaque valeur) sont les suivantes :

| Valeur | Description |
|--|--|
| BINDSTATUS_FINDINGRESOURCE | L’opération de liaison recherche la ressource qui contient l’objet ou le stockage en cours de liaison. *SzStatusText* fournit le nom complet de la ressource recherchée (par exemple, « www.Microsoft.com »). |
| BINDSTATUS_CONNECTING | L’opération de liaison se connecte à la ressource qui contient l’objet ou le stockage en cours de liaison. *SzStatusText* fournit le nom complet de la ressource à laquelle il est connecté (par exemple, une adresse IP). |
| BINDSTATUS_SENDINGREQUEST | L’opération de liaison demande l’objet ou le stockage en cours de liaison. *SzStatusText* fournit le nom complet de l’objet (par exemple, un nom de fichier). |
| BINDSTATUS_REDIRECTING | L’opération de liaison a été redirigée vers un emplacement de données différent. *SzStatusText* fournit le nom complet du nouvel emplacement des données. |
| BINDSTATUS_USINGCACHEDCOPY | L’opération de liaison récupère l’objet ou le stockage demandé à partir d’une copie mise en cache. *SzStatusText* a la valeur null. |
| BINDSTATUS_BEGINDOWNLOADDATA | L’opération de liaison a commencé à recevoir l’objet ou le stockage en cours de liaison. *SzStatusText* fournit le nom complet de l’emplacement des données. |
| BINDSTATUS_DOWNLOADINGDATA | L’opération de liaison continue à recevoir l’objet ou le stockage en cours de liaison avec. *SzStatusText* fournit le nom complet de l’emplacement des données. |
| BINDSTATUS_ENDDOWNLOADDATA | L’opération de liaison a terminé de recevoir l’objet ou le stockage en cours de liaison. *SzStatusText* fournit le nom complet de l’emplacement des données. |
| BINDSTATUS_CLASSIDAVAILABLE | Une instance de l’objet qui est lié à est en cours de création. Le *szStatusText* fournit le CLSID du nouvel objet au format chaîne, ce qui permet au client d’annuler l’opération de liaison, si nécessaire. |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a> CAsyncMonikerFile :: OnStartBinding

Substituez cette fonction dans vos classes dérivées pour exécuter des actions au démarrage de la liaison.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Notes

Cette fonction est rappelée par le moniker. L'implémentation par défaut n'exécute aucune opération.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a> CAsyncMonikerFile :: OnStopBinding

Appelée par le moniker à la fin de l’opération de liaison.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>Paramètres

*signé*<br/>
HRESULT qui est la valeur de l’erreur ou de l’avertissement.

*szErrort*<br/>
Chaîne de caractères décrivant l’erreur.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour exécuter des actions lorsque le transfert est arrêté. Par défaut, la fonction libère `IBinding` .

Pour obtenir une description de l' `IBinding` interface, consultez le SDK Windows.

## <a name="casyncmonikerfileopen"></a><a name="open"></a> CAsyncMonikerFile :: Open

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
Pointeur vers le fichier à ouvrir de façon asynchrone. Il peut s’agir d’une URL ou d’un nom de fichier valide.

*pError*<br/>
Pointeur vers les exceptions de fichier. En cas d’erreur, elle est définie en conséquence.

*pMoniker*<br/>
Pointeur vers l’interface du moniker asynchrone `IMoniker` , un moniker précis qui est la combinaison du propre moniker du document, que vous pouvez récupérer avec `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)` et un moniker créé à partir du nom du chemin d’accès. Le contrôle peut utiliser ce moniker pour la liaison, mais ce n’est pas le moniker que le contrôle doit enregistrer.

*pBindHost*<br/>
Pointeur vers l' `IBindHost` interface qui sera utilisée pour créer le moniker à partir d’un chemin d’accès potentiellement relatif. Si l’hôte de liaison n’est pas valide ou ne fournit pas de moniker, l’appel de prend par défaut la valeur `Open(lpszFileName,pError)` . Pour obtenir une description de l' `IBindHost` interface, consultez le SDK Windows.

*pServiceProvider*<br/>
Pointeur vers l'interface `IServiceProvider`. Si le fournisseur de services n’est pas valide ou ne parvient pas à fournir le service pour `IBindHost` , l’appel de prend par défaut la valeur `Open(lpszFileName,pError)` .

*pUnknown*<br/>
Pointeur vers l'interface `IUnknown`. Si `IServiceProvider` est trouvé, la fonction interroge `IBindHost` . Si le fournisseur de services n’est pas valide ou ne parvient pas à fournir le service pour `IBindHost` , l’appel de prend par défaut la valeur `Open(lpszFileName,pError)` .

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le fichier est ouvert avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Cet appel initie le processus de liaison.

Vous pouvez utiliser une URL ou un nom de fichier pour le paramètre *lpszURL* . Par exemple :

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- ou -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[CMonikerFile, classe](../../mfc/reference/cmonikerfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile, classe](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty, classe](../../mfc/reference/cdatapathproperty-class.md)
