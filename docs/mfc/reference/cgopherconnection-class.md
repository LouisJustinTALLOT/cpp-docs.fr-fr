---
title: CGopherConnection, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
dev_langs:
- C++
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f00a81aa7997591d152a665e14869f22bd14321
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377960"
---
# <a name="cgopherconnection-class"></a>CGopherConnection, classe

Gère votre connexion à un serveur Internet Gopher.

> [!NOTE]
>  Les classes `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` et leurs membres ont été déconseillées, car ils ne fonctionnent pas sur la plate-forme Windows XP, mais ils continueront à fonctionner sur des plateformes antérieures.

## <a name="syntax"></a>Syntaxe

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Construit un objet `CGopherConnection`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|Crée un [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet à rechercher des fichiers sur un serveur gopher.|
|[CGopherConnection::GetAttribute](#getattribute)|Récupère les informations d’attribut sur l’objet gopher.|
|[CGopherConnection::OpenFile](#openfile)|Ouvre un fichier gopher.|

## <a name="remarks"></a>Notes

Le service gopher est un des trois services Internet reconnus par les classes WinInet MFC.

La classe `CGopherConnection` contient un constructeur et trois fonctions membres supplémentaires qui gèrent le service gopher : [OpenFile](#openfile), [CreateLocator](#createlocator), et [GetAttribute](#getattribute).

Pour communiquer avec un serveur Internet gopher, vous devez d’abord créer une instance de [CInternetSession](../../mfc/reference/cinternetsession-class.md), puis appelez [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), ce qui crée le `CGopherConnection` l’objet et retourne un pointeur vers elle. Vous ne créez jamais un `CGopherConnection` directement l’objet.

Pour en savoir plus sur la façon `CGopherConnection` fonctionne avec les autres classes Internet de MFC, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur les deux autres prises en charge des services Internet, HTTP et FTP consultez les classes [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxinet.h

##  <a name="cgopherconnection"></a>  CGopherConnection::CGopherConnection

Cette fonction membre est appelée pour construire un `CGopherConnection` objet.

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);


CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Paramètres

*pSession*<br/>
Un pointeur vers le connexes [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet.

*hConnected*<br/>
Handle Windows de la session Internet actuel.

*pstrServer*<br/>
Un pointeur vers une chaîne contenant le nom du serveur FTP.

*dwContext*<br/>
L’identificateur de contexte pour l’opération. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). La valeur par défaut est défini sur 1 ; Toutefois, vous pouvez affecter explicitement un ID de contexte spécifique pour l’opération. L’objet et n’importe quel travail qu’elle effectue sera associés à cet ID de contexte.

*pstrUserName*<br/>
Pointeur vers une chaîne se terminant par null qui spécifie le nom de l’utilisateur pour vous connecter. Si NULL, la valeur par défaut est anonyme.

*pstrPassword*<br/>
Un pointeur vers une chaîne se terminant par null qui spécifie le mot de passe à utiliser pour vous connecter. Si les deux *pstrPassword* et *pstrUserName* ont la valeur NULL, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* est NULL (ou une chaîne vide), mais *pstrUserName* n’est pas NULL, un mot de passe vide est utilisée. Le tableau suivant décrit le comportement pour les quatre paramètres possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou « »|NULL ou « »|« anonyme »|Nom de messagerie de l’utilisateur|
|Chaîne non NULL|NULL ou « »|*pstrUserName*|" "|
|Chaîne Non-NULL NULL|ERREUR|ERREUR||
|Chaîne non NULL|Chaîne non NULL|*pstrUserName*|*pstrPassword*|

*%nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

### <a name="remarks"></a>Notes

Vous ne créez jamais un `CGopherConnection` directement. Au lieu de cela, appelez [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), ce qui crée un `CGopherConnection` de l’objet et retourne un pointeur vers elle.

##  <a name="createlocator"></a>  CGopherConnection::CreateLocator

Appelez cette fonction membre pour créer un localisateur gopher pour trouver ou identifier un fichier sur un serveur gopher.

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);


static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Paramètres

*pstrDisplayString*<br/>
Un pointeur vers une chaîne contenant le nom du document de gopher ou du répertoire à récupérer. Si le *pstrDisplayString* paramètre est NULL, le répertoire par défaut pour le serveur gopher est retourné.

*pstrSelectorString*<br/>
Pointeur vers la chaîne de sélecteur à envoyer au serveur gopher afin de récupérer un élément. *pstrSelectorString* peut être NULL.

*dwGopherType*<br/>
Ce paramètre spécifie si *pstrSelectorString* fait référence à un répertoire ou d’un document, et si la demande gopher ou gopher +. Voir les attributs de la structure [GOPHER_FIND_DATA](/windows/desktop/api/wininet/ns-wininet-gopher_find_dataa) dans le SDK Windows.

*pstrLocator*<br/>
Pointeur vers une chaîne qui identifie le fichier à ouvrir. En règle générale, cette chaîne est retournée à partir d’un appel à [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Un pointeur vers une chaîne contenant le nom du serveur gopher.

*%nPort*<br/>
Le numéro qui identifie le port Internet pour cette connexion.

### <a name="return-value"></a>Valeur de retour

Un [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet.

### <a name="remarks"></a>Notes

La version statique de la fonction membre vous oblige à spécifier un serveur, tandis que la version non statiques utilise le nom du serveur à partir de l’objet de connexion.

Pour récupérer des informations à partir d’un serveur gopher, une application doit d’abord obtenir un localisateur gopher. L’application doit ensuite traiter le localisateur sous forme d’un jeton opaque (autrement dit, l’application peut utiliser le localisateur mais pas directement manipuler ou comparer). Normalement, l’application utilise le localisateur pour les appels à la [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) fonction membre pour récupérer une information spécifique.

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

Appelez cette fonction membre pour récupérer les informations d’attribut spécifique sur un élément à partir du serveur gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Paramètres

*refLocator*<br/>
Une référence à un [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet.

*strRequestedAttributes*<br/>
Une chaîne délimitée spécifiant les noms des attributs demandés.

*strResult*<br/>
Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui reçoit le type de localisateur.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

##  <a name="openfile"></a>  CGopherConnection::OpenFile

Appelez cette fonction membre pour ouvrir un fichier sur un serveur gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*refLocator*<br/>
Une référence à un [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet.

*dwFlags*<br/>
N’importe quelle combinaison d’indicateurs de INTERNET_FLAG_. Consultez [CInternetSession::OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) pour plus d’informations sur INTERNET_FLAG_\* indicateurs.

*pstrView*<br/>
Un pointeur vers une chaîne d’affichage des fichiers. Si plusieurs vues du fichier existent au niveau du serveur, ce paramètre spécifie la vue du fichier à ouvrir. Si *pstrView* est NULL, l’affichage des fichiers par défaut est utilisé.

*dwContext*<br/>
L’ID de contexte pour le fichier ouvert. Consultez **remarques** pour plus d’informations sur *dwContext*.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le [CGopherFile](../../mfc/reference/cgopherfile-class.md) objet à ouvrir.

### <a name="remarks"></a>Notes

Remplacer le *dwContext* par défaut pour définir l’identificateur de contexte pour une valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de la `CGopherConnection` objet créé par son [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet. La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.

## <a name="see-also"></a>Voir aussi

[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection, classe](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator, classe](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile, classe](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession, classe](../../mfc/reference/cinternetsession-class.md)
