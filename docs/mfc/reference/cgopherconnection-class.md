---
description: 'En savoir plus sur : classe CGopherConnection'
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
ms.openlocfilehash: c75cdea4df7a0f5ecbead3770f572d482432382d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184086"
---
# <a name="cgopherconnection-class"></a>CGopherConnection, classe

Gère votre connexion à un serveur Internet Gopher.

> [!NOTE]
> Les classes `CGopherConnection` , `CGopherFile` , `CGopherFileFind` `CGopherLocator` et leurs membres ont été dépréciées, car elles ne fonctionnent pas sur la plateforme Windows XP, mais elles continuent de fonctionner sur les plateformes antérieures.

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
|[CGopherConnection :: CreateLocator](#createlocator)|Crée un objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) pour rechercher des fichiers sur un serveur Gopher.|
|[CGopherConnection :: GetAttribute](#getattribute)|Récupère des informations d’attribut sur l’objet Gopher.|
|[CGopherConnection :: OpenFile](#openfile)|Ouvre un fichier Gopher.|

## <a name="remarks"></a>Notes

Le service Gopher est l’un des trois services Internet reconnus par les classes WinInet MFC.

La classe `CGopherConnection` contient un constructeur et trois fonctions membres supplémentaires qui gèrent le service gopher : [OpenFile](#openfile), [CreateLocator](#createlocator)et [GetAttribute](#getattribute).

Pour communiquer avec un serveur Internet Gopher, vous devez d’abord créer une instance de [CInternetSession](../../mfc/reference/cinternetsession-class.md), puis appeler [CInternetSession :: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), qui crée l' `CGopherConnection` objet et retourne un pointeur vers celui-ci. Vous ne devez jamais créer un `CGopherConnection` objet directement.

Pour en savoir plus sur le `CGopherConnection` fonctionnement des autres classes Internet MFC, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur l’utilisation des deux autres services Internet pris en charge, FTP et HTTP, consultez les classes [CHttpConnection](../../mfc/reference/chttpconnection-class.md) et [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a> CGopherConnection::CGopherConnection

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
Pointeur vers l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) associé.

*hConnected*<br/>
Handle Windows de la session Internet en cours.

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur FTP.

*dwContext*<br/>
Identificateur de contexte de l’opération. *dwContext* identifie les informations d’état de l’opération retournées par [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). La valeur par défaut est 1 ; Toutefois, vous pouvez assigner explicitement un ID de contexte spécifique pour l’opération. L’objet et tout travail qu’il contient sont associés à cet ID de contexte.

*pstrUserName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom de l’utilisateur qui doit se connecter. Si la valeur est NULL, la valeur par défaut est Anonymous.

*pstrPassword*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le mot de passe à utiliser pour se connecter. Si *pstrPassword* et *pstrUserName* sont tous les deux null, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* a la valeur null (ou une chaîne vide) mais que *pstrUserName* n’a pas la valeur null, un mot de passe vide est utilisé. Le tableau suivant décrit le comportement des quatre paramètres possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou «»|NULL ou «»|façon|Nom de messagerie de l’utilisateur|
|Chaîne non NULL|NULL ou «»|*pstrUserName*|" "|
|Chaîne NULL non NULL|ERROR|ERROR||
|Chaîne non NULL|Chaîne non NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Numéro qui identifie le port TCP/IP à utiliser sur le serveur.

### <a name="remarks"></a>Notes

Vous ne créez jamais `CGopherConnection` directement un. Au lieu de cela, appelez [CInternetSession :: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), qui crée un `CGopherConnection` objet et retourne un pointeur vers celui-ci.

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a> CGopherConnection :: CreateLocator

Appelez cette fonction membre pour créer un localisateur Gopher afin de rechercher ou d’identifier un fichier sur un serveur Gopher.

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
Pointeur vers une chaîne contenant le nom du document ou du répertoire Gopher à récupérer. Si le paramètre *pstrDisplayString* est null, le répertoire par défaut du serveur Gopher est renvoyé.

*pstrSelectorString*<br/>
Pointeur vers la chaîne du sélecteur à envoyer au serveur Gopher pour récupérer un élément. *pstrSelectorString* peut avoir la valeur null.

*dwGopherType*<br/>
Spécifie si *pstrSelectorString* fait référence à un répertoire ou à un document, et si la demande est Gopher ou gopher +. Consultez les attributs de la structure [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) dans le SDK Windows.

*pstrLocator*<br/>
Pointeur vers une chaîne qui identifie le fichier à ouvrir. En règle générale, cette chaîne est retournée à partir d’un appel à [CGopherFileFind :: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Pointeur vers une chaîne contenant le nom du serveur Gopher.

*nPort*<br/>
Numéro identifiant le port Internet pour cette connexion.

### <a name="return-value"></a>Valeur renvoyée

Objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

### <a name="remarks"></a>Notes

La version statique de la fonction membre vous oblige à spécifier un serveur, tandis que la version non statique utilise le nom du serveur de l’objet de connexion.

Pour récupérer des informations à partir d’un serveur Gopher, une application doit d’abord obtenir un localisateur Gopher. L’application doit ensuite traiter le localisateur comme un jeton opaque (autrement dit, l’application peut utiliser le localisateur, mais pas directement la manipuler ou la comparer). Normalement, l’application utilise le localisateur pour les appels à la fonction membre [CGopherFileFind :: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) pour récupérer une information spécifique.

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a> CGopherConnection :: GetAttribute

Appelez cette fonction membre pour récupérer des informations d’attribut spécifiques sur un élément à partir du serveur Gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Paramètres

*refLocator*<br/>
Référence à un objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*strRequestedAttributes*<br/>
Chaîne délimitée par des espaces spécifiant les noms des attributs demandés.

*strResult*<br/>
Référence à un [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui reçoit le type de localisateur.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a> CGopherConnection :: OpenFile

Appelez cette fonction membre pour ouvrir un fichier sur un serveur Gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*refLocator*<br/>
Référence à un objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*dwFlags*<br/>
Toute combinaison d’indicateurs INTERNET_FLAG_ *. Pour plus d’informations sur les indicateurs de INTERNET_FLAG_, consultez [CInternetSession :: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) \* .

*pstrView*<br/>
Pointeur vers une chaîne de vue de fichier. Si plusieurs vues du fichier existent sur le serveur, ce paramètre spécifie la vue de fichier à ouvrir. Si *pstrView* a la valeur null, la vue de fichier par défaut est utilisée.

*dwContext*<br/>
ID de contexte du fichier en cours d’ouverture. Pour plus d’informations sur *dwContext*, consultez la **section Notes** .

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet [CGopherFile](../../mfc/reference/cgopherfile-class.md) à ouvrir.

### <a name="remarks"></a>Notes

Remplacez la valeur par défaut de *dwContext* pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de l' `CGopherConnection` objet créé par son objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) . La valeur est retournée à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec laquelle elle est identifiée. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

## <a name="see-also"></a>Voir aussi

[CInternetConnection,, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection, classe](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection, classe](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection,, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator, classe](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile, classe](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession (classe)](../../mfc/reference/cinternetsession-class.md)
