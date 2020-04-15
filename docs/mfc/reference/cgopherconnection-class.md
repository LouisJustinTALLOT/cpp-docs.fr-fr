---
title: CGopherConnection, classe
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: eade1a82b674d5ad2e91146559139445ef017180
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373713"
---
# <a name="cgopherconnection-class"></a>CGopherConnection, classe

Gère votre connexion à un serveur Internet Gopher.

> [!NOTE]
> Les `CGopherConnection`classes `CGopherFile` `CGopherFileFind`, `CGopherLocator` , et leurs membres ont été dépréciés parce qu’ils ne travaillent pas sur la plate-forme Windows XP, mais ils continueront à travailler sur des plates-formes antérieures.

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
|[CGopherConnection::CreateLocator](#createlocator)|Crée un objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) pour trouver des fichiers sur un serveur gopher.|
|[CGopherConnection::GetAttribute](#getattribute)|Récupère les informations d’attribut sur l’objet gopher.|
|[CGopherConnection::OpenFile](#openfile)|Ouvre un fichier de gaufre.|

## <a name="remarks"></a>Notes

Le service gopher est l’un des trois services Internet reconnus par les classes MFC WinInet.

La `CGopherConnection` classe contient un constructeur et trois fonctions membres supplémentaires qui gèrent le service de gopher: [OpenFile](#openfile), [CreateLocator](#createlocator), et [GetAttribute](#getattribute).

Pour communiquer avec un serveur Internet gopher, vous devez d’abord créer un exemple de [CInternetSession](../../mfc/reference/cinternetsession-class.md), puis appeler `CGopherConnection` [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), qui crée l’objet et retourne un pointeur à elle. Vous ne `CGopherConnection` créez jamais un objet directement.

Pour en savoir `CGopherConnection` plus sur la façon dont fonctionne avec les autres classes Internet MFC, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur l’utilisation des deux autres services Internet pris en charge, FTP et HTTP voir les classes [CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

Cette fonction de membre `CGopherConnection` est appelée à construire un objet.

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
Un pointeur à l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) connexe.

*hConnecté*<br/>
La poignée Windows de la session Internet actuelle.

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur FTP.

*dwContexte*<br/>
L’identifiant de contexte pour l’opération. *dwContext* identifie les informations sur l’état de l’opération retournées par [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). La valeur par défaut est réglée à 1; toutefois, vous pouvez affecter explicitement une pièce d’identité de contexte spécifique pour l’opération. L’objet et tout travail qu’il fait sera associé à cette pièce d’identité contextuelle.

*pstrUserName (en)*<br/>
Pointeur vers une chaîne non terminée qui spécifie le nom de l’utilisateur à se connecter. Si NULL, la valeur par défaut est anonyme.

*pstrPassword (pstrPassword)*<br/>
Un pointeur à une chaîne non terminée qui spécifie le mot de passe à utiliser pour se connecter. Si *pstrPassword* et *pstrUserName* sont NULL, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* est NULL (ou une chaîne vide) mais *pstrUserName n’est* pas NULL, un mot de passe vierge est utilisé. Le tableau suivant décrit le comportement des quatre réglages possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName (en)*|*pstrPassword (pstrPassword)*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou "|NULL ou "|"anonyme"|Nom de l’e-mail de l’utilisateur|
|Chaîne non-NULL|NULL ou "|*pstrUserName (en)*|" "|
|NULL Non- NULL String|ERROR|ERROR||
|Chaîne non-NULL|Chaîne non-NULL|*pstrUserName (en)*|*pstrPassword (pstrPassword)*|

*nPort (en)*<br/>
Un numéro qui identifie le port TCP/IP à utiliser sur le serveur.

### <a name="remarks"></a>Notes

Vous ne `CGopherConnection` créez jamais un directement. Plutôt, appelez [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), `CGopherConnection` qui crée un objet et retourne un pointeur à elle.

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a>CGopherConnection::CreateLocator

Appelez cette fonction de membre pour créer un localisateur de gopher pour trouver ou identifier un fichier sur un serveur de gopher.

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
Un pointeur à une chaîne contenant le nom du document de gaufre ou de l’annuaire à récupérer. Si le *paramètre pstrDisplayString* est NULL, l’annuaire par défaut pour le serveur gopher est retourné.

*pstrSelectorString*<br/>
Un pointeur à la chaîne de sélecteur à envoyer au serveur gopher afin de récupérer un élément. *pstrSelectorString* peut être NULL.

*dwGopherType dwGopherType*<br/>
Cela spécifie si *pstrSelectorString* se réfère à un répertoire ou un document, et si la demande est gopher ou gopher. Voir les attributs de la structure [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) dans le SDK Windows.

*pstrLocator (en)*<br/>
Un pointeur à une chaîne identifiant le fichier à ouvrir. Généralement, cette chaîne est retournée d’un appel à [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur gopher.

*nPort (en)*<br/>
Le numéro d’identification du port Internet pour cette connexion.

### <a name="return-value"></a>Valeur de retour

Un objet [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

### <a name="remarks"></a>Notes

La version statique de la fonction membre vous oblige à spécifier un serveur, tandis que la version non statique utilise le nom du serveur à partir de l’objet de connexion.

Afin de récupérer des informations à partir d’un serveur gopher, une application doit d’abord obtenir un localisateur gopher. L’application doit ensuite traiter le repérage comme un jeton opaque (c’est-à-dire que l’application peut utiliser le localisateur mais pas le manipuler ou le comparer directement). Normalement, l’application utilise le localisateur pour les appels vers le [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) fonction membre pour récupérer un élément spécifique de l’information.

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a>CGopherConnection::GetAttribute

Appelez cette fonction de membre pour récupérer des informations d’attribut spécifiques sur un élément du serveur gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Paramètres

*refLocator*<br/>
Une référence à un objet [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*strRequestedAttributes*<br/>
Une chaîne délimitée dans l’espace spécifiant les noms des attributs demandés.

*strResult*<br/>
Une référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui reçoit le type de localisateur.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a>CGopherConnection::OpenFile

Appelez cette fonction de membre pour ouvrir un fichier sur un serveur gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*refLocator*<br/>
Une référence à un objet [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*dwFlags*<br/>
Toute combinaison de drapeaux INTERNET_FLAG_. Voir [CInternetSession:OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) pour plus d’informations sur INTERNET_FLAG_\* drapeaux.

*pstrView (en)*<br/>
Un pointeur à une chaîne de fichier-vue. Si plusieurs vues du fichier existent sur le serveur, ce paramètre spécifie quelle vue de fichier s’ouvrir. Si *pstrView* est NULL, la vue de fichier par défaut est utilisée.

*dwContexte*<br/>
L’ID contextuelle pour le fichier en cours d’ouverture. Voir **Remarques** pour plus d’informations sur *dwContext*.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’objet [CGopherFile](../../mfc/reference/cgopherfile-class.md) à ouvrir.

### <a name="remarks"></a>Notes

Remplacer la valeur par défaut *dwContext* pour définir l’identifiant de contexte à une valeur de votre choix. L’identifiant de contexte est associé `CGopherConnection` à cette opération spécifique de l’objet créé par son objet [CInternetSession.](../../mfc/reference/cinternetsession-class.md) La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’opération avec laquelle il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="see-also"></a>Voir aussi

[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CFtpConnection](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Classe CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[Classe CGopherFile](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession, classe](../../mfc/reference/cinternetsession-class.md)
