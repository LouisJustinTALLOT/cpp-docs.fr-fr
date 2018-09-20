---
title: CAsyncSocket, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAsyncSocket
- AFXSOCK/CAsyncSocket
- AFXSOCK/CAsyncSocket::CAsyncSocket
- AFXSOCK/CAsyncSocket::Accept
- AFXSOCK/CAsyncSocket::AsyncSelect
- AFXSOCK/CAsyncSocket::Attach
- AFXSOCK/CAsyncSocket::Bind
- AFXSOCK/CAsyncSocket::Close
- AFXSOCK/CAsyncSocket::Connect
- AFXSOCK/CAsyncSocket::Create
- AFXSOCK/CAsyncSocket::Detach
- AFXSOCK/CAsyncSocket::FromHandle
- AFXSOCK/CAsyncSocket::GetLastError
- AFXSOCK/CAsyncSocket::GetPeerName
- AFXSOCK/CAsyncSocket::GetPeerNameEx
- AFXSOCK/CAsyncSocket::GetSockName
- AFXSOCK/CAsyncSocket::GetSockNameEx
- AFXSOCK/CAsyncSocket::GetSockOpt
- AFXSOCK/CAsyncSocket::IOCtl
- AFXSOCK/CAsyncSocket::Listen
- AFXSOCK/CAsyncSocket::Receive
- AFXSOCK/CAsyncSocket::ReceiveFrom
- AFXSOCK/CAsyncSocket::ReceiveFromEx
- AFXSOCK/CAsyncSocket::Send
- AFXSOCK/CAsyncSocket::SendTo
- AFXSOCK/CAsyncSocket::SendToEx
- AFXSOCK/CAsyncSocket::SetSockOpt
- AFXSOCK/CAsyncSocket::ShutDown
- AFXSOCK/CASyncSocket::Socket
- AFXSOCK/CAsyncSocket::OnAccept
- AFXSOCK/CAsyncSocket::OnClose
- AFXSOCK/CAsyncSocket::OnConnect
- AFXSOCK/CAsyncSocket::OnOutOfBandData
- AFXSOCK/CAsyncSocket::OnReceive
- AFXSOCK/CAsyncSocket::OnSend
- AFXSOCK/CAsyncSocket::m_hSocket
dev_langs:
- C++
helpviewer_keywords:
- CAsyncSocket [MFC], CAsyncSocket
- CAsyncSocket [MFC], Accept
- CAsyncSocket [MFC], AsyncSelect
- CAsyncSocket [MFC], Attach
- CAsyncSocket [MFC], Bind
- CAsyncSocket [MFC], Close
- CAsyncSocket [MFC], Connect
- CAsyncSocket [MFC], Create
- CAsyncSocket [MFC], Detach
- CAsyncSocket [MFC], FromHandle
- CAsyncSocket [MFC], GetLastError
- CAsyncSocket [MFC], GetPeerName
- CAsyncSocket [MFC], GetPeerNameEx
- CAsyncSocket [MFC], GetSockName
- CAsyncSocket [MFC], GetSockNameEx
- CAsyncSocket [MFC], GetSockOpt
- CAsyncSocket [MFC], IOCtl
- CAsyncSocket [MFC], Listen
- CAsyncSocket [MFC], Receive
- CAsyncSocket [MFC], ReceiveFrom
- CAsyncSocket [MFC], ReceiveFromEx
- CAsyncSocket [MFC], Send
- CAsyncSocket [MFC], SendTo
- CAsyncSocket [MFC], SendToEx
- CAsyncSocket [MFC], SetSockOpt
- CAsyncSocket [MFC], ShutDown
- CASyncSocket [MFC], Socket
- CAsyncSocket [MFC], OnAccept
- CAsyncSocket [MFC], OnClose
- CAsyncSocket [MFC], OnConnect
- CAsyncSocket [MFC], OnOutOfBandData
- CAsyncSocket [MFC], OnReceive
- CAsyncSocket [MFC], OnSend
- CAsyncSocket [MFC], m_hSocket
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef45fa1804b9199a6fc7d34b6c5d1aca278d47d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424350"
---
# <a name="casyncsocket-class"></a>CAsyncSocket (classe)

Représente un Socket Windows, un point de terminaison de communication réseau.

## <a name="syntax"></a>Syntaxe

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Construit un objet `CAsyncSocket`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAsyncSocket::Accept](#accept)|Accepte une connexion sur le socket.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Notification d’événement de demandes pour le socket.|
|[CAsyncSocket::Attach](#attach)|Attache un handle de socket à un `CAsyncSocket` objet.|
|[CAsyncSocket::Bind](#bind)|Associe une adresse locale du socket.|
|[CAsyncSocket::Close](#close)|Ferme le socket.|
|[CAsyncSocket::Connect](#connect)|Établit une connexion à un socket d’homologue.|
|[CAsyncSocket::Create](#create)|Crée un socket.|
|[CAsyncSocket::Detach](#detach)|Détache un handle de socket à partir d’un `CAsyncSocket` objet.|
|[CAsyncSocket::FromHandle](#fromhandle)|Retourne un pointeur vers un `CAsyncSocket` objet, un handle de socket.|
|[CAsyncSocket::GetLastError](#getlasterror)|Obtient l’état d’erreur pour la dernière opération qui a échoué.|
|[CAsyncSocket::GetPeerName](#getpeername)|Obtient l’adresse du socket homologue auquel le socket est connecté.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Obtient l’adresse du socket homologue auquel le socket est connecté (gère les adresses IPv6).|
|[Fonction membre CAsyncSocket::GetSockName](#getsockname)|Obtient le nom local pour un socket.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Obtient le nom local pour un socket (gère les adresses IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Récupère une option de socket.|
|[CAsyncSocket::IOCtl](#ioctl)|Contrôle le mode du socket.|
|[CAsyncSocket::Listen](#listen)|Établit un socket pour écouter les demandes de connexion entrantes.|
|[CAsyncSocket::Receive](#receive)|Reçoit les données à partir du socket.|
|[CAsyncSocket::ReceiveFrom](#receivefrom)|Reçoit un datagramme et stocke l’adresse source.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Reçoit un datagramme et stocke l’adresse source (gère les adresses IPv6).|
|[CAsyncSocket::Send](#send)|Envoie des données à un socket connecté.|
|[CAsyncSocket::SendTo](#sendto)|Envoie des données vers une destination spécifique.|
|[CAsyncSocket::SendToEx](#sendtoex)|Envoie des données vers une destination spécifique (gère les adresses IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Définit une option de socket.|
|[CAsyncSocket::ShutDown](#shutdown)|Désactive `Send` et/ou `Receive` appelle sur le socket.|
|[CASyncSocket::Socket](#socket)|Alloue un handle de socket.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|Avertit un socket d’écoute qu’il peut accepter les demandes de connexion en attente en appelant `Accept`.|
|[CAsyncSocket::OnClose](#onclose)|Avertit un socket connecté le socket a fermé.|
|[CAsyncSocket::OnConnect](#onconnect)|Avertit un socket de connexion que la tentative de connexion est terminée, si avec succès ou erreur.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Avertit un socket de réception qu’il existe des données hors-bande à lire sur le socket, généralement un message urgent.|
|[CAsyncSocket::OnReceive](#onreceive)|Avertit un socket d’écoute qu’il existe des données doit être récupéré en appelant `Receive`.|
|[CAsyncSocket::OnSend](#onsend)|Avertit un socket qu’il peut envoyer des données en appelant `Send`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAsyncSocket::operator =](#operator_eq)|Assigne une nouvelle valeur à un `CAsyncSocket` objet.|
|[CAsyncSocket::operator SOCKET](#operator_socket)|Utilisez cet opérateur pour récupérer le handle SOCKET de la `CAsyncSocket` objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Indique le handle SOCKET associé à ce `CAsyncSocket` objet.|

## <a name="remarks"></a>Notes

Classe `CAsyncSocket` encapsule l’API de fonctions de Socket Windows, en fournissant une abstraction et orienté objet pour les programmeurs qui souhaitent utiliser Windows Sockets conjointement avec MFC.

Cette classe est basée sur l’hypothèse que vous comprenez les communications réseau. Vous êtes chargé de gérer le blocage, les différences d’ordre d’octet, et les conversions entre des caractères Unicode et définir des chaînes (MBCS). Si vous souhaitez une interface plus pratique qui gère ces problèmes pour vous, consultez la classe [CSocket](../../mfc/reference/csocket-class.md).

À utiliser un `CAsyncSocket` d’objet, appeler son constructeur, puis appelez le [créer](#create) (fonction) pour créer le handle de socket sous-jacent (type `SOCKET`), sauf sur les sockets acceptés. Pour un appel de socket serveur le [écouter](#listen) fonction membre et pour un appel de socket client le [Connect](#connect) fonction membre. Le socket de serveur doit appeler le [Accept](#accept) fonction lors de la réception d’une demande de connexion. Utilisez les autres `CAsyncSocket` fonctions pour effectuer des communications entre les sockets. À l’achèvement, détruire le `CAsyncSocket` l’objet s’il a été créé sur le tas ; le destructeur appelle automatiquement la [fermer](#close) (fonction). Le type de données SOCKET est décrit dans l’article [Windows Sockets : arrière-plan](../../mfc/windows-sockets-background.md).

> [!NOTE]
>  Lors de l’utilisation de sockets MFC dans les threads secondaires dans une application MFC liée de manière statique, vous devez appeler `AfxSocketInit` dans chaque thread qui utilise des sockets pour initialiser les bibliothèques de socket. Par défaut, `AfxSocketInit` est uniquement appelée dans le thread principal.

Pour plus d’informations, consultez [Windows Sockets : à l’aide de classe CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) et articles connexes., ainsi que [API Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxsock.h

##  <a name="accept"></a>  CAsyncSocket::Accept

Appelez cette fonction membre pour accepter une connexion sur un socket.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Paramètres

*rConnectedSocket*<br/>
Une référence d’identification d’un nouveau socket qui est disponible pour la connexion.

*lpSockAddr*<br/>
Un pointeur vers un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure qui reçoit l’adresse de la connexion de socket, connue sur le réseau. Le format exact de la *lpSockAddr* argument est déterminé par la famille d’adresses établie lorsque le socket a été créé. Si *lpSockAddr* et/ou *lpSockAddrLen* sont égales à NULL, aucune information sur l’adresse distante du socket accepté est retourné.

*lpSockAddrLen*<br/>
Un pointeur vers la longueur de l’adresse dans *lpSockAddr* en octets. Le *lpSockAddrLen* est un paramètre de résultat de la valeur : il doit contenir initialement la quantité d’espace vers lequel pointé *lpSockAddr*; il contient la longueur réelle (en octets) de l’adresse renvoyée au retour.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT le *lpSockAddrLen* argument est trop faible (inférieur à la taille d’un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure).

- A WSAEINPROGRESS qu'appeler de blocage Windows Sockets est en cours.

- WSAEINVAL `Listen` n’était pas appelé avant l’accepter.

- WSAEMFILE la file d’attente est vide lors de l’entrée pour accepter et qu’aucun descripteur est disponible.

- Espace de mémoire tampon WSAENOBUFS No est disponible.

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEOPNOTSUPP le socket référencé n’est pas un type qui prend en charge de service orienté connexion.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et aucune connexion n’est présente pour être accepté.

### <a name="remarks"></a>Notes

Cette routine extrait la première connexion dans la file d’attente des connexions en attente, crée un nouveau socket avec les mêmes propriétés que ce socket et attache à *rConnectedSocket*. Si aucune connexion en attente n’est présentes sur la file d’attente, `Accept` retourne la valeur zéro et `GetLastError` retourne une erreur. Le socket accepté ( *rConnectedSocket)* ne peut pas être utilisé pour accepter plus de connexions. Le socket d’origine reste ouverte et à l’écoute.

L’argument *lpSockAddr* est un paramètre de résultat qui est rempli avec l’adresse de connexion de socket, connues de la couche des communications. `Accept` est utilisé avec types basée sur une connexion de socket telles que SOCK_STREAM.

##  <a name="asyncselect"></a>  CAsyncSocket::AsyncSelect

Appelez cette fonction membre pour demander la notification d’événement pour un socket.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Paramètres

*lEvent*<br/>
Masque de bits qui spécifie une combinaison d’événements réseau dans lequel l’application s’intéresse.

- FD_READ souhaitez recevoir une notification de préparation pour la lecture.

- FD_WRITE souhaitez recevoir une notification lorsque les données sont disponibles pour la lecture.

- FD_OOB souhaitez recevoir une notification de l’arrivée des données hors bande.

- FD_ACCEPT souhaitez recevoir une notification de connexions entrantes.

- FD_CONNECT souhaitez recevoir une notification des résultats de la connexion.

- FD_CLOSE souhaitez recevoir une notification lorsqu’un socket a été fermé par un homologue.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL indique que l’un des paramètres spécifiés n’est pas valide.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour spécifier les fonctions de notification de rappel MFC seront appelées pour le socket. `AsyncSelect` définit automatiquement ce socket en mode non bloquant. Pour plus d’informations, consultez l’article [Windows Sockets : Notifications de Socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="attach"></a>  CAsyncSocket::Attach

Appelez cette fonction membre pour attacher le *hSocket* handle vers un `CAsyncSocket` objet.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle à un socket.

*lEvent*<br/>
Masque de bits qui spécifie une combinaison d’événements réseau dans lequel l’application s’intéresse.

- FD_READ souhaitez recevoir une notification de préparation pour la lecture.

- FD_WRITE souhaitez recevoir une notification lorsque les données sont disponibles pour la lecture.

- FD_OOB souhaitez recevoir une notification de l’arrivée des données hors bande.

- FD_ACCEPT souhaitez recevoir une notification de connexions entrantes.

- FD_CONNECT souhaitez recevoir une notification des résultats de la connexion.

- FD_CLOSE souhaitez recevoir une notification lorsqu’un socket a été fermé par un homologue.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la fonction aboutit.

### <a name="remarks"></a>Notes

Le handle de SOCKET est stocké dans l’objet [m_hSocket](#m_hsocket) membre de données.

##  <a name="bind"></a>  CAsyncSocket::Bind

Appelez cette fonction membre pour associer une adresse locale du socket.

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);


BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Paramètres

*nSocketPort*<br/>
Le port identifiant l’application de socket.

*lpszSocketAddress*<br/>
L’adresse réseau, un nombre en pointillés tels que « 128.56.22.8 ». En passant la valeur NULL de chaîne pour ce paramètre indique le `CAsyncSocket` instance doit écouter les activités des clients sur toutes les interfaces réseau.

*lpSockAddr*<br/>
Un pointeur vers un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure qui contient l’adresse à attribuer à ce socket.

*nSockAddrLen*<br/>
La longueur de l’adresse dans *lpSockAddr* en octets.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE l’adresse spécifiée est déjà en cours d’utilisation. (Consultez l’option de socket SO_REUSEADDR sous [SetSockOpt](#setsockopt).)

- WSAEFAULT le *nSockAddrLen* argument est trop faible (inférieur à la taille d’un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure).

- A WSAEINPROGRESS qu'appeler de blocage Windows Sockets est en cours.

- WSAEAFNOSUPPORT la famille d’adresses spécifiée n’est pas pris en charge par ce port.

- WSAEINVAL le socket est déjà lié à une adresse.

- WSAENOBUFS pas suffisamment met en mémoire tampon disponible, trop de connexions.

- WSAENOTSOCK le descripteur n’est pas un socket.

### <a name="remarks"></a>Notes

Cette routine est utilisée sur un socket de flux de données, ou un datagramme non connecté avant suivantes `Connect` ou `Listen` appels. Avant d’accepter les demandes de connexion, un socket de serveur à l’écoute doit sélectionner un numéro de port et définissez-la comme connus Windows Sockets en appelant `Bind`. `Bind` établit l’association locale (hôte adresse/numéro de port) du socket en attribuant un nom local à un socket sans nom.

##  <a name="casyncsocket"></a>  CAsyncSocket::CAsyncSocket

Construit un objet socket vide.

```
CAsyncSocket();
```

### <a name="remarks"></a>Notes

Après la construction de l’objet, vous devez appeler son `Create` fonction membre pour créer la structure de données SOCKET et le lier son adresse. (Sur le côté serveur d’une communication de Windows Sockets, lorsque le socket d’écoute crée un socket à utiliser dans le `Accept` appel, vous n’appelez pas `Create` pour ce socket.)

##  <a name="close"></a>  CAsyncSocket::Close

Ferme le socket.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Cette fonction libère le descripteur de socket afin que les autres références à ce dernier échouera avec l’erreur WSAENOTSOCK. S’il s’agit de la dernière référence pour le socket sous-jacent, les informations d’affectation de noms associées et les données en file d’attente sont ignorées. Appels de destructeur de l’objet socket `Close` pour vous.

Pour `CAsyncSocket`, mais pas pour `CSocket`, la sémantique de `Close` sont affectées par les options de socket SO_LINGER et SO_DONTLINGER. Pour plus d’informations, consultez la fonction membre `GetSockOpt`.

##  <a name="connect"></a>  CAsyncSocket::Connect

Appelez cette fonction membre pour établir une connexion à un socket datagramme ou un flux non connecté.

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);


BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Paramètres

*lpszHostAddress*<br/>
L’adresse réseau du socket à laquelle cet objet est connecté : un nom d’ordinateur tel que « FTP.Microsoft.com », ou un nombre en pointillés tels que « 128.56.22.8 ».

*nHostPort*<br/>
Le port identifiant l’application de socket.

*lpSockAddr*<br/>
Un pointeur vers un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure qui contient l’adresse du socket connecté.

*nSockAddrLen*<br/>
La longueur de l’adresse dans *lpSockAddr* en octets.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Si cela indique un code d’erreur de WSAEWOULDBLOCK, et que votre application utilise les rappels substituables, votre application reçoit un `OnConnect` message lorsque l’opération de connexion est terminée. Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE l’adresse spécifiée est déjà en cours d’utilisation.

- A WSAEINPROGRESS qu'appeler de blocage Windows Sockets est en cours.

- WSAEADDRNOTAVAIL l’adresse spécifiée n’est pas disponible à partir de l’ordinateur local.

- Adresses WSAEAFNOSUPPORT dans la famille spécifiée ne peut pas être utilisés avec ce socket.

- WSAECONNREFUSED la tentative de connexion a été rejetée.

- Adresse de destination WSAEDESTADDRREQ A est requise.

- WSAEFAULT le *nSockAddrLen* argument est incorrect.

- Adresse d’hôte WSAEINVAL non valide.

- WSAEISCONN le socket est déjà connecté.

- WSAEMFILE aucun autre descripteur de fichier est disponibles.

- WSAENETUNREACH le réseau ne peut pas être atteint à partir de cet hôte pour l’instant.

- Espace de mémoire tampon WSAENOBUFS No est disponible. Le socket n’est pas accessible.

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAETIMEDOUT tentative de connexion a expiré sans avoir à établir une connexion.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et la connexion ne peut pas être effectuée immédiatement.

### <a name="remarks"></a>Notes

Si le socket est détachée, valeurs uniques sont affectés à l’association locale par le système, et le socket est marqué comme liés. Notez que si le champ d’adresse de la structure de nom est tous les zéros non significatifs, `Connect` retourne la valeur zéro. Pour obtenir les informations d’erreur étendues, appelez le `GetLastError` fonction membre.

Pour les sockets de flux de données (type SOCK_STREAM), une connexion active est lancée sur l’hôte externe. Lors de l’appel de socket se termine avec succès, le socket est prêt à envoyer/recevoir des données.

Pour un socket datagramme (type SOCK_DGRAM), une destination par défaut est définie, qui sera utilisée sur suivantes `Send` et `Receive` appels.

##  <a name="create"></a>  CAsyncSocket::Create

Appelez le `Create` fonction membre après la construction d’un objet socket pour créer le socket de Windows et l’attacher.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Paramètres

*nSocketPort*<br/>
Un port connu pour être utilisé avec le socket, ou 0 si vous souhaitez que les Sockets Windows pour sélectionner un port.

*nSocketType*<br/>
SOCK_STREAM ou SOCK_DGRAM.

*lEvent*<br/>
Masque de bits qui spécifie une combinaison d’événements réseau dans lequel l’application s’intéresse.

- FD_READ souhaitez recevoir une notification de préparation pour la lecture.

- FD_WRITE souhaitez recevoir une notification de préparation pour l’écriture.

- FD_OOB souhaitez recevoir une notification de l’arrivée des données hors bande.

- FD_ACCEPT souhaitez recevoir une notification de connexions entrantes.

- FD_CONNECT souhaitez recevoir une notification de connexion terminée.

- FD_CLOSE souhaitez recevoir une notification de fermeture du socket.

*lpszSockAddress*<br/>
Un pointeur vers une chaîne contenant l’adresse réseau du socket connecté, un nombre en pointillés tels que « 128.56.22.8 ». En passant la valeur NULL de chaîne pour ce paramètre indique le `CAsyncSocket` instance doit écouter les activités des clients sur toutes les interfaces réseau.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEAFNOSUPPORT la famille d’adresses spécifiée n’est pas pris en charge.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAEMFILE aucun autre descripteur de fichier est disponibles.

- Espace de mémoire tampon WSAENOBUFS No est disponible. Impossible de créer le socket.

- WSAEPROTONOSUPPORT le port spécifié n’est pas pris en charge.

- WSAEPROTOTYPE le port spécifié est de type incorrect pour ce socket.

- WSAESOCKTNOSUPPORT le type de socket spécifié n’est pas pris en charge dans cette famille d’adresses.

### <a name="remarks"></a>Notes

`Create` appels [Socket](#socket) et en cas de réussite, elle appelle [lier](#bind) pour lier le socket à l’adresse spécifiée. Les types de socket suivants sont pris en charge :

- SOCK_STREAM fournit séquencé, flux d’octets fiables, duplex intégral, basée sur la connexion. Utilise le protocole TCP (Transmission Control) pour la famille d’adresses Internet.

- Prend en charge SOCK_DGRAM datagrammes, qui sont peu fiables, sans connexion, les paquets de longueur maximale fixe (généralement réduite). Utilise le protocole UDP (User Datagram) pour la famille d’adresses Internet.

    > [!NOTE]
    >  Le `Accept` fonction membre prend une référence à un vide `CSocket` objet comme paramètre. Vous devez créer cet objet avant d’appeler `Accept`. N’oubliez pas que si cet objet socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet socket.

> [!IMPORTANT]
> `Create` est **pas** thread-safe.  Si vous appelez cela dans un environnement multithread où il peut être appelé simultanément par différents threads, veillez à protéger chaque appel avec un mutex ou autre verrou de synchronisation.

Pour plus d’informations sur les sockets de flux de données et de datagramme, consultez les articles [Windows Sockets : arrière-plan](../../mfc/windows-sockets-background.md) et [Windows Sockets : Ports et adresses de Socket](../../mfc/windows-sockets-ports-and-socket-addresses.md) et [API Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2).

##  <a name="detach"></a>  CAsyncSocket::Detach

Appelez cette fonction membre pour détacher le handle de SOCKET dans la *m_hSocket* membre de données à partir de la `CAsyncSocket` de l’objet et définissez *m_hSocket* avec la valeur NULL.

```
SOCKET Detach();
```

##  <a name="fromhandle"></a>  CAsyncSocket::FromHandle

Retourne un pointeur vers un `CAsyncSocket` objet.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle à un socket.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CAsyncSocket` de l’objet, ou NULL s’il n’existe aucun `CAsyncSocket` objet attaché à *hSocket*.

### <a name="remarks"></a>Notes

En fonction d’un handle de SOCKET, si un `CAsyncSocket` objet n’est pas attaché au handle, la fonction membre retourne NULL.

##  <a name="getlasterror"></a>  CAsyncSocket::GetLastError

Appelez cette fonction membre pour obtenir l’état d’erreur pour la dernière opération qui a échoué.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Valeur de retour

La valeur de retour indique le code d’erreur pour la routine API de Sockets Windows dernière effectuée par ce thread.

### <a name="remarks"></a>Notes

Lorsqu’une fonction membre particulière indique qu’une erreur s’est produite, `GetLastError` doit être appelé pour extraire le code d’erreur approprié. Consultez les descriptions de la fonction membre individuel pour obtenir la liste des codes d’erreur applicable.

Pour plus d’informations sur les codes d’erreur, consultez [API Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2).

##  <a name="getpeername"></a>  CAsyncSocket::GetPeerName

Appelez cette fonction membre pour obtenir l’adresse du socket homologue auquel est connecté ce socket.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);


BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Paramètres

*rPeerAddress*<br/>
Référence à un `CString` objet qui reçoit une adresse IP de nombre en pointillés.

*rPeerPort*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Un pointeur vers le [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure qui reçoit le nom du socket homologue.

*lpSockAddrLen*<br/>
Un pointeur vers la longueur de l’adresse dans *lpSockAddr* en octets. En retour, le *lpSockAddrLen* argument contient la taille réelle de *lpSockAddr* retournée en octets.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT le *lpSockAddrLen* argument n’est pas assez grand.

- A WSAEINPROGRESS qu'appeler de blocage Windows Sockets est en cours.

- WSAENOTCONN le socket n’est pas connecté.

- WSAENOTSOCK le descripteur n’est pas un socket.

### <a name="remarks"></a>Notes

Pour gérer les adresses IPv6, utilisez [CAsyncSocket::GetPeerNameEx](#getpeernameex).

##  <a name="getpeernameex"></a>  CAsyncSocket::GetPeerNameEx

Appelez cette fonction membre pour obtenir l’adresse du socket homologue auquel ce socket est connecté (gère les adresses IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Paramètres

*rPeerAddress*<br/>
Référence à un `CString` objet qui reçoit une adresse IP de nombre en pointillés.

*rPeerPort*<br/>
Référence à un UINT qui stocke un port.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT le *lpSockAddrLen* argument n’est pas assez grand.

- A WSAEINPROGRESS qu'appeler de blocage Windows Sockets est en cours.

- WSAENOTCONN le socket n’est pas connecté.

- WSAENOTSOCK le descripteur n’est pas un socket.

### <a name="remarks"></a>Notes

Cette fonction est identique à [CAsyncSocket::GetPeerName](#getpeername) , à ceci près qu’il gère IPv6 résout également que les anciens protocoles.

##  <a name="getsockname"></a>  Fonction membre CAsyncSocket::GetSockName

Appelez cette fonction membre pour obtenir le nom local pour un socket.

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);


BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Paramètres

*rSocketAddress*<br/>
Référence à un `CString` objet qui reçoit une adresse IP de nombre en pointillés.

*rSocketPort*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Un pointeur vers un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure qui reçoit l’adresse du socket.

*lpSockAddrLen*<br/>
Un pointeur vers la longueur de l’adresse dans *lpSockAddr* en octets.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT le *lpSockAddrLen* argument n’est pas assez grand.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEINVAL le socket n’a pas été lié à une adresse avec `Bind`.

### <a name="remarks"></a>Notes

Cet appel est particulièrement utile quand un `Connect` appel a été effectué sans effectuer un `Bind` tout d’abord ; cet appel fournit le seul moyen par lequel vous pouvez déterminer l’association locale qui a été définie par le système.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket::GetSockNameEx](#getsocknameex)

##  <a name="getsocknameex"></a>  CAsyncSocket::GetSockNameEx

Appelez cette fonction membre pour obtenir le nom local pour un socket (gère les adresses IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Paramètres

*rSocketAddress*<br/>
Référence à un `CString` objet qui reçoit une adresse IP de nombre en pointillés.

*rSocketPort*<br/>
Référence à un UINT qui stocke un port.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT le *lpSockAddrLen* argument n’est pas assez grand.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEINVAL le socket n’a pas été lié à une adresse avec `Bind`.

### <a name="remarks"></a>Notes

Cet appel est identique à [fonction membre CAsyncSocket::GetSockName](#getsockname) , à ceci près qu’il gère IPv6 résout également que les anciens protocoles.

Cet appel est particulièrement utile quand un `Connect` appel a été effectué sans effectuer un `Bind` tout d’abord ; cet appel fournit le seul moyen par lequel vous pouvez déterminer l’association locale qui a été définie par le système.

##  <a name="getsockopt"></a>  CAsyncSocket::GetSockOpt

Appelez cette fonction membre pour récupérer une option de socket.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Paramètres

*nOptionName*<br/>
L’option de socket pour lequel la valeur doit être récupéré.

*lpOptionValue*<br/>
Pointeur vers la mémoire tampon dans laquelle la valeur de l’option demandée doit être retourné. La valeur associée à l’option sélectionnée est retournée dans la mémoire tampon *lpOptionValue*. L’entier désigné par *lpOptionLen* doit contenir l’origine de la taille de cette mémoire tampon en octets ; et en retour, elle sera définie à la taille de la valeur retournée. Pour SO_LINGER, il s’agit de la taille d’un `LINGER` structure ; pour toutes les autres options, il sera la taille d’une valeur Booléenne ou une **int**, en fonction de l’option. Afficher la liste des options et leur taille dans la section Notes.

*lpOptionLen*<br/>
Un pointeur vers la taille de la *lpOptionValue* mémoire tampon en octets.

*nLevel*<br/>
Le niveau auquel l’option est définie ; Seuls les niveaux pris en charge sont SOL_SOCKET et IPPROTO_TCP.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Si une option n’a jamais été définie avec `SetSockOpt`, puis `GetSockOpt` retourne la valeur par défaut pour l’option. Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT le *lpOptionLen* argument n’est pas valide.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAENOPROTOOPT l’option est inconnu ou non pris en charge. En particulier, SO_BROADCAST n’est pas pris en charge sur les sockets de type SOCK_STREAM, tout en SO_ACCEPTCONN SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER et SO_OOBINLINE ne sont pas pris en charge sur les sockets de type SOCK_DGRAM.

- WSAENOTSOCK le descripteur n’est pas un socket.

### <a name="remarks"></a>Notes

`GetSockOpt` Récupère la valeur actuelle d’une option de socket associée à un socket de n’importe quel type, dans n’importe quel état et stocke le résultat dans *lpOptionValue*. Les options affectent les opérations de socket, notamment le routage de paquets, transfert de données hors bande et ainsi de suite.

Les options suivantes sont prises en charge pour `GetSockOpt`. Le Type identifie le type de données adressées par *lpOptionValue*. L’option TCP_NODELAY utilise IPPROTO_TCP niveau ; toutes les autres options utilisent niveau SOL_SOCKET.

|Value|Type|Signification|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Socket est à l’écoute.|
|SO_BROADCAST|BOOL|Socket est configuré pour la transmission de messages de diffusion.|
|SO_DEBUG|BOOL|Le débogage est activé.|
|SO_DONTLINGER|BOOL|Si la valeur est true, l’option SO_LINGER est désactivée.|
|SO_DONTROUTE|BOOL|Le routage est désactivé.|
|SO_ERROR|**int**|Récupérer l’état d’erreur et effacer.|
|SO_KEEPALIVE|BOOL|Des connexions persistantes sont envoyés.|
|SO_LINGER|`struct LINGER`|Retourne les options de persistance actuelle.|
|SO_OOBINLINE|BOOL|Données hors bande sont reçues dans le flux de données normal.|
|SO_RCVBUF|int|Taille de mémoire tampon pour reçoit.|
|SO_REUSEADDR|BOOL|Le socket peut être lié à une adresse qui est déjà en cours d’utilisation.|
|SO_SNDBUF|**int**|Taille de mémoire tampon pour envoie.|
|SO_TYPE|**int**|Le type du socket (par exemple, SOCK_STREAM).|
|TCP_NODELAY|BOOL|Désactive l'algorithme Nagle pour la fusion des envois.|

Options de Distribution BSD (Berkeley Software) non pris en charge pour `GetSockOpt` sont :

|Value|Type|Signification|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Limite inférieure de la réception.|
|SO_RCVTIMEO|**int**|Délai de réception.|
|SO_SNDLOWAT|**int**|Envoyer la limite inférieure.|
|SO_SNDTIMEO|**int**|Délai d’attente d’envoi.|
|IP_OPTIONS||Obtenir les options dans l’en-tête IP.|
|TCP_MAXSEG|**int**|Obtenir la taille de segment maximale de TCP.|

Appel `GetSockOpt` avec une option non prise en charge entraîne un code d’erreur de WSAENOPROTOOPT retourné à partir de `GetLastError`.

##  <a name="ioctl"></a>  CAsyncSocket::IOCtl

Appelez cette fonction membre pour contrôler le mode d’un socket.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Paramètres

*lCommand*<br/>
La commande à effectuer sur le socket.

*lpArgument*<br/>
Un pointeur vers un paramètre pour *lCommand*.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL *lCommand* n’est pas une commande valide, ou *lpArgument* n’est pas un paramètre acceptable pour *lCommand*, ou la commande n’est pas applicable au type de socket fournis .

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAENOTSOCK le descripteur n’est pas un socket.

### <a name="remarks"></a>Notes

Cette routine peut être utilisée sur n’importe quel socket dans n’importe quel état. Il est utilisé pour obtenir ou de récupérer les paramètres d’opération associées au socket, indépendamment du sous-système de protocole et les communications. Les commandes suivantes sont prises en charge :

- FIONBIO activer ou désactiver le mode non bloquant sur le socket. Le *lpArgument* paramètre pointe vers une `DWORD`, qui est différent de zéro si le mode non bloquant doit être activée et zéro si elle doit être désactivée. Si `AsyncSelect` a été émise sur un socket, puis toute tentative d’utilisation `IOCtl` pour définir le socket retour au mode blocage échoue avec WSAEINVAL. Pour définir le socket en mode blocage et éviter l’erreur WSAEINVAL, une application doit tout d’abord désactiver `AsyncSelect` en appelant `AsyncSelect` avec la *lEvent* paramètre égal à 0, puis appelez `IOCtl`.

- FIONREAD de déterminer le nombre maximal d’octets qui peut être lu avec un `Receive` appeler à partir de ce socket. Le *lpArgument* paramètre pointe vers une `DWORD` dans lequel `IOCtl` stocke le résultat. Si ce socket est de type SOCK_STREAM, FIONREAD retourne la quantité totale de données qui peuvent être lu dans un seul `Receive`; cela est normalement le même que la quantité totale de données en file d’attente sur le socket. Si ce socket est de type SOCK_DGRAM, FIONREAD retourne que la taille de la première datagramme en file d’attente sur le socket.

- SIOCATMARK déterminer si toutes les données hors bande a été lu. Cela s’applique uniquement à un socket de type SOCK_STREAM qui a été configuré pour la réception en ligne des données hors bande (SO_OOBINLINE). Si aucune donnée hors-bande n’est en attente à lire, l’opération retourne différente de zéro. Sinon, elle retourne 0 et la prochaine `Receive` ou `ReceiveFrom` effectuées sur le socket récupérera tout ou partie des données précédant la marque « » ; l’application doit utiliser l’opération SIOCATMARK pour déterminer si le reste des données. S’il existe des données normales précédant les terme « urgentes » données (out-of-band), elle sera reçue dans l’ordre. (Notez qu’un `Receive` ou `ReceiveFrom` sera ne mélangez jamais les données hors-bande et normales dans le même appel.) Le *lpArgument* paramètre pointe vers une `DWORD` dans lequel `IOCtl` stocke le résultat.

Cette fonction est un sous-ensemble de `ioctl()` tel qu’utilisé dans les sockets Berkeley. En particulier, il n’existe aucune commande qui est équivalent à FIOASYNC, tandis que SIOCATMARK est la commande uniquement de niveau socket qui est pris en charge.

##  <a name="listen"></a>  CAsyncSocket::Listen

Appelez cette fonction membre pour écouter les demandes de connexion entrantes.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Paramètres

*nConnectionBacklog*<br/>
La longueur maximale que peut atteindre la file d’attente des connexions en attente. Plage valide est comprise entre 1 et 5.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE une tentative a été effectuée à l’écoute sur une adresse en cours d’utilisation.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAEINVAL le socket n’a pas été lié avec `Bind` ou est déjà connecté.

- WSAEISCONN le socket est déjà connecté.

- WSAEMFILE aucun autre descripteur de fichier est disponibles.

- Espace de mémoire tampon WSAENOBUFS No est disponible.

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEOPNOTSUPP le socket référencé n’est pas un type qui prend en charge la `Listen` opération.

### <a name="remarks"></a>Notes

Pour accepter les connexions, le socket est d’abord créé avec `Create`, un retard de traitement pour les connexions entrantes est spécifié avec `Listen`, et ensuite les connexions sont acceptées avec `Accept`. `Listen` s’applique uniquement aux sockets qui prennent en charge les connexions, autrement dit, ceux de type SOCK_STREAM. Ce socket est placé en mode « passif » où les connexions entrantes sont acceptées et en file d’attente en attente d’acceptation par le processus.

Cette fonction est généralement utilisée par les serveurs (ou n’importe quelle application qui souhaite accepter les connexions) qui peut avoir plusieurs demandes de connexion à la fois : si une demande de connexion arrive avec la file d’attente est complète, le client recevra une erreur avec une indication de WSAECONNREFUSED.

`Listen` tente de continuer à fonctionner rationnelle lorsqu’il n’y a aucun port disponible (descripteurs). Il accepte les connexions jusqu'à ce que la file d’attente est vide. Si les ports sont disponibles, un appel ultérieur à `Listen` ou `Accept` sera rechargement de la file d’attente actuelle ou plus récente » backlog, » si possible et reprend l’écoute pour les connexions entrantes.

##  <a name="m_hsocket"></a>  CAsyncSocket::m_hSocket

Contient le handle SOCKET pour le socket encapsulé par cet `CAsyncSocket` objet.

```
SOCKET m_hSocket;
```

##  <a name="onaccept"></a>  CAsyncSocket::OnAccept

Appelé par l’infrastructure pour avertir un socket d’écoute qu’il peut accepter les demandes de connexion en attente en appelant le [Accept](#accept) fonction membre.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur un socket. Les codes d’erreur suivant s’applique à la `OnAccept` fonction membre :

- **0** la fonction exécutée avec succès.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : Notifications de Socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onclose"></a>  CAsyncSocket::OnClose

Appelé par l’infrastructure pour informer ce socket que le socket connecté est fermé par son processus.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur un socket. Codes d’erreur suivants s’appliquent à la `OnClose` fonction membre :

- **0** la fonction exécutée avec succès.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAECONNRESET la connexion a été réinitialisé par le côté distant.

- WSAECONNABORTED la connexion a été abandonnée en raison d’une défaillance ou de délai d’attente.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : Notifications de Socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onconnect"></a>  CAsyncSocket::OnConnect

Appelé par l’infrastructure pour notifier au socket de connexion que sa tentative de connexion est terminée avec succès ou erreur.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur un socket. Codes d’erreur suivants s’appliquent à la `OnConnect` fonction membre :

- **0** la fonction exécutée avec succès.

- WSAEADDRINUSE l’adresse spécifiée est déjà en cours d’utilisation.

- WSAEADDRNOTAVAIL l’adresse spécifiée n’est pas disponible à partir de l’ordinateur local.

- Adresses WSAEAFNOSUPPORT dans la famille spécifiée ne peut pas être utilisés avec ce socket.

- WSAECONNREFUSED la tentative de connexion a été rejetée.

- Adresse de destination WSAEDESTADDRREQ A est requise.

- WSAEFAULT le *lpSockAddrLen* argument est incorrect.

- WSAEINVAL le socket est déjà lié à une adresse.

- WSAEISCONN le socket est déjà connecté.

- WSAEMFILE aucun autre descripteur de fichier est disponibles.

- WSAENETUNREACH le réseau ne peut pas être atteint à partir de cet hôte pour l’instant.

- Espace de mémoire tampon WSAENOBUFS No est disponible. Le socket n’est pas accessible.

- WSAENOTCONN le socket n’est pas connecté.

- WSAENOTSOCK le descripteur est un fichier, pas un socket.

- WSAETIMEDOUT la tentative de connexion a expiré sans avoir à établir une connexion.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Dans [CSocket](../../mfc/reference/csocket-class.md), le `OnConnect` fonction de notification n’est jamais appelée. Pour les connexions, il suffit d’appeler `Connect`, qui retournera l’issue de la connexion (avec succès ou erreur). Gestion des notifications de connexion est un détail d’implémentation MFC.

Pour plus d’informations, consultez [Windows Sockets : Notifications de Socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

##  <a name="onoutofbanddata"></a>  CAsyncSocket::OnOutOfBandData

Appelé par l’infrastructure pour avertir le socket de réception du socket émetteur est hors-bande des données à envoyer.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur un socket. Codes d’erreur suivants s’appliquent à la `OnOutOfBandData` fonction membre :

- **0** la fonction exécutée avec succès.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Données hors bande sont un canal logiquement indépendant qui est associé à chaque paire de sockets connectées de type SOCK_STREAM. Le canal est généralement utilisé pour envoyer des données urgentes.

MFC prend en charge les données hors bande, mais les utilisateurs de classe `CAsyncSocket` est déconseillé de l’utiliser. Le plus simple consiste à créer un deuxième socket pour transmettre ces données. Pour plus d’informations sur les données hors bande, consultez [Windows Sockets : Notifications de Socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onreceive"></a>  CAsyncSocket::OnReceive

Appelé par l’infrastructure pour informer ce socket qu’il y a des données dans la mémoire tampon qui peut être récupérée en appelant le `Receive` fonction membre.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur un socket. Codes d’erreur suivants s’appliquent à la `OnReceive` fonction membre :

- **0** la fonction exécutée avec succès.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : Notifications de Socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

##  <a name="onsend"></a>  CAsyncSocket::OnSend

Appelé par l’infrastructure pour avertir le socket qu’il peut maintenant envoyer des données en appelant le `Send` fonction membre.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur un socket. Codes d’erreur suivants s’appliquent à la `OnSend` fonction membre :

- **0** la fonction exécutée avec succès.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : Notifications de Socket](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

##  <a name="operator_eq"></a>  CAsyncSocket::operator =

Assigne une nouvelle valeur à un `CAsyncSocket` objet.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Une référence à un existant `CAsyncSocket` objet.

### <a name="remarks"></a>Notes

Appelez cette fonction pour copier un existant `CAsyncSocket` objet vers un autre `CAsyncSocket` objet.

##  <a name="operator_socket"></a>  CAsyncSocket::operator SOCKET

Utilisez cet opérateur pour récupérer le handle SOCKET de la `CAsyncSocket` objet.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, le handle de l’objet SOCKET ; Sinon, NULL.

### <a name="remarks"></a>Notes

Vous pouvez utiliser le handle d’appeler directement les API de Windows.

##  <a name="receive"></a>  CAsyncSocket::Receive

Appelez cette fonction membre pour recevoir des données à partir d’un socket.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Une mémoire tampon pour les données entrantes.

*nBufLen*<br/>
La longueur de *lpBuf* en octets.

*nIndicateurs*<br/>
Spécifie le mode dans lequel l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le *nIndicateurs* paramètre. Ce dernier est construit en combinant les valeurs suivantes avec le C++ **ou** opérateur :

- MSG_PEEK lire les données entrantes. Les données sont copiées dans la mémoire tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB traiter les données de hors-bande.

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `Receive` retourne le nombre d’octets reçus. Si la connexion a été fermée, elle retourne 0. Sinon, une valeur de SOCKET_ERROR est retournée et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAENOTCONN le socket n’est pas connecté.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifiée, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `Receive` sur un socket après `ShutDown` a été appelée avec *nHow* définie sur 0 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et `Receive` susceptibles de bloquer l’opération.

- WSAEMSGSIZE le datagramme était trop grand pour tenir dans la mémoire tampon spécifiée et a été tronqué.

- WSAEINVAL le socket n’a pas été lié avec `Bind`.

- WSAECONNABORTED le circuit virtuel a été abandonnée en raison d’une défaillance ou de délai d’attente.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour les flux de données connectée ou sockets datagramme et est utilisée pour lire les données entrantes.

Pour les sockets de type SOCK_STREAM, toutes les informations que n’est actuellement disponible jusqu'à la taille de la mémoire tampon fournie sont retournées. Si le socket a été configuré pour la réception dans la ligne de données hors bande (option de socket SO_OOBINLINE) et out-of-band données non lues, seules les données hors bande seront affichera. L’application peut utiliser le `IOCtlSIOCATMARK` option ou [OnOutOfBandData](#onoutofbanddata) pour déterminer si toutes les données plus out-of-band restent à lire.

Pour les sockets datagramme, les données sont extraites à partir de la première datagramme en file d’attente, jusqu'à la taille de la mémoire tampon fournie. Si le datagramme est supérieur à la mémoire tampon fournie, la mémoire tampon est remplie avec la première partie du datagramme, les données excédentaires sont perdues, et `Receive` retourne un SOCKET_ERROR avec le code d’erreur valeur WSAEMSGSIZE. Si aucune données entrantes ne sont disponibles sur le socket, une valeur de SOCKET_ERROR est retournée avec le code d’erreur WSAEWOULDBLOCK la valeur. Le [OnReceive](#onreceive) fonction de rappel peut être utilisée pour déterminer quand davantage de données arrivent.

Si le socket est de type SOCK_STREAM et le côté distant a fermé la connexion correctement, un `Receive` se termine immédiatement avec 0 octets reçus. Si la connexion a été réinitialisée, un `Receive` échoue avec l’erreur WSAECONNRESET.

`Receive` doit être appelée qu’une seule fois pour chaque fois [CAsyncSocket::OnReceive](#onreceive) est appelée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAsyncSocket::OnReceive](#onreceive).

##  <a name="receivefrom"></a>  CAsyncSocket::ReceiveFrom

Appelez cette fonction membre pour recevoir un datagramme et stocke l’adresse source dans le [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure ou dans *rSocketAddress*.

```
int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);


int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Une mémoire tampon pour les données entrantes.

*nBufLen*<br/>
La longueur de *lpBuf* en octets.

*rSocketAddress*<br/>
Référence à un `CString` objet qui reçoit une adresse IP de nombre en pointillés.

*rSocketPort*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Un pointeur vers un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure qui contient l’adresse source au moment du retour.

*lpSockAddrLen*<br/>
Un pointeur vers la longueur de l’adresse source dans *lpSockAddr* en octets.

*nIndicateurs*<br/>
Spécifie le mode dans lequel l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le *nIndicateurs* paramètre. Ce dernier est construit en combinant les valeurs suivantes avec le C++ **ou** opérateur :

- MSG_PEEK lire les données entrantes. Les données sont copiées dans la mémoire tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB traiter les données de hors-bande.

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `ReceiveFrom` retourne le nombre d’octets reçus. Si la connexion a été fermée, elle retourne 0. Sinon, une valeur de SOCKET_ERROR est retournée et un code d’erreur spécifique peut être récupéré en appelant `GetLastError`. Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT le *lpSockAddrLen* argument n’est pas valide : le *lpSockAddr* tampon est trop petite pour contenir l’adresse de l’homologue.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAEINVAL le socket n’a pas été lié avec `Bind`.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifiée, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `ReceiveFrom` sur un socket après `ShutDown` a été appelée avec *nHow* définie sur 0 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et `ReceiveFrom` susceptibles de bloquer l’opération.

- WSAEMSGSIZE le datagramme était trop grand pour tenir dans la mémoire tampon spécifiée et a été tronqué.

- WSAECONNABORTED le circuit virtuel a été abandonnée en raison d’une défaillance ou de délai d’attente.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour lire les données entrantes sur un socket (éventuellement connecté) et de capturer l’adresse à partir de laquelle les données a été envoyées.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket::ReceiveFromEx](#receivefromex).

Pour les sockets de type SOCK_STREAM, toutes les informations que n’est actuellement disponible jusqu'à la taille de la mémoire tampon fournie sont retournées. Si le socket a été configuré pour la réception dans la ligne de données hors bande (option de socket SO_OOBINLINE) et out-of-band données non lues, seules les données hors bande seront affichera. L’application peut utiliser le `IOCtlSIOCATMARK` option ou `OnOutOfBandData` pour déterminer si toutes les données plus out-of-band restent à lire. Le *lpSockAddr* et *lpSockAddrLen* paramètres sont ignorés pour les sockets SOCK_STREAM.

Pour les sockets datagramme, les données sont extraites à partir de la première datagramme en file d’attente, jusqu'à la taille de la mémoire tampon fournie. Si le datagramme est supérieur à la mémoire tampon fournie, la mémoire tampon est remplie avec la première partie du message, les données excédentaires sont perdues, et `ReceiveFrom` retourne un SOCKET_ERROR avec le code d’erreur valeur WSAEMSGSIZE.

Si *lpSockAddr* est différent de zéro et le socket est de type SOCK_DGRAM, l’adresse réseau du socket qui a envoyé les données est copié correspondant [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure. La valeur vers laquelle pointe *lpSockAddrLen* est initialisée à la taille de cette structure et est modifié en retour pour indiquer la taille réelle de l’adresse qui y sont stocké. Si aucune données entrantes ne sont disponibles sur le socket, le `ReceiveFrom` appel attend des données arrivent, sauf si le socket est non bloquant. Dans ce cas, une valeur de SOCKET_ERROR est retournée avec le code d’erreur WSAEWOULDBLOCK la valeur. Le `OnReceive` rappel peut être utilisé pour déterminer quand davantage de données arrivent.

Si le socket est de type SOCK_STREAM et le côté distant a fermé la connexion correctement, un `ReceiveFrom` se termine immédiatement avec 0 octets reçus.

##  <a name="receivefromex"></a>  CAsyncSocket::ReceiveFromEx

Appelez cette fonction membre pour recevoir un datagramme et stocke l’adresse source dans le [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure ou dans *rSocketAddress* (gère les adresses IPv6).

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Une mémoire tampon pour les données entrantes.

*nBufLen*<br/>
La longueur de *lpBuf* en octets.

*rSocketAddress*<br/>
Référence à un `CString` objet qui reçoit une adresse IP de nombre en pointillés.

*rSocketPort*<br/>
Référence à un UINT qui stocke un port.

*nIndicateurs*<br/>
Spécifie le mode dans lequel l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le *nIndicateurs* paramètre. Ce dernier est construit en combinant les valeurs suivantes avec le C++ **ou** opérateur :

- MSG_PEEK lire les données entrantes. Les données sont copiées dans la mémoire tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB traiter les données de hors-bande.

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `ReceiveFromEx` retourne le nombre d’octets reçus. Si la connexion a été fermée, elle retourne 0. Sinon, une valeur de SOCKET_ERROR est retournée et un code d’erreur spécifique peut être récupéré en appelant `GetLastError`. Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT le *lpSockAddrLen* argument n’est pas valide : le *lpSockAddr* tampon est trop petite pour contenir l’adresse de l’homologue.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAEINVAL le socket n’a pas été lié avec `Bind`.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifiée, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `ReceiveFromEx` sur un socket après `ShutDown` a été appelée avec *nHow* définie sur 0 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et `ReceiveFromEx` susceptibles de bloquer l’opération.

- WSAEMSGSIZE le datagramme était trop grand pour tenir dans la mémoire tampon spécifiée et a été tronqué.

- WSAECONNABORTED le circuit virtuel a été abandonnée en raison d’une défaillance ou de délai d’attente.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour lire les données entrantes sur un socket (éventuellement connecté) et de capturer l’adresse à partir de laquelle les données a été envoyées.

Cette fonction est identique à [CAsyncSocket::ReceiveFrom](#receivefrom) , à ceci près qu’il gère IPv6 résout également que les anciens protocoles.

Pour les sockets de type SOCK_STREAM, toutes les informations que n’est actuellement disponible jusqu'à la taille de la mémoire tampon fournie sont retournées. Si le socket a été configuré pour la réception dans la ligne de données hors bande (option de socket SO_OOBINLINE) et out-of-band données non lues, seules les données hors bande seront affichera. L’application peut utiliser le `IOCtlSIOCATMARK` option ou `OnOutOfBandData` pour déterminer si toutes les données plus out-of-band restent à lire. Le *lpSockAddr* et *lpSockAddrLen* paramètres sont ignorés pour les sockets SOCK_STREAM.

Pour les sockets datagramme, les données sont extraites à partir de la première datagramme en file d’attente, jusqu'à la taille de la mémoire tampon fournie. Si le datagramme est supérieur à la mémoire tampon fournie, la mémoire tampon est remplie avec la première partie du message, les données excédentaires sont perdues, et `ReceiveFromEx` retourne un SOCKET_ERROR avec le code d’erreur valeur WSAEMSGSIZE.

Si *lpSockAddr* est différent de zéro et le socket est de type SOCK_DGRAM, l’adresse réseau du socket qui a envoyé les données est copié correspondant [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure. La valeur vers laquelle pointe *lpSockAddrLen* est initialisée à la taille de cette structure et est modifié en retour pour indiquer la taille réelle de l’adresse qui y sont stocké. Si aucune données entrantes ne sont disponibles sur le socket, le `ReceiveFromEx` appel attend des données arrivent, sauf si le socket est non bloquant. Dans ce cas, une valeur de SOCKET_ERROR est retournée avec le code d’erreur WSAEWOULDBLOCK la valeur. Le `OnReceive` rappel peut être utilisé pour déterminer quand davantage de données arrivent.

Si le socket est de type SOCK_STREAM et le côté distant a fermé la connexion correctement, un `ReceiveFromEx` se termine immédiatement avec 0 octets reçus.

##  <a name="send"></a>  CAsyncSocket::Send

Appelez cette fonction membre pour envoyer des données sur un socket connecté.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Une mémoire tampon contenant les données à transmettre.

*nBufLen*<br/>
La longueur des données dans *lpBuf* en octets.

*nIndicateurs*<br/>
Spécifie le mode dans lequel l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le *nIndicateurs* paramètre. Ce dernier est construit en combinant les valeurs suivantes avec le C++ **ou** opérateur :

- MSG_DONTROUTE Spécifie que les données ne doivent pas être soumis à routage. Un fournisseur Windows Sockets peut choisir d’ignorer cet indicateur.

- MSG_OOB envoyer hors-bande de données (SOCK_STREAM uniquement).

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `Send` retourne le nombre total de caractères envoyés. (Notez que cela peut être inférieur au nombre indiqué par *nBufLen*.) Sinon, une valeur de SOCKET_ERROR est retournée et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES l’adresse demandée est une adresse de diffusion, mais l’indicateur approprié n’a pas été définie.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAEFAULT le *lpBuf* argument n’est pas une partie valide de l’espace d’adressage utilisateur.

- WSAENETRESET la connexion doit être réinitialisé, car l’implémentation Windows Sockets abandonnée.

- Implémentation WSAENOBUFS The Windows Sockets signale un interblocage de la mémoire tampon.

- WSAENOTCONN le socket n’est pas connecté.

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifiée, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `Send` sur un socket après `ShutDown` a été appelée avec *nHow* définie sur 1 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et bloque l’opération demandée.

- WSAEMSGSIZE le socket est de type SOCK_DGRAM, et le datagramme est supérieur à la valeur maximale prise en charge par l’implémentation Windows Sockets.

- WSAEINVAL le socket n’a pas été lié avec `Bind`.

- WSAECONNABORTED le circuit virtuel a été abandonnée en raison d’une défaillance ou de délai d’attente.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

`Send` est utilisé pour écrire des données sortantes sur le flux connectés ou les sockets datagramme. Pour les sockets datagramme, être vigilant pour ne pas dépasser la taille maximale du paquet IP des sous-réseaux sous-jacente, qui est fourni par le `iMaxUdpDg` élément dans le [WSADATA](../../mfc/reference/wsadata-structure.md) structure retournée par `AfxSocketInit`. Si les données sont trop longues à traverser atomiquement le protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée `GetLastError`, et aucune donnée n’est transmise.

Notez que la réussite de socket de datagramme un `Send` n’indique pas que les données a été correctement remises.

Sur `CAsyncSocket` objets de type SOCK_STREAM, le nombre d’octets écrits peut être comprise entre 1 et la longueur demandée, en fonction de la disponibilité de mémoire tampon sur les hôtes locales et à l’étrangers.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAsyncSocket::OnSend](#onsend).

##  <a name="sendto"></a>  CAsyncSocket::SendTo

Appelez cette fonction membre pour envoyer des données vers une destination spécifique.

```
int SendTo(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);


int SendTo(
    const void* lpBuf,
    int nBufLen,
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Une mémoire tampon contenant les données à transmettre.

*nBufLen*<br/>
La longueur des données dans *lpBuf* en octets.

*nHostPort*<br/>
Le port identifiant l’application de socket.

*lpszHostAddress*<br/>
L’adresse réseau du socket à laquelle cet objet est connecté : un nom d’ordinateur tel que « FTP.Microsoft.com », ou un nombre en pointillés tels que « 128.56.22.8 ».

*nIndicateurs*<br/>
Spécifie le mode dans lequel l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le *nIndicateurs* paramètre. Ce dernier est construit en combinant les valeurs suivantes avec le C++ **ou** opérateur :

- MSG_DONTROUTE Spécifie que les données ne doivent pas être soumis à routage. Un fournisseur Windows Sockets peut choisir d’ignorer cet indicateur.

- MSG_OOB envoyer hors-bande de données (SOCK_STREAM uniquement).

*lpSockAddr*<br/>
Un pointeur vers un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure qui contient l’adresse du socket cible.

*nSockAddrLen*<br/>
La longueur de l’adresse dans *lpSockAddr* en octets.

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `SendTo` retourne le nombre total de caractères envoyés. (Notez que cela peut être inférieur au nombre indiqué par *nBufLen*.) Sinon, une valeur de SOCKET_ERROR est retournée et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES l’adresse demandée est une adresse de diffusion, mais l’indicateur approprié n’a pas été définie.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAEFAULT le *lpBuf* ou *lpSockAddr* paramètres ne font pas partie de l’espace d’adressage utilisateur, ou le *lpSockAddr* argument est trop faible (inférieur à la taille d’un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure).

- WSAEINVAL le nom d’hôte n’est pas valide.

- WSAENETRESET la connexion doit être réinitialisé, car l’implémentation Windows Sockets abandonnée.

- Implémentation WSAENOBUFS The Windows Sockets signale un interblocage de la mémoire tampon.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifiée, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `SendTo` sur un socket après `ShutDown` a été appelée avec *nHow* définie sur 1 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et bloque l’opération demandée.

- WSAEMSGSIZE le socket est de type SOCK_DGRAM, et le datagramme est supérieur à la valeur maximale prise en charge par l’implémentation Windows Sockets.

- WSAECONNABORTED le circuit virtuel a été abandonnée en raison d’une défaillance ou de délai d’attente.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

- WSAEADDRNOTAVAIL l’adresse spécifiée n’est pas disponible à partir de l’ordinateur local.

- Adresses WSAEAFNOSUPPORT dans la famille spécifiée ne peut pas être utilisés avec ce socket.

- Adresse de destination WSAEDESTADDRREQ A est requise.

- WSAENETUNREACH le réseau ne peut pas être atteint à partir de cet hôte pour l’instant.

### <a name="remarks"></a>Notes

`SendTo` est utilisé sur les sockets datagramme ou un flux de données et est utilisé pour écrire des données sortantes sur un socket. Pour les sockets datagramme, être vigilant pour ne pas dépasser la taille maximale du paquet IP des sous-réseaux sous-jacente, qui est fourni par le `iMaxUdpDg` élément dans le [WSADATA](../../mfc/reference/wsadata-structure.md) structure remplis par [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si les données sont trop longues à traverser atomiquement le protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée, et aucune donnée n’est transmise.

Notez que la réussite d’un `SendTo` n’indique pas que les données a été correctement remises.

`SendTo` est utilisé uniquement sur un socket SOCK_DGRAM pour envoyer un datagramme à un socket spécifique identifié par le *lpSockAddr* paramètre.

Pour envoyer une diffusion (sur un SOCK_DGRAM uniquement), l’adresse dans le *lpSockAddr* paramètre doit être construit à l’aide de l’adresse IP spéciale INADDR_BROADCAST (défini dans le fichier d’en-tête Windows Sockets WINSOCK. (H) avec le numéro de port souhaité. Ou, si le *lpszHostAddress* paramètre est NULL, le socket est configuré pour la diffusion. Il est généralement déconseillé pour un datagramme diffusé à dépasser la taille à laquelle la fragmentation peut se produire, ce qui implique que la partie données du datagramme (à l’exclusion des en-têtes) ne doit pas dépasser 512 octets.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket::SendToEx](#sendtoex).

##  <a name="sendtoex"></a>  CAsyncSocket::SendToEx

Appelez cette fonction membre pour envoyer des données vers une destination spécifique (gère les adresses IPv6).

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Une mémoire tampon contenant les données à transmettre.

*nBufLen*<br/>
La longueur des données dans *lpBuf* en octets.

*nHostPort*<br/>
Le port identifiant l’application de socket.

*lpszHostAddress*<br/>
L’adresse réseau du socket à laquelle cet objet est connecté : un nom d’ordinateur tel que « FTP.Microsoft.com », ou un nombre en pointillés tels que « 128.56.22.8 ».

*nIndicateurs*<br/>
Spécifie le mode dans lequel l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le *nIndicateurs* paramètre. Ce dernier est construit en combinant les valeurs suivantes avec le C++ **ou** opérateur :

- MSG_DONTROUTE Spécifie que les données ne doivent pas être soumis à routage. Un fournisseur Windows Sockets peut choisir d’ignorer cet indicateur.

- MSG_OOB envoyer hors-bande de données (SOCK_STREAM uniquement).

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `SendToEx` retourne le nombre total de caractères envoyés. (Notez que cela peut être inférieur au nombre indiqué par *nBufLen*.) Sinon, une valeur de SOCKET_ERROR est retournée et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES l’adresse demandée est une adresse de diffusion, mais l’indicateur approprié n’a pas été définie.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAEFAULT le *lpBuf* ou *lpSockAddr* paramètres ne font pas partie de l’espace d’adressage utilisateur, ou le *lpSockAddr* argument est trop faible (inférieur à la taille d’un [SOCKADDR](../../mfc/reference/sockaddr-structure.md) structure).

- WSAEINVAL le nom d’hôte n’est pas valide.

- WSAENETRESET la connexion doit être réinitialisé, car l’implémentation Windows Sockets abandonnée.

- Implémentation WSAENOBUFS The Windows Sockets signale un interblocage de la mémoire tampon.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifiée, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `SendToEx` sur un socket après `ShutDown` a été appelée avec *nHow* définie sur 1 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et bloque l’opération demandée.

- WSAEMSGSIZE le socket est de type SOCK_DGRAM, et le datagramme est supérieur à la valeur maximale prise en charge par l’implémentation Windows Sockets.

- WSAECONNABORTED le circuit virtuel a été abandonnée en raison d’une défaillance ou de délai d’attente.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

- WSAEADDRNOTAVAIL l’adresse spécifiée n’est pas disponible à partir de l’ordinateur local.

- Adresses WSAEAFNOSUPPORT dans la famille spécifiée ne peut pas être utilisés avec ce socket.

- Adresse de destination WSAEDESTADDRREQ A est requise.

- WSAENETUNREACH le réseau ne peut pas être atteint à partir de cet hôte pour l’instant.

### <a name="remarks"></a>Notes

Cette méthode est identique à [CAsyncSocket::SendTo](#sendto) , à ceci près qu’il gère IPv6 résout également que les anciens protocoles.

`SendToEx` est utilisé sur les sockets datagramme ou un flux de données et est utilisé pour écrire des données sortantes sur un socket. Pour les sockets datagramme, être vigilant pour ne pas dépasser la taille maximale du paquet IP des sous-réseaux sous-jacente, qui est fourni par le `iMaxUdpDg` élément dans le [WSADATA](../../mfc/reference/wsadata-structure.md) structure remplis par [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si les données sont trop longues à traverser atomiquement le protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée, et aucune donnée n’est transmise.

Notez que la réussite d’un `SendToEx` n’indique pas que les données a été correctement remises.

`SendToEx` est utilisé uniquement sur un socket SOCK_DGRAM pour envoyer un datagramme à un socket spécifique identifié par le *lpSockAddr* paramètre.

Pour envoyer une diffusion (sur un SOCK_DGRAM uniquement), l’adresse dans le *lpSockAddr* paramètre doit être construit à l’aide de l’adresse IP spéciale INADDR_BROADCAST (défini dans le fichier d’en-tête Windows Sockets WINSOCK. (H) avec le numéro de port souhaité. Ou, si le *lpszHostAddress* paramètre est NULL, le socket est configuré pour la diffusion. Il est généralement déconseillé pour un datagramme diffusé à dépasser la taille à laquelle la fragmentation peut se produire, ce qui implique que la partie données du datagramme (à l’exclusion des en-têtes) ne doit pas dépasser 512 octets.

##  <a name="setsockopt"></a>  CAsyncSocket::SetSockOpt

Appelez cette fonction membre pour définir une option de socket.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Paramètres

*nOptionName*<br/>
L’option de socket pour lequel la valeur doit être défini.

*lpOptionValue*<br/>
Pointeur vers la mémoire tampon dans laquelle la valeur de l’option demandée est fournie.

*nOptionLen*<br/>
La taille de la *lpOptionValue* mémoire tampon en octets.

*nLevel*<br/>
Le niveau auquel l’option est définie ; Seuls les niveaux pris en charge sont SOL_SOCKET et IPPROTO_TCP.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *lpOptionValue* n’est pas dans une partie de l’espace d’adressage de processus valide.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAEINVAL *nLevel* n’est pas valide, ou les informations contenues dans *lpOptionValue* n’est pas valide.

- WSAENETRESET connexion a expiré SO_KEEPALIVE est définie.

- WSAENOPROTOOPT l’option est inconnu ou non pris en charge. En particulier, SO_BROADCAST n’est pas pris en charge sur les sockets de type SOCK_STREAM, tout en SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER et SO_OOBINLINE ne sont pas pris en charge sur les sockets de type SOCK_DGRAM.

- WSAENOTCONN connexion a été réinitialisée lorsque SO_KEEPALIVE est définie.

- WSAENOTSOCK le descripteur n’est pas un socket.

### <a name="remarks"></a>Notes

`SetSockOpt` définit la valeur actuelle d’une option de socket associée à un socket de n’importe quel type, dans n’importe quel état. Bien que les options peuvent exister à plusieurs niveaux de protocole, cette spécification définit uniquement les options qui existent au niveau du socket « supérieure ». Les options affectent les opérations de socket, par exemple si les données expédiées sont reçues dans le flux de données normale, si les messages de diffusion peuvent être envoyés sur le socket et ainsi de suite.

Il existe deux types d’options de socket : options booléennes qui activent ou désactivent une fonctionnalité ou un comportement et options qui nécessitent une valeur entière ou une structure. Pour activer une option booléenne, *lpOptionValue* pointe vers un entier différent de zéro. Pour désactiver l’option *lpOptionValue* pointe vers un entier égal à zéro. *nOptionLen* doit être égale à `sizeof(BOOL)` options booléennes. Pour les autres options, *lpOptionValue* pointe vers l’entier ou une structure qui contient la valeur souhaitée pour l’option, et *nOptionLen* est la longueur de l’entier ou la structure.

SO_LINGER contrôle l’action effectuée lorsque les données non envoyées sont en file d’attente sur un socket et le `Close` fonction est appelée pour fermer le socket.

Par défaut, un socket ne peut pas être lié (consultez [lier](#bind)) à une adresse locale qui est déjà en cours d’utilisation. Parfois, cependant, il peut être souhaitable de « réutiliser » une adresse de cette façon. Étant donné que chaque connexion est identifiée par la combinaison des adresses locales et distantes, il n’existe aucun problème avec un deux sockets liés à la même adresse locale, que les adresses à distance sont différents.

Pour informer l’implémentation Windows Sockets qui un `Bind` appel sur un socket ne doit pas être rejeté, car l’adresse souhaité est déjà en cours d’utilisation par un autre socket, l’application doit définir l’option de socket SO_REUSEADDR pour le socket avant d’émettre la `Bind` appeler. Notez que l’option est interprétée uniquement au moment de la `Bind` appeler : il est donc inutile (mais sans incidence) pour définir l’option sur un socket qui ne doit ne pas être lié à une adresse existante, et en définissant ou la réinitialisation de l’option après la `Bind` appel a aucun effet sur ce socket ou un autre.

Une application peut demander que l’implémentation Windows Sockets activer l’utilisation de paquets « keep-alive » sur les connexions de protocole TCP (Transmission Control) en activant l’option de socket SO_KEEPALIVE. Une implémentation Windows Sockets devez prend pas en charge l’utilisation de connexions persistantes : le cas échéant, la sémantique de précision sont spécifiques à l’implémentation, mais doit être conforme à la section 4.2.3.6 de la RFC 1122 : « configuration requise pour les hôtes Internet, les couches de Communication. » Si une connexion est supprimée en tant que le résultat de « persistantes » le code d’erreur WSAENETRESET est retournée pour tous les appels en cours d’exécution sur le socket, et les appels suivants échoueront avec WSAENOTCONN.

L’option TCP_NODELAY désactive l’algorithme Nagle. L’algorithme Nagle est utilisé pour réduire le nombre de petits paquets envoyés par un hôte en mémoire tampon d’envoi sans accusé de réception de données jusqu'à ce qu’un paquet en taille réelle peut être envoyé. Toutefois, pour certaines applications, cet algorithme peut nuire aux performances et TCP_NODELAY peut être utilisé pour la désactiver. Les rédacteurs d’application ne doivent pas défini TCP_NODELAY, sauf si l’impact de cette opération est donc bien assimilés et souhaitée, étant donné que le paramètre TCP_NODELAY peut avoir un impact négatif sur les performances réseau. TCP_NODELAY est la seule option de socket qui utilise le niveau IPPROTO_TCP ; prise en charge toutes les autres options utilisent niveau SOL_SOCKET.

Certaines implémentations de l’approvisionnement de Windows Sockets sortent des informations de débogage si l’option SO_DEBUG est définie par une application.

Les options suivantes sont prises en charge pour `SetSockOpt`. Le Type identifie le type de données adressées par *lpOptionValue*.

|Value|Type|Signification|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|Autoriser la transmission de messages de diffusion sur le socket.|
|SO_DEBUG|BOOL|Enregistrer les informations de débogage.|
|SO_DONTLINGER|BOOL|Ne bloquez pas `Close` en attente pour envoi de données non envoyées. Définition de cette option revient à définir SO_LINGER avec `l_onoff` défini à zéro.|
|SO_DONTROUTE|BOOL|Ne pas acheminer : envoi directement à l’interface.|
|SO_KEEPALIVE|BOOL|Envoyer des connexions persistantes.|
|SO_LINGER|`struct LINGER`|Attendre pendant la `Close` si non envoyés de données sont présentes.|
|SO_OOBINLINE|BOOL|Permet de recevoir des données de hors-bande dans le flux de données normal.|
|SO_RCVBUF|**int**|Spécifiez reçoit de la taille de mémoire tampon pour.|
|SO_REUSEADDR|BOOL|Autoriser le socket doit être lié à une adresse qui est déjà en cours d’utilisation. (Consultez [lier](#bind).)|
|SO_SNDBUF|**int**|Spécifiez la taille de mémoire tampon pour l’envoi.|
|TCP_NODELAY|BOOL|Désactive l'algorithme Nagle pour la fusion des envois.|

Options de Distribution BSD (Berkeley Software) non pris en charge pour `SetSockOpt` sont :

|Value|Type|Signification|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|L’écoute de socket|
|SO_ERROR|**int**|Obtenir l’état d’erreur et effacer.|
|SO_RCVLOWAT|**int**|Limite inférieure de la réception.|
|SO_RCVTIMEO|**int**|Délai de réception|
|SO_SNDLOWAT|**int**|Envoyer la limite inférieure.|
|SO_SNDTIMEO|**int**|Délai d’attente d’envoi.|
|SO_TYPE|**int**|Type du socket.|
|IP_OPTIONS||Champ d’options SET dans l’en-tête IP.|

##  <a name="shutdown"></a>  CAsyncSocket::ShutDown

Appel de cette fonction membre pour désactiver envoie, reçoit, ou les deux sur le socket.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Paramètres

*nHow*<br/>
Un indicateur qui décrit les types d’opération sera plus autorisé, à l’aide de valeurs énumérées suivantes :

- **reçoit = 0**

- **envoie = 1**

- **à la fois = 2**

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED A réussi [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) doit se produire avant d’utiliser cette API.

- Implémentation de WSAENETDOWN The Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL *nHow* n’est pas valide.

- Opération de Windows Sockets blocage WSAEINPROGRESS A est en cours.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un socket.

### <a name="remarks"></a>Notes

`ShutDown` est utilisé sur tous les types de sockets pour désactiver la réception, transmission ou les deux. Si *nHow* est 0, reçoit suivantes sur le socket n’est pas autorisé. Cela n’a aucun effet sur les couches de protocole inférieures.

Pour protocole TCP (Transmission Control), la fenêtre TCP n’est pas modifiée et les données entrantes seront acceptées (mais pas accusé de réception) jusqu'à l’épuisement de la fenêtre. Pour protocole UDP (User Datagram), les datagrammes entrants sont acceptés et en file d’attente. Dans aucun cas un paquet d’erreur ICMP doit être généré. Si *nHow* est 1, envoie suivantes n’est pas autorisées. Pour les sockets TCP, vous recevrez un FIN. Paramètre *nHow* 2 désactive les envois et reçoit comme décrit ci-dessus.

Notez que `ShutDown` ne pas fermer le socket et les ressources jointes au socket ne seront pas libérées jusqu'à ce que `Close` est appelée. Une application ne doit pas dépendre de la possibilité de réutiliser un socket après que qu’il a été arrêté. En particulier, une implémentation Windows Sockets n’est pas nécessaire pour prendre en charge l’utilisation de `Connect` sur un socket de ce type.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CAsyncSocket::OnReceive](#onreceive).

##  <a name="socket"></a>  CASyncSocket::Socket

Alloue un handle de socket.

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>Paramètres

*nSocketType*<br/>
Spécifie `SOCK_STREAM` ou `SOCK_DGRAM`.

*lEvent*<br/>
Masque de bits qui spécifie une combinaison d’événements réseau dans lequel l’application s’intéresse.

- `FD_READ`: Souhaitez recevoir une notification de préparation pour la lecture.

- `FD_WRITE`: Souhaitez recevoir une notification de préparation pour l’écriture.

- `FD_OOB`: Souhaitez recevoir une notification de l’arrivée des données hors bande.

- `FD_ACCEPT`: Souhaitez recevoir une notification de connexions entrantes.

- `FD_CONNECT`: Souhaitez recevoir une notification de connexion terminée.

- `FD_CLOSE`: Souhaitez recevoir une notification de fermeture du socket.

*nProtocolType*<br/>
Protocole à utiliser avec le socket qui est spécifique à la famille d’adresses indiquée.

*nAddressFormat*<br/>
Spécification de la famille d’adresses.

### <a name="return-value"></a>Valeur de retour

Retourne `TRUE` en cas de réussite, `FALSE` en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode alloue un handle de socket. Il n’appelle pas [CAsyncSocket::Bind](#bind) pour lier le socket à une adresse spécifiée, donc vous devez appeler `Bind` ultérieurement à la liaison du socket à une adresse spécifiée. Vous pouvez utiliser [CAsyncSocket::SetSockOpt](#setsockopt) pour définir l’option de socket avant qu’il est lié.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSocket, classe](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
