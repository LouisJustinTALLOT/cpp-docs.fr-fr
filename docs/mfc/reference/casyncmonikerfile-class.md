---
title: Classe CAsyncMonikerFile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16d4b5169ffa93892b8a3076cbfa24227ccf569f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356010"
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
|[CAsyncMonikerFile::GetBinding](#getbinding)|Récupère un pointeur vers le transfert asynchrone la liaison.|  
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|Récupère le format des données dans le flux de données.|  
|[CAsyncMonikerFile::Open](#open)|Ouvre un fichier de façon asynchrone.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|Crée un objet COM qui implémente `IBindStatusCallback`.|  
|[CAsyncMonikerFile::GetBindInfo](#getbindinfo)|Appelée par la bibliothèque du système OLE pour demander des informations sur le type de liaison à créer.|  
|[CAsyncMonikerFile::GetPriority](#getpriority)|Appelée par la bibliothèque du système OLE pour obtenir la priorité de la liaison.|  
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|Appelé pour fournir des données dès qu’il sera disponible pour le client lors des opérations de liaison asynchrone.|  
|[CAsyncMonikerFile::OnLowResource](#onlowresource)|Appelé lorsque les ressources sont insuffisantes.|  
|[CAsyncMonikerFile::OnProgress](#onprogress)|Appelé pour indiquer la progression sur les données du processus de téléchargement.|  
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|Appelé lorsque la liaison démarre.|  
|[CAsyncMonikerFile::OnStopBinding](#onstopbinding)|Appelé lorsque le transfert asynchrone est arrêté.|  
  
## <a name="remarks"></a>Notes  
 Dérivé de [CMonikerFile](../../mfc/reference/cmonikerfile-class.md), qui à son tour est dérivée de [COleStreamFile](../../mfc/reference/colestreamfile-class.md), `CAsyncMonikerFile` utilise le [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705) interface pour accéder à n’importe quel flux de données en mode asynchrone, y compris le chargement des fichiers à partir d’une URL de façon asynchrone. Les fichiers peuvent être le chemin de données des propriétés des contrôles ActiveX.  
  
 Les monikers asynchrones sont utilisés principalement dans les applications compatibles avec Internet et les contrôles ActiveX pour fournir une interface utilisateur réactive pendant les transferts de fichiers. Un exemple de cela est l’utilisation de [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) pour fournir des propriétés asynchrones aux contrôles ActiveX. Le `CDataPathProperty` objet obtenez à plusieurs reprises un rappel pour indiquer la disponibilité de nouvelles données lors d’un processus d’échange propriété longue.  
  
 Pour plus d’informations sur l’utilisation de monikers asynchrones et les contrôles ActiveX dans les applications Internet, consultez les articles suivants :  
  
- [Internet premières étapes : Les Monikers asynchrones](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
- [Internet premières étapes : Les contrôles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
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
 Il ne crée pas le `IBindHost` interface. `IBindHost` est utilisé uniquement si vous fournissez dans le **ouvrir** fonction membre.  
  
 Pour obtenir une description de le `IBindHost` l’interface, consultez le Kit de développement logiciel Windows.  
  
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
 `pUnkControlling`  
 Un pointeur vers l’inconnu de contrôle (externe **IUnknown**) ou **NULL** si l’agrégation n’est pas utilisée.  
  
### <a name="return-value"></a>Valeur de retour  
 Si `pUnkControlling` n’est pas **NULL**, la fonction retourne un pointeur à l’exception interne **IUnknown** sur un nouvel objet COM prenant en charge `IBindStatusCallback`. Si `pUnkControlling` est **NULL**, la fonction retourne un pointeur vers un **IUnknown** sur un nouvel objet COM prenant en charge `IBindStatusCallback`.  
  
### <a name="remarks"></a>Notes  
 `CAsyncMonikerFile` nécessite un objet COM qui implémente `IBindStatusCallback`. MFC implémente ce type d’objet, et il ne peut être agrégé. Vous pouvez substituer `CreateBindStatusCallback` pour retourner votre propre objet COM. Votre objet COM peut agréger l’implémentation MFC en appelant `CreateBindStatusCallback` avec inconnu de contrôle de votre objet COM. Les objets COM implémentés à l’aide de la `CCmdTarget` prise en charge COM peut récupérer le contrôle inconnu à l’aide de **CCmdTarget::GetControllingUnknown**.  
  
 Vous pouvez également votre objet COM peut déléguer à l’implémentation MFC en appelant **CreateBindStatusCallback (NULL)**.  
  
 [CAsyncMonikerFile::Open](#open) appelle `CreateBindStatusCallback`.  
  
 Pour plus d’informations sur les monikers asynchrones et liaison asynchrone, consultez le [IBindStatusCallback](http://msdn.microsoft.com/library/ie/ms775060) interface et [comment une liaison asynchrone et le travail de stockage](http://msdn.microsoft.com/library/windows/desktop/aa379152). Pour une présentation d’agrégation, consultez [agrégation](http://msdn.microsoft.com/library/windows/desktop/ms686558). Tous les trois rubriques se trouvent dans le SDK de Windows.  
  
##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo  
 Appelée à partir du client d’un moniker asynchrone pour indiquer le moniker asynchrone comment il souhaite lier.  
  
```  
virtual DWORD GetBindInfo() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Récupère les paramètres pour **IBindStatusCallBack**. Pour obtenir une description de le `IBindStatusCallback` l’interface, consultez le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut définit la liaison doit être asynchrone, utilisez un support de stockage (un flux de données) et à utiliser le modèle d’émission de données. Remplacez cette fonction si vous souhaitez modifier le comportement de la liaison.  
  
 L’une des raisons pour cela serait à la liaison avec le modèle d’extraction de données au lieu du modèle de push de données. Dans un modèle d’extraction de données, le client lecteurs de l’opération de liaison et le moniker fournit des données au client lorsqu’il est lu. Dans un modèle de push de données, le moniker de l’opération de liaison asynchrone les lecteurs et signale en permanence au client chaque fois que les nouvelles données sont disponibles.  
  
##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding  
 Appelez cette fonction pour récupérer un pointeur vers le transfert asynchrone la liaison.  
  
```  
IBinding* GetBinding() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `IBinding` interface fournie au commencement de transfert asynchrone. Retourne **NULL** si pour une raison quelconque le transfert ne peut pas être exécutée de façon asynchrone.  
  
### <a name="remarks"></a>Notes  
 Cela permet de contrôler le transfert de données processus via le `IBinding` de l’interface, par exemple, avec **IBinding::Abort**, **IBinding::Pause**, et **IBinding::Resume**.  
  
 Pour obtenir une description de le `IBinding` l’interface, consultez le Kit de développement logiciel Windows.  
  
##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc  
 Appelez cette fonction pour récupérer le format des données dans le flux de données.  
  
```  
FORMATETC* GetFormatEtc() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la structure Windows [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) pour le flux ouvert. Retourne **NULL** si le moniker n’a pas été lié, si elle n’est pas asynchrone, ou si l’opération asynchrone n’a pas commencé.  
  
##  <a name="getpriority"></a>  CAsyncMonikerFile::GetPriority  
 Appelée à partir du client d’un moniker asynchrone au démarrage du processus de liaison recevoir la priorité donnée au thread pour l’opération de liaison.  
  
```  
virtual LONG GetPriority() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La priorité à laquelle le transfert asynchrone a lieu. Un des indicateurs de priorité de thread standard : **THREAD_PRIORITY_ABOVE_NORMAL**, **THREAD_PRIORITY_BELOW_NORMAL**, **THREAD_PRIORITY_HIGHEST**,  **THREAD_PRIORITY_IDLE**, **niveau de priorité**, **THREAD_PRIORITY_NORMAL**, et **THREAD_PRIORITY_TIME_CRITICAL**. Consultez la fonction Windows [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) pour obtenir une description de ces valeurs.  
  
### <a name="remarks"></a>Notes  
 `GetPriority` doit pas être appelée directement. **THREAD_PRIORITY_NORMAL** est retourné par l’implémentation par défaut.  
  
##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable  
 Un moniker asynchrone appelle `OnDataAvailable` pour fournir des données au client qu’il est disponible, lier des opérations pendant asynchrone.  
  
```  
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwSize`  
 La quantité cumulée (en octets) de données disponibles depuis le début de la liaison. Peut être égal à zéro, indiquant que la quantité de données ne s’applique pas à l’opération, ou qu’aucun montant spécifique est désormais disponible.  
  
 *bscfFlag*  
 A **BSCF** valeur d’énumération. Peut être une ou plusieurs des valeurs suivantes :  
  
- **BSCF_FIRSTDATANOTIFICATION** identifie le premier appel à `OnDataAvailable` pour une opération de liaison de donnée.  
  
- **BSCF_INTERMEDIATEDATANOTIFICATION** identifie un appel intermédiaire à `OnDataAvailable` pour une opération de liaison.  
  
- **BSCF_LASTDATANOTIFICATION** identifie le dernier appel à `OnDataAvailable` pour une opération de liaison.  
  
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
 `ulProgress`  
 Indique la progression actuelle de l’opération de liaison par rapport à la valeur maximale attendue indiquée dans `ulProgressMax`.  
  
 `ulProgressMax`  
 Indique la valeur maximale attendue de `ulProgress` pour la durée des appels à `OnProgress` pour cette opération.  
  
 `ulStatusCode`  
 Fournit des informations supplémentaires concernant la progression de l’opération de liaison. Les valeurs valides sont effectuées à partir de la `BINDSTATUS` énumération. Consultez la section Notes pour les valeurs possibles.  
  
 `szStatusText`  
 Plus d’informations sur l’état d’avancement, selon la valeur de `ulStatusCode`. Consultez la section Notes pour les valeurs possibles.  
  
### <a name="remarks"></a>Notes  
 Les valeurs possibles pour `ulStatusCode` (et `szStatusText` pour chaque valeur) sont :  
  
 **BINDSTATUS_FINDINGRESOURCE**  
 L’opération de liaison est de trouver la ressource qui contient l’objet ou le stockage liée. Le `szStatusText` fournit le nom d’affichage de la ressource recherchée pour (par exemple, « www.microsoft.com »).  
  
 **BINDSTATUS_CONNECTING**  
 L’opération de liaison se connecte à la ressource qui contient l’objet ou le stockage liée. Le `szStatusText` fournit le nom d’affichage de la ressource qui est connecté à (par exemple, une adresse IP).  
  
 **BINDSTATUS_SENDINGREQUEST**  
 Demande l’objet ou le stockage liée à l’opération de liaison. Le `szStatusText` fournit le nom complet de l’objet (par exemple, un nom de fichier).  
  
 **BINDSTATUS_REDIRECTING**  
 L’opération de liaison a été redirigée vers un emplacement de données différents. Le `szStatusText` fournit le nom complet du nouvel emplacement de données.  
  
 **BINDSTATUS_USINGCACHEDCOPY**  
 L’opération de liaison est la récupération de l’objet ou le stockage à partir d’une copie mise en cache. Le `szStatusText` est **NULL**.  
  
 **BINDSTATUS_BEGINDOWNLOADDATA**  
 L’opération de liaison a commencé à recevoir de l’objet ou le stockage liée. Le `szStatusText` fournit le nom complet de l’emplacement des données.  
  
 **BINDSTATUS_DOWNLOADINGDATA**  
 L’opération de liaison continue de recevoir l’objet ou le stockage liée à. Le `szStatusText` fournit le nom complet de l’emplacement des données.  
  
 **BINDSTATUS_ENDDOWNLOADDATA**  
 L’opération de liaison a fini de recevoir l’objet ou le stockage liée. Le `szStatusText` fournit le nom complet de l’emplacement des données.  
  
 **BINDSTATUS_CLASSIDAVAILABLE**  
 Une instance de l’objet lié aux est sur le point d’être créé. Le `szStatusText` fournit le CLSID du nouvel objet au format de chaîne, permettant au client d’annuler l’opération de liaison, si vous le souhaitez.  
  
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
 `hresult`  
 Un `HRESULT` qui est l’erreur ou la valeur de l’avertissement.  
  
 *szErrort*  
 Une chaîne de caractères décrivant l’erreur.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour effectuer des actions lorsque le transfert est arrêté. Par défaut, la fonction libère `IBinding`.  
  
 Pour obtenir une description de le `IBinding` l’interface, consultez le Kit de développement logiciel Windows.  
  
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
 `lpszURL`  
 Pointeur vers le fichier à ouvrir en mode asynchrone. Le fichier peut être n’importe quel nom de fichier ou une URL valide.  
  
 `pError`  
 Pointeur vers les exceptions de fichier. En cas d’erreur, elle est définie à la cause.  
  
 `pMoniker`  
 Un pointeur vers l’interface de monikers asynchrones `IMoniker`, un moniker précis qui est la combinaison du moniker du document, que vous pouvez extraire avec **IOleClientSite::GetMoniker (** *OLEWHICHMK_ CONTENEUR* **)** et un moniker créé à partir du nom de chemin d’accès. Le contrôle peut utiliser ce moniker à lier, mais ce n’est pas le moniker qu'est conseillé d’enregistrer le contrôle.  
  
 *pBindHost*  
 Un pointeur vers le `IBindHost` interface permettant de créer le moniker à partir d’un chemin d’accès relatif potentiellement. Si l’hôte de la liaison n’est pas valide ou ne fournit pas d’un moniker, l’appel par défaut **ouvrir (** `lpszFileName` **,**`pError`**)**. Pour obtenir une description de le `IBindHost` l’interface, consultez le Kit de développement logiciel Windows.  
  
 `pServiceProvider`  
 Un pointeur vers le `IServiceProvider` interface. Si le fournisseur de services n’est pas valide ou ne parvient pas à fournir le service pour `IBindHost`, l’appel par défaut est **ouvrir (** `lpszFileName` **,**`pError`**)**.  
  
 *pUnknown*  
 Un pointeur vers le **IUnknown** interface. Si `IServiceProvider` est trouvée, la fonction interroge pour `IBindHost`. Si le fournisseur de services n’est pas valide ou ne parvient pas à fournir le service pour `IBindHost`, l’appel par défaut est **ouvrir (** `lpszFileName` **,**`pError`**)**.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le fichier est ouvert avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cet appel lance le processus de liaison.  
  
 Vous pouvez utiliser une URL ou un nom de fichier pour le `lpszURL` paramètre. Par exemple :  
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]  
  
 - ou  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CMonikerFile](../../mfc/reference/cmonikerfile-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de CMonikerFile](../../mfc/reference/cmonikerfile-class.md)   
 [CDataPathProperty, classe](../../mfc/reference/cdatapathproperty-class.md)
