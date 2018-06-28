---
title: Classe de CInternetConnection | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
dev_langs:
- C++
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 227637dc042777725692122babe0d4c7b232d578
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037776"
---
# <a name="cinternetconnection-class"></a>Classe de CInternetConnection
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
|[CInternetConnection::GetServerName](#getservername)|Obtient le nom de serveur associé à la connexion.|  
|[CInternetConnection::GetSession](#getsession)|Obtient un pointeur vers le [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet associé à la connexion.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Un handle à une session Internet.|  
  
## <a name="remarks"></a>Notes  
 Il s’agit de la classe de base pour les classes MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [objet CHttpConnection](../../mfc/reference/chttpconnection-class.md), et [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Chacune de ces classes fournit des fonctionnalités supplémentaires pour la communication avec le serveur FTP, HTTP et gopher respectif.  
  
 Pour communiquer directement avec un serveur Internet, vous devez avoir un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet et un `CInternetConnection` objet.  
  
 Pour plus d’informations sur comment WinInet les classes de travail, consultez l’article [de programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxinet.h  
  
##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection  
 Cette fonction membre est appelée quand un `CInternetConnection` objet est créé.  
  
```  
CInternetConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Paramètres  
 *pSession*  
 Un pointeur vers un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet.  
  
 *pstrServer*  
 Un pointeur vers une chaîne contenant le nom du serveur.  
  
 *%nPort*  
 Numéro qui identifie le port Internet pour cette connexion.  
  
 *dwContext*  
 L’identificateur de contexte pour le `CInternetConnection` objet. Consultez **remarques** pour plus d’informations sur *dwContext*.  
  
### <a name="remarks"></a>Notes  
 Ne jamais appeler `CInternetConnection` ; au lieu de cela, appelez le [CInternetSession](../../mfc/reference/cinternetsession-class.md) fonction membre pour le type de connexion que vous souhaitez établir :  
  
- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)  
  
- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)  
  
- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)  
  
 La valeur par défaut *dwContext* est envoyé par MFC pour le `CInternetConnection`-objet dérivé le [CInternetSession](../../mfc/reference/cinternetsession-class.md) de l’objet qui a créé le **InternetConnection**- objet dérivé. La valeur par défaut est définie sur 1 ; Toutefois, vous pouvez affecter explicitement un identificateur de contexte spécifique dans le [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) constructeur pour la connexion. L’objet et tout travail qu’elle fournit à associer à cet ID de contexte. L’identificateur de contexte est retourné à [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) pour fournir l’état de l’objet avec lequel il est identifié. Consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.  
  
##  <a name="getcontext"></a>  CInternetConnection::GetContext  
 Appelez cette fonction membre pour obtenir l’ID de contexte pour cette session.  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID de contexte d’application attribuée.  
  
### <a name="remarks"></a>Notes  
 L’ID de contexte est spécifiée à l’origine dans [CInternetSession](../../mfc/reference/cinternetsession-class.md) et se propage à `CInternetConnection`- et [CInternetFile](../../mfc/reference/cinternetfile-class.md)-classes dérivées, sauf indication différemment dans l’appel à une fonction qui s’ouvre la connexion. L’ID de contexte est associé à une opération de l’objet donné et identifie les informations d’état de l’opération retournées par [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).  
  
 Pour plus d’informations sur la façon `GetContext` fonctionne avec d’autres classes WinInet pour donner les informations d’état utilisateur, consultez l’article [Internet premières étapes : WinInet](../../mfc/wininet-basics.md) pour plus d’informations sur l’identificateur de contexte.  
  
##  <a name="getservername"></a>  CInternetConnection::GetServerName  
 Appelez cette fonction membre pour obtenir le nom du serveur associé à cette connexion Internet.  
  
```  
CString GetServerName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nom du serveur que cet objet de connexion fonctionne.  
  
##  <a name="getsession"></a>  CInternetConnection::GetSession  
 Appelez cette fonction membre pour obtenir un pointeur vers le `CInternetSession` objet qui est associé à cette connexion.  
  
```  
CInternetSession* GetSession() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un [CInternetSession](../../mfc/reference/cinternetsession-class.md) objet associé à cet objet de connexion Internet.  
  
##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET  
 Cet opérateur permet d’obtenir le handle au niveau de l’API pour la session Internet.  
  
```  
operator HINTERNET() const;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



