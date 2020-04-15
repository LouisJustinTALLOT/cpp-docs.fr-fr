---
title: CHttpConnection, classe
ms.date: 03/27/2019
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: af402b532b3aba28bdfefea5afa67331765db4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351816"
---
# <a name="chttpconnection-class"></a>CHttpConnection, classe

Gère votre connexion à un serveur HTTP.

## <a name="syntax"></a>Syntaxe

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHttpConnection::CHttpConnection](#chttpconnection)|Crée un objet `CHttpConnection` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|Ouvre une demande HTTP.|

## <a name="remarks"></a>Notes

HTTP est l’un des trois protocoles de serveur Internet mis en œuvre par les classes MFC WinInet.

La `CHttpConnection` classe contient un constructeur et une fonction membre, [OpenRequest](#openrequest), qui gère les connexions à un serveur avec un protocole HTTP.

Pour communiquer avec un serveur HTTP, vous devez d’abord créer un exemple de [CInternetSession,](../../mfc/reference/cinternetsession-class.md)puis créer un objet [CHttpConnection.](#chttpconnection) Vous ne `CHttpConnection` créez jamais un objet directement; plutôt, appelez [CInternetSession:GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), `CHttpConnection` qui crée l’objet et retourne un pointeur à elle.

Pour en savoir `CHttpConnection` plus sur la façon dont fonctionne avec les autres classes Internet MFC, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur la connexion aux serveurs à l’aide des deux autres protocoles Internet pris en charge, gopher et FTP, consultez les classes [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) et [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>CHttpConnection::CHttpConnection

Cette fonction de membre `CHttpConnection` est appelée à construire un objet.

```
CHttpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pSession*<br/>
Un pointeur à un objet [CInternetSession.](../../mfc/reference/cinternetsession-class.md)

*hConnecté*<br/>
Une poignée à une connexion Internet.

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur.

*dwContexte*<br/>
L’identifiant de `CInternetConnection` contexte pour l’objet. Pour plus d’informations sur *dwContext*, voir la section **Remarques.**

*nPort (en)*<br/>
Le numéro qui identifie le port Internet pour cette connexion.

*pstrUserName (en)*<br/>
Pointeur vers une chaîne désintérable qui spécifie le nom de l’utilisateur à signer. Si NULL, la valeur par défaut est anonyme.

*pstrPassword (pstrPassword)*<br/>
Un pointeur à une chaîne désilisable qui spécifie le mot de passe à utiliser pour se connecter. Si *pstrPassword* et *pstrUserName* sont NULL, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* est NULL ou une chaîne vide, mais *pstrUserName n’est* pas NULL, un mot de passe vierge est utilisé. Le tableau suivant décrit le comportement des quatre réglages possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName (en)*|*pstrPassword (pstrPassword)*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou "|NULL ou "|"anonyme"|Nom de l’e-mail de l’utilisateur|
|Chaîne non-NULL|NULL ou "|*pstrUserName (en)*|" "|
|NULL |Chaîne non-NULL|ERROR|ERROR|
|Chaîne non-NULL|Chaîne non-NULL|*pstrUserName (en)*|*pstrPassword (pstrPassword)*|

*dwFlags*<br/>
Toute combinaison `INTERNET_FLAG_*` des drapeaux. Voir le tableau dans la section **Remarques** de [CHttpConnection::OpenRequest](#openrequest) pour une description des valeurs *dwFlags.*

### <a name="remarks"></a>Notes

Vous ne `CHttpConnection` créez jamais un directement. Au contraire, vous créez un objet en appelant [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a>CHttpConnection::OpenRequest

Appelez cette fonction de membre pour ouvrir une connexion HTTP.

```
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

CHttpFile* OpenRequest(
    int nVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```

### <a name="parameters"></a>Paramètres

*pstrVerb (pstrVerb)*<br/>
Un pointeur à une chaîne contenant le verbe à utiliser dans la demande. Si NULL, "GET" est utilisé.

*pstrObjectName*<br/>
Pointeur d’une chaîne contenant l’objet cible du verbe spécifié. Cette chaîne est généralement un nom de fichier, un module exécutable ou un spécificateur de recherche.

*pstrReferer (en)*<br/>
Un pointeur à une chaîne qui spécifie l’adresse (URL) du document à partir de laquelle l’URL dans la demande (*pstrObjectName*) a été obtenue. Si NULL, aucun en-tête HTTP n’est spécifié.

*dwContexte*<br/>
L’identifiant de `OpenRequest` contexte pour l’opération. Pour plus d’informations sur *dwContext*, voir la section Remarques.

*ppstrAcceptTypes*<br/>
Un pointeur à un tableau annulé de pointeurs LPCTSTR aux chaînes indiquant les types de contenu acceptés par le client. Si *ppstrAcceptTypes* est NULL, les serveurs interprètent que le client n’accepte que les documents de type "texte/" (c’est-à-dire seulement des documents texte et non des photos ou d’autres fichiers binaires). Le type de contenu est équivalent à la variable DE CGI CONTENT_TYPE, qui identifie le type de données pour les requêtes qui ont joint des informations, telles que HTTP POST et PUT.

*pstrVersion*<br/>
Un pointeur à une chaîne définissant la version HTTP. Si NULL, "HTTP/1.0" est utilisé.

*dwFlags*<br/>
Toute combinaison des INTERNET_ FLAG_. Consultez la section Remarques pour une description des valeurs *dwFlags* possibles.

*nVerb (en)*<br/>
Un numéro associé au type de demande HTTP. Il peut s'agir d'une des méthodes suivantes :

|Type de demande HTTP|*nVerb* valeur|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’objet [CHttpFile](../../mfc/reference/chttpfile-class.md) demandé.

### <a name="remarks"></a>Notes

*dwFlags* peut être l’un des suivants:

|Indicateur Internet|Description|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Force un téléchargement du fichier demandé, objet, ou la liste d’annuaire à partir du serveur d’origine, pas à partir du cache.|
|INTERNET_FLAG_DONT_CACHE|N’ajoute pas l’entité retournée au cache.|
|INTERNET_FLAG_MAKE_PERSISTENT|Ajoute l’entité retournée au cache en tant qu’entité persistante. Cela signifie que le nettoyage standard des caches, la vérification de la cohérence ou la collecte des ordures ne peuvent pas retirer cet article du cache.|
|INTERNET_FLAG_SECURE|Utilise la sémantique sécurisée de transaction. Il se traduit par l’utilisation de SSL/PCT et n’est significatif que dans les demandes HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Utilisé uniquement avec HTTP, spécifie que les redirections ne doivent pas être traitées automatiquement dans [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Remplacez `dwContext` la valeur par défaut pour définir l’identifiant de contexte à une valeur de votre choix. L’identifiant de contexte est associé `CHttpConnection` à cette opération spécifique de l’objet créé par son objet [CInternetSession.](../../mfc/reference/cinternetsession-class.md) La valeur est retournée à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’opération avec laquelle il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

Des exceptions peuvent être écartées de cette fonction.

## <a name="see-also"></a>Voir aussi

[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Classe CHttpFile](../../mfc/reference/chttpfile-class.md)
