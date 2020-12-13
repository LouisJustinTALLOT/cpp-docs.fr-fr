---
description: 'En savoir plus sur : classe CHttpConnection'
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
ms.openlocfilehash: 19a99f0f4eb6844d60a6e42a079214e1c70628fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143648"
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
|[CHttpConnection :: CHttpConnection](#chttpconnection)|Crée un objet `CHttpConnection`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|Ouvre une requête HTTP.|

## <a name="remarks"></a>Notes

HTTP est l’un des trois protocoles de serveur Internet implémentés par les classes WinInet MFC.

La classe `CHttpConnection` contient un constructeur et une fonction membre, [OpenRequest](#openrequest), qui gère les connexions à un serveur avec un protocole http.

Pour communiquer avec un serveur HTTP, vous devez d’abord créer une instance de [CInternetSession](../../mfc/reference/cinternetsession-class.md), puis créer un objet [CHttpConnection](#chttpconnection) . Vous ne créez jamais un `CHttpConnection` objet directement ; au lieu de cela, appelez [CInternetSession :: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), qui crée l' `CHttpConnection` objet et retourne un pointeur vers celui-ci.

Pour en savoir plus sur le `CHttpConnection` fonctionnement des autres classes Internet MFC, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md). Pour plus d’informations sur la connexion aux serveurs à l’aide des deux autres protocoles Internet pris en charge, Gopher et FTP, consultez les classes [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) et [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a> CHttpConnection :: CHttpConnection

Cette fonction membre est appelée pour construire un `CHttpConnection` objet.

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
Pointeur vers un objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) .

*hConnected*<br/>
Handle d’une connexion Internet.

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur.

*dwContext*<br/>
Identificateur de contexte de l' `CInternetConnection` objet. Pour plus d’informations sur *dwContext*, consultez la section **Notes** .

*nPort*<br/>
Numéro qui identifie le port Internet pour cette connexion.

*pstrUserName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le nom de l’utilisateur qui se connecte. Si la valeur est NULL, la valeur par défaut est Anonymous.

*pstrPassword*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui spécifie le mot de passe à utiliser pour se connecter. Si *pstrPassword* et *pstrUserName* sont tous les deux null, le mot de passe anonyme par défaut est le nom de messagerie de l’utilisateur. Si *pstrPassword* a la valeur null ou est une chaîne vide, alors que *pstrUserName* n’est pas null, un mot de passe vide est utilisé. Le tableau suivant décrit le comportement des quatre paramètres possibles de *pstrUserName* et *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Nom d’utilisateur envoyé au serveur FTP|Mot de passe envoyé au serveur FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL ou «»|NULL ou «»|façon|Nom de messagerie de l’utilisateur|
|Chaîne non NULL|NULL ou «»|*pstrUserName*|" "|
|NULL |Chaîne non NULL|ERROR|ERROR|
|Chaîne non NULL|Chaîne non NULL|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Toute combinaison d' `INTERNET_FLAG_*` indicateurs. Consultez le tableau de la section **Notes** de [CHttpConnection :: OpenRequest](#openrequest) pour obtenir une description des valeurs *dwFlags* .

### <a name="remarks"></a>Notes

Vous ne créez jamais `CHttpConnection` directement un. Au lieu de cela, vous créez un objet en appelant [CInternetSession :: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a> CHttpConnection :: OpenRequest

Appelez cette fonction membre pour ouvrir une connexion HTTP.

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

*pstrVerb*<br/>
Pointeur vers une chaîne contenant le verbe à utiliser dans la demande. Si la valeur est NULL, « obtient » est utilisé.

*pstrObjectName*<br/>
Pointeur vers une chaîne contenant l’objet cible du verbe spécifié. Cette chaîne est généralement un nom de fichier, un module exécutable ou un spécificateur de recherche.

*pstrReferer*<br/>
Pointeur vers une chaîne qui spécifie l’adresse (URL) du document à partir duquel l’URL de la demande (*pstrObjectName*) a été obtenue. Si la valeur est NULL, aucun en-tête HTTP n’est spécifié.

*dwContext*<br/>
Identificateur de contexte de l' `OpenRequest` opération. Pour plus d’informations sur *dwContext*, consultez la section Notes.

*ppstrAcceptTypes*<br/>
Pointeur vers un tableau de pointeurs LPCTSTR se terminant par un caractère null vers des chaînes indiquant les types de contenu acceptés par le client. Si *ppstrAcceptTypes* a la valeur null, les serveurs interprètent que le client accepte uniquement les documents de type « text/* » (autrement dit, seuls les documents texte et non les images ou d’autres fichiers binaires). Le type de contenu est équivalent à la variable CGI CONTENT_TYPE, qui identifie le type de données pour les requêtes qui ont des informations jointes, telles que HTTP Après et PUT.

*pstrVersion*<br/>
Pointeur vers une chaîne définissant la version HTTP. Si la valeur est NULL, « HTTP/1.0 » est utilisé.

*dwFlags*<br/>
Toute combinaison des indicateurs INTERNET_ FLAG_ *. Consultez la section Notes pour obtenir une description des valeurs *dwFlags* possibles.

*nVerb*<br/>
Nombre associé au type de requête HTTP. Il peut s'agir d'une des méthodes suivantes :

|Type de requête HTTP|valeur *nVerb*|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet [CHttpFile](../../mfc/reference/chttpfile-class.md) demandé.

### <a name="remarks"></a>Notes

*dwFlags* peut être l’un des éléments suivants :

|Indicateur Internet|Description|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Force le téléchargement du fichier, de l’objet ou de la liste de répertoires demandés à partir du serveur d’origine, et non à partir du cache.|
|INTERNET_FLAG_DONT_CACHE|N’ajoute pas l’entité retournée au cache.|
|INTERNET_FLAG_MAKE_PERSISTENT|Ajoute l’entité retournée au cache en tant qu’entité persistante. Cela signifie que le nettoyage du cache standard, la vérification de la cohérence ou la garbage collection ne peuvent pas supprimer cet élément du cache.|
|INTERNET_FLAG_SECURE|Utilise la sémantique des transactions sécurisées. Il se traduit par l’utilisation de SSL/PCT et est uniquement significatif dans les requêtes HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Utilisé uniquement avec HTTP, spécifie que les redirections ne doivent pas être gérées automatiquement dans [CHttpFile :: SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Remplacez la valeur `dwContext` par défaut pour définir l’identificateur de contexte sur la valeur de votre choix. L’identificateur de contexte est associé à cette opération spécifique de l' `CHttpConnection` objet créé par son objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) . La valeur est retournée à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’opération avec laquelle elle est identifiée. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

Les exceptions peuvent être levées avec cette fonction.

## <a name="see-also"></a>Voir aussi

[CInternetConnection,, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection,, classe](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile, classe](../../mfc/reference/chttpfile-class.md)
