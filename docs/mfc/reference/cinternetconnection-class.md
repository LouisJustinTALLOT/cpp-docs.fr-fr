---
description: 'En savoir plus sur : classe CInternetConnection,'
title: CInternetConnection,, classe
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
ms.openlocfilehash: 2ae869e8cbf3bbfb3ce19e78088a465ae1d6aa65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143544"
---
# <a name="cinternetconnection-class"></a>CInternetConnection,, classe

Gère votre connexion à un serveur Internet.

## <a name="syntax"></a>Syntaxe

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetConnection, :: CInternetConnection,](#cinternetconnection)|Construit un objet `CInternetConnection`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CInternetConnection, :: GetContext](#getcontext)|Obtient l’ID de contexte pour cet objet de connexion.|
|[CInternetConnection, :: GetServerName](#getservername)|Obtient le nom du serveur associé à la connexion.|
|[CInternetConnection, :: GetSession](#getsession)|Obtient un pointeur vers l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) associé à la connexion.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CInternetConnection, :: Operator HINTERNET](#operator_hinternet)|Handle d’une session Internet.|

## <a name="remarks"></a>Notes

Il s’agit de la classe de base pour les classes MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md)et [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Chacune de ces classes fournit des fonctionnalités supplémentaires pour communiquer avec le serveur FTP, HTTP ou Gopher respectif.

Pour communiquer directement avec un serveur Internet, vous devez avoir un objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) et un `CInternetConnection` objet.

Pour en savoir plus sur le fonctionnement des classes WinInet, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a> CInternetConnection, :: CInternetConnection,

Cette fonction membre est appelée lorsqu’un `CInternetConnection` objet est créé.

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Paramètres

*pSession*<br/>
Pointeur vers un objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) .

*pstrServer*<br/>
Pointeur vers une chaîne contenant le nom du serveur.

*nPort*<br/>
Numéro qui identifie le port Internet pour cette connexion.

*dwContext*<br/>
Identificateur de contexte de l' `CInternetConnection` objet. Pour plus d’informations sur *dwContext*, consultez la **section Notes** .

### <a name="remarks"></a>Notes

Vous ne vous appelez jamais `CInternetConnection` ; à la place, appelez la fonction membre [CInternetSession](../../mfc/reference/cinternetsession-class.md) pour le type de connexion que vous souhaitez établir :

- [CInternetSession :: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession :: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession :: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

La valeur par défaut pour *dwContext* est envoyée par MFC à l' `CInternetConnection` objet dérivé de l’objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) qui a créé l’objet dérivé de **InternetConnection**. La valeur par défaut est 1 ; Toutefois, vous pouvez assigner explicitement un identificateur de contexte spécifique dans le constructeur [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) pour la connexion. L’objet et tout travail qu’il contient sont associés à cet ID de contexte. L’identificateur de contexte est retourné à [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Pour plus d’informations sur l’identificateur de contexte, consultez la section [Internet First Steps : wininet](../../mfc/wininet-basics.md) .

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a> CInternetConnection, :: GetContext

Appelez cette fonction membre pour obtenir l’ID de contexte pour cette session.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Valeur renvoyée

ID de contexte affecté à l’application.

### <a name="remarks"></a>Notes

L’ID de contexte est spécifié à l’origine dans [CInternetSession](../../mfc/reference/cinternetsession-class.md) et est propagé aux `CInternetConnection` classes dérivées de [CInternetFile](../../mfc/reference/cinternetfile-class.md), sauf indication contraire dans l’appel à une fonction qui ouvre la connexion. L’ID de contexte est associé à toute opération de l’objet donné et identifie les informations d’état de l’opération retournées par [CInternetSession :: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

Pour plus d’informations sur la façon dont `GetContext` fonctionne avec d’autres classes WinInet pour fournir les informations d’état de l’utilisateur, consultez l’article [première étape d’Internet : wininet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a> CInternetConnection, :: GetServerName

Appelez cette fonction membre pour récupérer le nom du serveur associé à cette connexion Internet.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nom du serveur avec lequel travaille cet objet de connexion.

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a> CInternetConnection, :: GetSession

Appelez cette fonction membre pour obtenir un pointeur vers l' `CInternetSession` objet associé à cette connexion.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CInternetSession](../../mfc/reference/cinternetsession-class.md) associé à cet objet de connexion Internet.

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a> CInternetConnection, :: Operator HINTERNET

Utilisez cet opérateur pour obtenir le handle au niveau de l’API pour la session Internet en cours.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
