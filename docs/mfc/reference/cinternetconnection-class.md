---
title: CInternetConnection, classe
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 6649986f279e010a833b31157922cb4fd1ea8613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372425"
---
# <a name="cinternetconnection-class"></a>CInternetConnection, classe

Gère votre connexion à un serveur Internet.

## <a name="syntax"></a>Syntaxe

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Construit un objet `CInternetConnection`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|Obtient l’ID de contexte pour cet objet de connexion.|
|[CInternetConnection::GetServerName](#getservername)|Obtient le nom du serveur associé à la connexion.|
|[CInternetConnection::GetSession](#getsession)|Obtient un pointeur à l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) associé à la connexion.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetConnection::opérateur HINTERNET](#operator_hinternet)|Une poignée à une session Internet.|

## <a name="remarks"></a>Notes

C’est la classe de base pour les classes MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md), et [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Chacune de ces classes fournit des fonctionnalités supplémentaires pour communiquer avec le serveur FTP, HTTP ou gopher respectif.

Pour communiquer directement avec un serveur Internet, vous devez disposer d’un objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) et d’un `CInternetConnection` objet.

Pour en savoir plus sur le fonctionnement des classes WinInet, consultez l’article [Internet Programming with WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a>CInternetConnection::CInternetConnection

Cette fonction de membre `CInternetConnection` est appelée lorsqu’un objet est créé.

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pSession*<br/>
Un pointeur à un objet [CInternetSession.](../../mfc/reference/cinternetsession-class.md)

*pstrServer (en)*<br/>
Un pointeur à une chaîne contenant le nom du serveur.

*nPort (en)*<br/>
Le numéro qui identifie le port Internet pour cette connexion.

*dwContexte*<br/>
L’identifiant de `CInternetConnection` contexte pour l’objet. Voir **Remarques** pour plus d’informations sur *dwContext*.

### <a name="remarks"></a>Notes

On ne `CInternetConnection` s’appelle jamais toi-même; au lieu de cela, appelez la fonction membre [CInternetSession](../../mfc/reference/cinternetsession-class.md) pour le type de connexion que vous souhaitez établir :

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

La valeur par défaut pour *dwContext* `CInternetConnection`est envoyée par MFC à l’objet dérivé de [l’objet CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l’objet dérivé **d’InternetConnection.** La valeur par défaut est réglée à 1; toutefois, vous pouvez affecter explicitement un identifiant de contexte spécifique dans le constructeur [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) pour la connexion. L’objet et tout travail qu’il fait sera associé à cette pièce d’identité contextuelle. L’identifiant de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état sur l’objet avec lequel il est identifié. Voir l’article [Internet First Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a>CInternetConnection::GetContext

Appelez cette fonction de membre pour obtenir l’ID de contexte pour cette session.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valeur de retour

L’ID de contexte assigné par l’application.

### <a name="remarks"></a>Notes

L’ID de contexte est à l’origine spécifié dans `CInternetConnection` [CInternetSession](../../mfc/reference/cinternetsession-class.md) et se propage à - et [CInternetFile](../../mfc/reference/cinternetfile-class.md)- classes dérivées, sauf spécifié différemment dans l’appel à une fonction qui ouvre la connexion. L’ID contextuelle est associé à toute opération de l’objet donné et identifie les informations d’état de l’opération retournées par [CInternetSession:OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

Pour plus d’informations sur la façon dont `GetContext` fonctionne avec d’autres classes WinInet pour donner des informations sur l’état de l’utilisateur, consultez l’article Internet First [Steps: WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identifiant de contexte.

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a>CInternetConnection::GetServerName

Appelez cette fonction de membre pour obtenir le nom du serveur associé à cette connexion Internet.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom du serveur avec lequel cet objet de connexion travaille.

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a>CInternetConnection::GetSession

Appelez cette fonction de membre `CInternetSession` pour obtenir un pointeur à l’objet qui est associé à cette connexion.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) associé à cet objet de connexion Internet.

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetConnection::opérateur HINTERNET

Utilisez cet opérateur pour obtenir la poignée au niveau API pour la session Internet en cours.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
