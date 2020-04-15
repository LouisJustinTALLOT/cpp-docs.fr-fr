---
title: Classe CAsyncSocket
ms.date: 09/03/2019
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
ms.openlocfilehash: 7ab02dba4bf10b04dddac4e2e954623223af42d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353028"
---
# <a name="casyncsocket-class"></a>Classe CAsyncSocket

Représente une prise Windows — un point final de la communication réseau.

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
|[CAsyncSocket::Accepter](#accept)|Accepte une connexion sur la prise.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Demande la notification de l’événement pour la prise.|
|[CAsyncSocket::Attach](#attach)|Attache une poignée de `CAsyncSocket` prise à un objet.|
|[CAsyncSocket::Bind](#bind)|Associe une adresse locale à la prise.|
|[CAsyncSocket::Fermer](#close)|Ferme la prise.|
|[CAsyncSocket::Connect](#connect)|Établit une connexion à une prise par les pairs.|
|[CAsyncSocket::Create](#create)|Crée une prise.|
|[CAsyncSocket::Detach](#detach)|Détache une poignée de prise `CAsyncSocket` d’un objet.|
|[CAsyncSocket::DeHandle](#fromhandle)|Retourne un pointeur à un `CAsyncSocket` objet, étant donné une poignée de prise.|
|[CAsyncSocket::GetLastError](#getlasterror)|Obtient le statut d’erreur pour la dernière opération qui a échoué.|
|[CAsyncSocket::GetPeerName](#getpeername)|Obtient l’adresse de la prise par les pairs à laquelle la prise est connectée.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Obtient l’adresse de la prise par les pairs à laquelle la prise est connectée (gère les adresses IPv6).|
|[CAsyncSocket::GetSockName](#getsockname)|Obtient le nom local pour une prise.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Obtient le nom local pour une prise (gère les adresses IPv6).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Récupère une option de prise.|
|[CAsyncSocket::IOCtl](#ioctl)|Contrôle le mode de la prise.|
|[CAsyncSocket::Écoutez](#listen)|Établit une prise pour écouter les demandes de connexion entrantes.|
|[CAsyncSocket::Recevoir](#receive)|Reçoit des données de la prise.|
|[CAsyncSocket::RecevoirDe](#receivefrom)|Reçoit un datagram et stocke l’adresse source.|
|[CAsyncSocket::ReceiveDeEx](#receivefromex)|Reçoit un datagram et stocke l’adresse source (gère les adresses IPv6).|
|[CAsyncSocket::Envoyer](#send)|Envoie des données à un socket connecté.|
|[CAsyncSocket::SendTo](#sendto)|Envoie des données vers une destination spécifique.|
|[CAsyncSocket::SendToEx](#sendtoex)|Envoie des données vers une destination spécifique (gère les adresses IPv6).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Définit une option de prise.|
|[CAsyncSocket::ShutDown](#shutdown)|Désactiver `Send` et/ou `Receive` faire appel à la prise.|
|[CASyncSocket::Socket](#socket)|Alloue une poignée de prise.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|Informe une prise d’écoute qu’elle peut `Accept`accepter les demandes de connexion en attente en appelant .|
|[CAsyncSocket::OnClose](#onclose)|Informe une prise que la prise qui s’y est connectée a fermé.|
|[CAsyncSocket::OnConnect](#onconnect)|Informe une prise de connexion que la tentative de connexion est terminée, que ce soit avec succès ou par erreur.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Informe une prise de réception qu’il y a des données hors bande à lire sur la prise, habituellement un message urgent.|
|[CAsyncSocket::OnReceive](#onreceive)|Informe une prise d’écoute qu’il y `Receive`a des données à récupérer en appelant .|
|[CAsyncSocket::OnSend](#onsend)|Informe une prise qu’elle peut `Send`envoyer des données en appelant .|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAsyncSocket::opérateur](#operator_eq)|Attribue une nouvelle valeur `CAsyncSocket` à un objet.|
|[CAsyncSocket::opérateur SOCKET](#operator_socket)|Utilisez cet opérateur pour récupérer la `CAsyncSocket` poignée SOCKET de l’objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Indique la poignée SOCKET `CAsyncSocket` attachée à cet objet.|

## <a name="remarks"></a>Notes

La `CAsyncSocket` classe résume l’API des fonctions Windows Socket, offrant une abstraction orientée objet pour les programmeurs qui souhaitent utiliser windows Sockets en collaboration avec MFC.

Cette classe est basée sur l’hypothèse que vous comprenez les communications réseau. Vous êtes responsable de la gestion des différences de blocage, d’ordre de byte et des conversions entre les chaînes Unicode et les chaînes de caractères multioctets (MBCS). Si vous voulez une interface plus pratique qui gère ces questions pour vous, voir classe [CSocket](../../mfc/reference/csocket-class.md).

Pour utiliser `CAsyncSocket` un objet, appelez son constructeur, puis appelez la fonction `SOCKET` [Créer](#create) pour créer la poignée de prise sous-jacente (type), sauf sur les prises acceptées. Pour une prise de serveur, appelez la fonction membre [Listen,](#listen) et pour une prise client appelez la fonction de membre [Connect.](#connect) La prise du serveur doit appeler la fonction [Accepter](#accept) lors de la réception d’une demande de connexion. Utilisez les `CAsyncSocket` fonctions restantes pour effectuer des communications entre les prises. Une fois terminé, détruire l’objet `CAsyncSocket` s’il a été créé sur le tas; le destructeur appelle automatiquement la fonction [Close.](#close) Le type de données SOCKET est décrit dans l’article [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

> [!NOTE]
> Lorsque vous utilisez des prises MFC dans des threads secondaires dans `AfxSocketInit` une application MFC statiquement liée, vous devez appeler dans chaque thread qui utilise des prises pour initialiser les bibliothèques de prises. Par défaut, `AfxSocketInit` est appelé uniquement dans le fil principal.

Pour plus d’informations, voir [Windows Sockets: Using Class CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) and related articles., as well as [Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Spécifications

**En-tête:** afxsock.h

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket::Accepter

Appelez cette fonction de membre pour accepter une connexion sur une prise.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Paramètres

*rConnectedSocket (en)*<br/>
Une référence identifiant une nouvelle prise qui est disponible pour la connexion.

*lpSockAddr*<br/>
Un pointeur vers une structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) qui reçoit l’adresse de la prise de connexion, comme on le sait sur le réseau. Le format exact de *l’argument lpSockAddr* est déterminé par la famille d’adresse établie lors de la création de la prise. Si *lpSockAddr* et/ou *lpSockAddrLen* sont égaux à NULL, alors aucune information sur l’adresse à distance de la prise acceptée n’est retournée.

*lpSockAddrLen*<br/>
Un pointeur sur la longueur de l’adresse en *lpSockAddr* dans les octets. Le *lpSockAddrLen* est un paramètre de valeur-résultat: il devrait d’abord contenir la quantité d’espace pointée par *lpSockAddr;* au retour, il contiendra la longueur réelle (dans les octets) de l’adresse retournée.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *L’argument lpSockAddrLen* est trop petit (moins que la taille d’une structure [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Un appel de windows Sockets de blocage est en cours.

- WSAEINVAL `Listen` n’a pas été invoqué avant d’être accepté.

- WSAEMFILE La file d’attente est vide à l’entrée pour accepter et il n’y a pas de descripteurs disponibles.

- WSAENOBUFS Aucun espace tampon n’est disponible.

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEOPNOTSUPP La prise référencée n’est pas un type qui prend en charge le service axé sur la connexion.

- WSAEWOULDBLOCK La prise est marquée comme non-blocage et aucune connexion n’est présente pour être acceptée.

### <a name="remarks"></a>Notes

Cette routine extrait la première connexion dans la file d’attente des connexions en attente, crée une nouvelle prise avec les mêmes propriétés que cette prise, et l’attache à *rConnectedSocket*. Si aucune connexion en attente n’est présente sur la file d’attente, `Accept` renvoie zéro et `GetLastError` renvoie une erreur. La prise acceptée *(rConnectedSocket)* ne peut pas être utilisée pour accepter plus de connexions. La prise d’origine reste ouverte et à l’écoute.

*L’argument lpSockAddr* est un paramètre de résultat qui est rempli avec l’adresse de la prise de connexion, comme connu de la couche de communication. `Accept`est utilisé avec des types de prises basées sur la connexion tels que SOCK_STREAM.

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket::AsyncSelect

Appelez cette fonction membre pour demander la notification d’événement pour une prise.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Paramètres

*Levent*<br/>
Un bitmask qui spécifie une combinaison d’événements réseau dans lesquels l’application est intéressée.

- FD_READ Voulez recevoir une notification de préparation à la lecture.

- FD_WRITE Souhaitez recevoir une notification lorsque les données sont disponibles pour être lues.

- FD_OOB Voulez recevoir une notification de l’arrivée des données hors bande.

- FD_ACCEPT Voulez recevoir une notification des connexions entrantes.

- FD_CONNECT Souhaitez recevoir une notification des résultats de connexion.

- FD_CLOSE Voulez recevoir une notification lorsqu’une prise a été fermée par un pair.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL indique que l’un des paramètres spécifiés était invalide.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour spécifier quelles fonctions de notification de rappel MFC seront appelées pour la prise. `AsyncSelect`définit automatiquement cette prise en mode non-blocage. Pour plus d’informations, consultez l’article [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketattach"></a><a name="attach"></a>CAsyncSocket::Attach

Appelez cette fonction de membre pour attacher `CAsyncSocket` la poignée *de hSocket* à un objet.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient une poignée à une prise.

*Levent*<br/>
Un bitmask qui spécifie une combinaison d’événements réseau dans lesquels l’application est intéressée.

- FD_READ Voulez recevoir une notification de préparation à la lecture.

- FD_WRITE Souhaitez recevoir une notification lorsque les données sont disponibles pour être lues.

- FD_OOB Voulez recevoir une notification de l’arrivée des données hors bande.

- FD_ACCEPT Voulez recevoir une notification des connexions entrantes.

- FD_CONNECT Souhaitez recevoir une notification des résultats de connexion.

- FD_CLOSE Voulez recevoir une notification lorsqu’une prise a été fermée par un pair.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la fonction aboutit.

### <a name="remarks"></a>Notes

La poignée SOCKET est stockée dans le membre de données [m_hSocket](#m_hsocket) de l’objet.

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket::Bind

Appelez cette fonction de membre pour associer une adresse locale à la prise.

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Paramètres

*nSocketPort (en)*<br/>
Le port identifiant l’application de prise.

*lpszSocketAddress*<br/>
L’adresse réseau, un numéro pointillé tel que "128.56.22.8". Passer la chaîne NULL pour `CAsyncSocket` ce paramètre indique que l’instance doit écouter l’activité client sur toutes les interfaces réseau.

*lpSockAddr*<br/>
Un pointeur vers une structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) qui contient l’adresse à attribuer à cette prise.

*nSockAddrLen (en)*<br/>
La longueur de l’adresse en *lpSockAddr* dans les octets.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). La liste suivante couvre quelques-unes des erreurs qui pourraient être retournées. Pour une liste complète, voir [windows Sockets Error Codes](/windows/win32/winsock/windows-sockets-error-codes-2).

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE L’adresse spécifiée est déjà utilisée. (Voir l’option SO_REUSEADDR prise sous [SetSockOpt](#setsockopt).)

- WSAEFAULT *L’argument nSockAddrLen* est trop petit (moins que la taille d’une structure [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Un appel de windows Sockets de blocage est en cours.

- WSAEAFNOSUPPORT La famille d’adresse spécifiée n’est pas soutenue par ce port.

- WSAEINVAL La prise est déjà liée à une adresse.

- WSAENOBUFS Pas assez de tampons disponibles, trop de connexions.

- WSAENOTSOCK Le descripteur n’est pas une prise.

### <a name="remarks"></a>Notes

Cette routine est utilisée sur un datagram ou une `Connect` `Listen` prise de flux non relié, avant les appels ou les appels suivants. Avant de pouvoir accepter les demandes de connexion, une prise de serveur d’écoute `Bind`doit sélectionner un numéro de port et le faire connaître aux prises Windows en appelant . `Bind`établit l’association locale (adresse d’accueil/numéro de port) de la prise en attribuant un nom local à une prise anonyme.

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket::CAsyncSocket

Construit un objet de prise vierge.

```
CAsyncSocket();
```

### <a name="remarks"></a>Notes

Après la construction de l’objet, vous devez appeler sa `Create` fonction de membre pour créer la structure de données SOCKET et lier son adresse. (Du côté serveur d’une communication Windows Sockets, lorsque la prise `Accept` d’écoute crée `Create` une prise à utiliser dans l’appel, vous n’appelez pas pour cette prise.)

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket::Fermer

Ferme la prise.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Cette fonction libère le descripteur de prise de sorte que d’autres références à celui-ci échouent avec l’erreur WSAENOTSOCK. Si c’est la dernière référence à la prise sous-jacente, les informations de nommage associées et les données en file d’attente sont rejetées. Le destructeur de l’objet `Close` de la prise vous appelle.

Pour `CAsyncSocket`, mais `CSocket`pas pour , `Close` la sémantique de sont affectés par les options de prise SO_LINGER et SO_DONTLINGER. Pour plus d’informations, voir fonction `GetSockOpt`membre .

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket::Connect

Appelez cette fonction de membre pour établir une connexion à un flux non connecté ou une prise de datagram.

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
L’adresse réseau de la prise à laquelle cet objet est connecté : un nom de machine tel que « ftp.microsoft.com », ou un numéro pointillé tel que « 128.56.22.8 ».

*nHostPort (nHostPort)*<br/>
Le port identifiant l’application de prise.

*lpSockAddr*<br/>
Un pointeur vers une structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) qui contient l’adresse de la prise connectée.

*nSockAddrLen (en)*<br/>
La longueur de l’adresse en *lpSockAddr* dans les octets.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Si cela indique un code d’erreur de WSAEWOULDBLOCK, et que votre application `OnConnect` utilise les rappels prépondérants, votre application recevra un message lorsque l’opération de connexion est terminée. Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE L’adresse spécifiée est déjà utilisée.

- WSAEINPROGRESS Un appel de windows Sockets de blocage est en cours.

- WSAEADDRNOTAVAIL L’adresse spécifiée n’est pas disponible à partir de la machine locale.

- Les adresses WSAEAFNOSUPPORT dans la famille spécifiée ne peuvent pas être utilisées avec cette prise.

- WSAECONNREFUSED La tentative de connexion a été rejetée.

- WSAEDESTADDRREQ Une adresse de destination est requise.

- WSAEFAULT *L’argument nSockAddrLen* est incorrect.

- Adresse d’accueil WSAEINVAL Invalid.

- WSAEISCONN La prise est déjà connectée.

- WSAEMFILE Plus plus descripteurs de fichiers sont disponibles.

- WSAENETUNREACH Le réseau ne peut pas être atteint à partir de cet hôte pour le moment.

- WSAENOBUFS Aucun espace tampon n’est disponible. La prise ne peut pas être reliée.

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAETIMEDOUT Tentative de connexion chronométrée sans établir de connexion.

- WSAEWOULDBLOCK La prise est marquée comme non-blocage et la connexion ne peut pas être complétée immédiatement.

### <a name="remarks"></a>Notes

Si la prise n’est pas liée, des valeurs uniques sont attribuées à l’association locale par le système, et la prise est marquée comme liée. Notez que si le champ d’adresse `Connect` de la structure de nom est tous les zéros, retournera zéro. Pour obtenir des informations `GetLastError` d’erreur étendues, appelez la fonction membre.

Pour les prises de flux (type SOCK_STREAM), une connexion active est initiée à l’hôte étranger. Lorsque l’appel de prise se termine avec succès, la prise est prête à envoyer/recevoir des données.

Pour une prise de datagram (type SOCK_DGRAM), une destination par défaut `Send` `Receive` est définie, qui sera utilisée sur les appels et les appels suivants.

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket::Créer

Appelez `Create` la fonction membre après la construction d’un objet de prise pour créer la prise Windows et l’attacher.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Paramètres

*nSocketPort (en)*<br/>
Un port bien connu à utiliser avec la prise, ou 0 si vous voulez windows Sockets pour sélectionner un port.

*nSocketType (en)*<br/>
SOCK_STREAM ou SOCK_DGRAM.

*Levent*<br/>
Un bitmask qui spécifie une combinaison d’événements réseau dans lesquels l’application est intéressée.

- FD_READ Voulez recevoir une notification de préparation à la lecture.

- FD_WRITE Voulez recevoir une notification de préparation à l’écriture.

- FD_OOB Voulez recevoir une notification de l’arrivée des données hors bande.

- FD_ACCEPT Voulez recevoir une notification des connexions entrantes.

- FD_CONNECT Voulez recevoir une notification de connexion complétée.

- FD_CLOSE Voulez recevoir une notification de fermeture de prise.

*lpszSockAddress*<br/>
Un pointeur à une chaîne contenant l’adresse réseau de la prise connectée, un numéro pointillé tel que "128.56.22.8". Passer la chaîne NULL pour `CAsyncSocket` ce paramètre indique que l’instance doit écouter l’activité client sur toutes les interfaces réseau.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEAFNOSUPPORT La famille d’adresse spécifiée n’est pas prise en charge.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAEMFILE Plus plus descripteurs de fichiers sont disponibles.

- WSAENOBUFS Aucun espace tampon n’est disponible. La prise ne peut pas être créée.

- WSAEPROTONOSUPPORT Le port spécifié n’est pas pris en charge.

- WSAEPROTOTYPE Le port spécifié est le mauvais type pour cette prise.

- WSAESOCKTNOSUPPORT Le type de prise spécifié n’est pas pris en charge dans cette famille d’adresses.

### <a name="remarks"></a>Notes

`Create`appelle [Socket](#socket) et en cas de succès, il appelle [Bind](#bind) pour lier la prise à l’adresse spécifiée. Les types de prises suivants sont pris en charge :

- SOCK_STREAM Fournit des flux d’accessoires séquencés, fiables, entièrement en duplex et basés sur la connexion. Utilise le protocole de contrôle de transmission (TCP) pour la famille d’adresses Internet.

- SOCK_DGRAM prend en charge les datagrammes, qui sont des paquets sans connexion et peu fiables d’une longueur maximale fixe (généralement petite). Utilise le protocole de datagram utilisateur (UDP) pour la famille d’adresses Internet.

    > [!NOTE]
    >  La `Accept` fonction membre fait référence à `CSocket` un nouvel objet vide comme paramètre. Vous devez construire cet `Accept`objet avant d’appeler . Gardez à l’esprit que si cet objet de prise sort de portée, la connexion se ferme. N’appelez `Create` pas pour ce nouvel objet de prise.

> [!IMPORTANT]
> `Create`**n’est pas** sans fil.  Si vous l’appelez dans un environnement à plusieurs fils où il pourrait être invoqué simultanément par différents threads, assurez-vous de protéger chaque appel avec un mutex ou un autre verrou de synchronisation.

Pour plus d’informations sur les prises de flux et de datagram, consultez les articles [Windows Sockets: Background](../../mfc/windows-sockets-background.md) et [Windows Sockets: Ports and Socket Addresses](../../mfc/windows-sockets-ports-and-socket-addresses.md) et Windows [Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket::Detach

Appelez cette fonction de membre pour détacher la poignée SOCKET `CAsyncSocket` dans le membre *de* données m_hSocket de l’objet et *définissez m_hSocket* à NULL.

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket::DeHandle

Retourne un pointeur à un `CAsyncSocket` objet.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient une poignée à une prise.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CAsyncSocket` vers un objet, `CAsyncSocket` ou NULL s’il n’y a pas d’objet attaché à *hSocket*.

### <a name="remarks"></a>Notes

Lorsqu’on lui donne une `CAsyncSocket` poignée SOCKET, si un objet n’est pas attaché à la poignée, la fonction du membre renvoie NULL.

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket::GetLastError

Appelez cette fonction de membre pour obtenir le statut d’erreur pour la dernière opération qui a échoué.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Valeur de retour

La valeur de retour indique le code d’erreur pour la dernière routine aPI Windows Sockets effectuée par ce thread.

### <a name="remarks"></a>Notes

Lorsqu’une fonction particulière de membre `GetLastError` indique qu’une erreur s’est produite, doit être appelé pour récupérer le code d’erreur approprié. Consultez les descriptions de fonctions des membres pour une liste des codes d’erreur applicables.

Pour plus d’informations sur les codes d’erreur, voir [Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket::GetPeerName

Appelez cette fonction de membre pour obtenir l’adresse de la prise par les pairs à laquelle cette prise est connectée.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Paramètres

*rPeerAddress (en)*<br/>
Référence à `CString` un objet qui reçoit une adresse IP numéro pointillé.

*rPeerPort (en)*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Un pointeur à la structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) qui reçoit le nom de la prise par les pairs.

*lpSockAddrLen*<br/>
Un pointeur sur la longueur de l’adresse en *lpSockAddr* dans les octets. Au retour, *l’argument lpSockAddrLen* contient la taille réelle de *lpSockAddr* retourné dans les octets.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *LpSockAddrLen* argument n’est pas assez grand.

- WSAEINPROGRESS Un appel de windows Sockets de blocage est en cours.

- WSAENOTCONN La prise n’est pas connectée.

- WSAENOTSOCK Le descripteur n’est pas une prise.

### <a name="remarks"></a>Notes

Pour gérer les adresses IPv6, utilisez [CAsyncSocket::GetPeerNameEx](#getpeernameex).

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket::GetPeerNameEx

Appelez cette fonction de membre pour obtenir l’adresse de la prise par les pairs à laquelle cette prise est connectée (gère les adresses IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Paramètres

*rPeerAddress (en)*<br/>
Référence à `CString` un objet qui reçoit une adresse IP numéro pointillé.

*rPeerPort (en)*<br/>
Référence à un UINT qui stocke un port.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *LpSockAddrLen* argument n’est pas assez grand.

- WSAEINPROGRESS Un appel de windows Sockets de blocage est en cours.

- WSAENOTCONN La prise n’est pas connectée.

- WSAENOTSOCK Le descripteur n’est pas une prise.

### <a name="remarks"></a>Notes

Cette fonction est la même que [CAsyncSocket::GetPeerName](#getpeername) sauf qu’il gère les adresses IPv6 ainsi que les protocoles plus anciens.

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket::GetSockName

Appelez cette fonction de membre pour obtenir le nom local pour une prise.

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);

BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Paramètres

*rSocketAddress (en)*<br/>
Référence à `CString` un objet qui reçoit une adresse IP numéro pointillé.

*rSocketPort (en)*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Un pointeur vers une structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) qui reçoit l’adresse de la prise.

*lpSockAddrLen*<br/>
Un pointeur sur la longueur de l’adresse en *lpSockAddr* dans les octets.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *LpSockAddrLen* argument n’est pas assez grand.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEINVAL La prise n’a pas `Bind`été liée à une adresse avec .

### <a name="remarks"></a>Notes

Cet appel est particulièrement utile `Connect` lorsqu’un `Bind` appel a été fait sans faire une première; cet appel fournit le seul moyen par lequel vous pouvez déterminer l’association locale qui a été définie par le système.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket::GetSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket::GetSockNameEx

Appelez cette fonction de membre pour obtenir le nom local pour une prise (gère les adresses IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Paramètres

*rSocketAddress (en)*<br/>
Référence à `CString` un objet qui reçoit une adresse IP numéro pointillé.

*rSocketPort (en)*<br/>
Référence à un UINT qui stocke un port.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *LpSockAddrLen* argument n’est pas assez grand.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEINVAL La prise n’a pas `Bind`été liée à une adresse avec .

### <a name="remarks"></a>Notes

Cet appel est le même que [CAsyncSocket::GetSockName](#getsockname) sauf qu’il gère les adresses IPv6 ainsi que les protocoles plus anciens.

Cet appel est particulièrement utile `Connect` lorsqu’un `Bind` appel a été fait sans faire une première; cet appel fournit le seul moyen par lequel vous pouvez déterminer l’association locale qui a été définie par le système.

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket::GetSockOpt

Appelez cette fonction de membre pour récupérer une option de prise.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Paramètres

*nOptionName (en)*<br/>
L’option de prise pour laquelle la valeur doit être récupérée.

*lpOptionValue*<br/>
Un pointeur vers le tampon dans lequel la valeur de l’option demandée doit être retournée. La valeur associée à l’option sélectionnée est retournée dans le tampon *lpOptionValue*. L’intégrateur pointé par *lpOptionLen* devrait à l’origine contenir la taille de ce tampon dans les octets; et au retour, il sera réglé à la taille de la valeur retournée. Pour SO_LINGER, ce sera la taille `LINGER` d’une structure; pour toutes les autres options, il sera de la taille d’un BOOL ou un **int**, selon l’option. Consultez la liste des options et de leurs tailles dans la section Remarques.

*lpOptionLen*<br/>
Un pointeur à la taille de la tampon *lpOptionValue* dans les octets.

*nLevel (en)*<br/>
le niveau auquel l’option est définie; les seuls niveaux pris en charge sont SOL_SOCKET et IPPROTO_TCP.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Si une option n’a jamais été définie avec, `SetSockOpt`puis `GetSockOpt` retourne la valeur par défaut pour l’option. Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *LpOptionLen* argument était invalide.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAENOPROTOOPT L’option est inconnue ou non supportée. En particulier, SO_BROADCAST n’est pas pris en charge sur les prises de SOCK_STREAM de type, tandis que les SO_ACCEPTCONN, les SO_DONTLINGER, les SO_KEEPALIVE, les SO_LINGER et les SO_OOBINLINE ne sont pas pris en charge sur des prises de type SOCK_DGRAM.

- WSAENOTSOCK Le descripteur n’est pas une prise.

### <a name="remarks"></a>Notes

`GetSockOpt`récupère la valeur actuelle d’une option de prise associée à une prise de tout type, dans n’importe quel état, et stocke le résultat en *lpOptionValue*. Les options affectent les opérations de prise, telles que le routage des paquets, le transfert de données hors bande, et ainsi de suite.

Les options suivantes `GetSockOpt`sont prises en charge pour . Le type identifie le type de données traitées par *lpOptionValue*. L’option TCP_NODELAY utilise des IPPROTO_TCP de niveau; toutes les autres options utilisent le niveau SOL_SOCKET.

|Value|Type|Signification|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Socket écoute.|
|SO_BROADCAST|BOOL|Socket est configuré pour la transmission de messages de diffusion.|
|SO_DEBUG|BOOL|Le débogage est activé.|
|SO_DONTLINGER|BOOL|Si c’est vrai, l’option SO_LINGER est désactivée.|
|SO_DONTROUTE|BOOL|Le routage est désactivé.|
|SO_ERROR|**int**|Récupérez l’état d’erreur et effacez.|
|SO_KEEPALIVE|BOOL|Des garder en vie sont envoyés.|
|SO_LINGER|`struct LINGER`|Retourne les options actuelles.|
|SO_OOBINLINE|BOOL|Les données hors bande sont reçues dans le flux de données normal.|
|SO_RCVBUF|int|Taille tampon pour les réceptions.|
|SO_REUSEADDR|BOOL|La prise peut être liée à une adresse qui est déjà utilisée.|
|SO_SNDBUF|**int**|Taille tampon pour les envois.|
|SO_TYPE|**int**|Le type de prise (par exemple, SOCK_STREAM).|
|TCP_NODELAY|BOOL|Désactive l'algorithme Nagle pour la fusion des envois.|

Berkeley Software Distribution (BSD) `GetSockOpt` options non prises en charge sont les suivantes:

|Value|Type|Signification|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Recevez une faible marque d’eau.|
|SO_RCVTIMEO|**int**|Recevez un délai d’attente.|
|SO_SNDLOWAT|**int**|Envoyez une marque basse d’eau.|
|SO_SNDTIMEO|**int**|Envoyez un délai d’attente.|
|IP_OPTIONS||Obtenez des options en en en-tête IP.|
|TCP_MAXSEG|**int**|Obtenez la taille maximale du segment TCP.|

Appeler `GetSockOpt` avec une option non-supportée entraînera un code d’erreur de WSAENOPROTOOPT étant retourné de `GetLastError`.

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket::IOCtl

Appelez cette fonction de membre pour contrôler le mode d’une prise.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Paramètres

*lCommand (en)*<br/>
L’ordre d’effectuer sur la prise.

*lpArgument*<br/>
Un pointeur vers un paramètre pour *lCommand*.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL *lCommand* n’est pas une commande valide, ou *lpArgument* n’est pas un paramètre acceptable pour *le lCommand*, ou la commande n’est pas applicable au type de prise fournie.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAENOTSOCK Le descripteur n’est pas une prise.

### <a name="remarks"></a>Notes

Cette routine peut être utilisée sur n’importe quelle prise dans n’importe quel état. Il est utilisé pour obtenir ou récupérer les paramètres d’exploitation associés à la prise, indépendamment du protocole et du sous-système de communication. Les commandes suivantes sont prises en charge :

- FIONBIO Activez ou désactivent le mode de non-blocage sur la prise. Le *paramètre lpArgument* pointe à un `DWORD`, qui est nonzero si le mode de non-blocage doit être activé et zéro si elle doit être désactivée. Si `AsyncSelect` a été émis sur une prise, `IOCtl` alors toute tentative d’utiliser pour remettre la prise en mode de blocage échouera avec WSAEINVAL. Pour remettre la prise en mode de blocage et éviter l’erreur WSAEINVAL, une application doit `AsyncSelect` d’abord désactiver en `AsyncSelect` appelant avec le paramètre *lEvent* égal à 0, puis appelez `IOCtl`.

- FIONREAD Déterminez le nombre maximum d’octets qui peuvent être lus avec un seul `Receive` appel à partir de cette prise. Le *paramètre lpArgument* indique un `DWORD` dans lequel `IOCtl` stocke le résultat. Si cette prise est de type SOCK_STREAM, FIONREAD renvoie la quantité totale `Receive`de données qui peuvent être lues en une seule ; c’est normalement le même que la quantité totale de données en file d’attente sur la prise. Si cette prise est de type SOCK_DGRAM, FIONREAD retourne la taille du premier datagram en file d’attente sur la prise.

- SIOCATMARK Déterminez si toutes les données hors bande ont été lues. Cela ne s’applique qu’à une prise de type SOCK_STREAM qui a été configurée pour la réception en ligne de toutes les données hors bande (SO_OOBINLINE). Si aucune donnée hors bande n’attend d’être lue, l’opération renvoie nonzero. Sinon, il retourne 0, et le suivant `Receive` ou `ReceiveFrom` effectué sur la prise récupérera une partie ou la totalité des données précédant la «marque»; l’application doit utiliser l’opération SIOCATMARK pour déterminer si des données subsistent. S’il y a des données normales précédant les données « urgentes » (hors bande), elles seront reçues dans l’ordre. (Notez `Receive` qu’un ou `ReceiveFrom` ne mélangera jamais des données hors bande et normales dans le même appel.) Le *paramètre lpArgument* indique un `DWORD` dans lequel `IOCtl` stocke le résultat.

Cette fonction est un `ioctl()` sous-ensemble de comme utilisé dans les prises de Berkeley. En particulier, il n’y a pas de commande équivalente à FIOASYNC, tandis que SIOCATMARK est la seule commande au niveau des prises qui est prise.

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket::Écoutez

Appelez cette fonction de membre pour écouter les demandes de connexion entrantes.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Paramètres

*nConnectionBacklog (nConnectionBacklog)*<br/>
La longueur maximale à laquelle la file d’attente des connexions en attente peut croître. La portée valide est de 1 à 5.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE Une tentative a été faite pour écouter une adresse utilisée.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAEINVAL La prise n’a `Bind` pas été liée ou est déjà connectée.

- WSAEISCONN La prise est déjà connectée.

- WSAEMFILE Plus plus descripteurs de fichiers sont disponibles.

- WSAENOBUFS Aucun espace tampon n’est disponible.

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEOPNOTSUPP La prise référencée n’est `Listen` pas d’un type qui prend en charge l’opération.

### <a name="remarks"></a>Notes

Pour accepter les connexions, la `Create`prise est d’abord `Listen`créée avec , un `Accept`arriéré pour les connexions entrantes est spécifié avec , puis les connexions sont acceptées avec . `Listen`ne s’applique qu’aux prises qui prennent en charge les connexions, c’est-à-dire celles de type SOCK_STREAM. Cette prise est mise en mode « passif » où les connexions entrantes sont reconnues et mises en file d’attente en attendant l’acceptation par le processus.

Cette fonction est généralement utilisée par les serveurs (ou toute application qui veut accepter les connexions) qui pourraient avoir plus d’une demande de connexion à la fois: si une demande de connexion arrive avec la file d’attente complète, le client recevra une erreur avec une indication de WSAECONNREFUSED.

`Listen`de continuer à fonctionner rationnellement lorsqu’il n’y a pas de ports disponibles (descripteurs). Il acceptera les connexions jusqu’à ce que la file d’attente soit vidée. Si des ports deviennent disponibles, un appel ultérieur `Listen` à la file d’attente ou `Accept` remplira la file d’attente à l'« arriéré » actuel ou le plus récent, si possible, et reprendra l’écoute des connexions entrantes.

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket::m_hSocket

Contient la poignée SOCKET pour la prise `CAsyncSocket` encapsulée par cet objet.

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket::OnAccept

Appelé par le cadre pour informer une prise d’écoute qu’il peut accepter les demandes de connexion en attente en appelant la fonction membre [Accepter.](#accept)

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur une prise. Les codes d’erreur `OnAccept` suivants s’appliquent à la fonction membre :

- **0** La fonction exécutée avec succès.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket::OnClose

Appelé par le cadre pour informer cette prise que la prise connectée est fermée par son processus.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur une prise. Les codes d’erreur `OnClose` suivants s’appliquent à la fonction membre :

- **0** La fonction exécutée avec succès.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAECONNRESET La connexion a été réinitialisée par le côté distant.

- WSAECONNABORTED La connexion a été avortée en raison d’un délai d’attente ou d’une autre défaillance.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket::OnConnect

Appelé par le cadre pour informer cette prise de connexion que sa tentative de connexion est terminée, que ce soit avec succès ou par erreur.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur une prise. Les codes d’erreur `OnConnect` suivants s’appliquent à la fonction membre :

- **0** La fonction exécutée avec succès.

- WSAEADDRINUSE L’adresse spécifiée est déjà utilisée.

- WSAEADDRNOTAVAIL L’adresse spécifiée n’est pas disponible à partir de la machine locale.

- Les adresses WSAEAFNOSUPPORT dans la famille spécifiée ne peuvent pas être utilisées avec cette prise.

- WSAECONNREFUSED La tentative de connexion a été rejetée avec force.

- WSAEDESTADDRREQ Une adresse de destination est requise.

- WSAEFAULT *LpSockAddrLen* argument est incorrect.

- WSAEINVAL La prise est déjà liée à une adresse.

- WSAEISCONN La prise est déjà connectée.

- WSAEMFILE Plus plus descripteurs de fichiers sont disponibles.

- WSAENETUNREACH Le réseau ne peut pas être atteint à partir de cet hôte pour le moment.

- WSAENOBUFS Aucun espace tampon n’est disponible. La prise ne peut pas être reliée.

- WSAENOTCONN La prise n’est pas connectée.

- WSAENOTSOCK Le descripteur est un fichier, pas une prise.

- WSAETIMEDOUT La tentative de connexion chronométrée sans établir de connexion.

### <a name="remarks"></a>Notes

> [!NOTE]
> Dans [CSocket](../../mfc/reference/csocket-class.md) `OnConnect` , la fonction de notification n’est jamais appelée. Pour les connexions, vous appelez `Connect`simplement, qui reviendra lorsque la connexion est terminée (soit avec succès ou par erreur). La façon dont les notifications de connexion sont traitées est un détail de implémentation MFC.

Pour plus d’informations, voir [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket::OnOutOfBandData

Appelé par le cadre pour informer la prise de réception que la prise d’envoi a des données hors bande à envoyer.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur une prise. Les codes d’erreur `OnOutOfBandData` suivants s’appliquent à la fonction membre :

- **0** La fonction exécutée avec succès.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Les données hors bande sont un canal logiquement indépendant qui est associé à chaque paire de prises connectées de type SOCK_STREAM. Le canal est généralement utilisé pour envoyer des données urgentes.

MFC prend en charge les données hors `CAsyncSocket` bande, mais les utilisateurs de classe sont découragés de les utiliser. Le moyen le plus facile est de créer une deuxième prise pour passer de telles données. Pour plus d’informations sur les données hors bande, voir [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket::OnReceive

Appelé par le cadre pour informer cette prise qu’il existe des données `Receive` dans le tampon qui peuvent être récupérées en appelant la fonction membre.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur une prise. Les codes d’erreur `OnReceive` suivants s’appliquent à la fonction membre :

- **0** La fonction exécutée avec succès.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket::OnSend

Appelé par le cadre pour informer la prise qu’il `Send` peut maintenant envoyer des données en appelant la fonction membre.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
L’erreur la plus récente sur une prise. Les codes d’erreur `OnSend` suivants s’appliquent à la fonction membre :

- **0** La fonction exécutée avec succès.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket::opérateur

Attribue une nouvelle valeur `CAsyncSocket` à un objet.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Paramètres

*rSrc (rSrc)*<br/>
Une référence à `CAsyncSocket` un objet existant.

### <a name="remarks"></a>Notes

Appelez cette fonction pour `CAsyncSocket` copier `CAsyncSocket` un objet existant à un autre objet.

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket::opérateur SOCKET

Utilisez cet opérateur pour récupérer la `CAsyncSocket` poignée SOCKET de l’objet.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, la poignée de l’objet SOCKET; autrement, NULL.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la poignée pour appeler directement les API Windows.

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket::Recevoir

Appelez cette fonction de membre pour recevoir des données d’une prise.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Un tampon pour les données entrantes.

*nBufLen (en)*<br/>
La longueur de *lpBuf* dans les octets.

*nFlags*<br/>
Spécifie la façon dont l’appel est fait. La sémantique de cette fonction est déterminée par les options de prise et le *paramètre nFlags.* Ce dernier est construit en combinant l’une des valeurs suivantes avec l’opérateur **C OU** :

- MSG_PEEK Jetez un coup d’œil aux données entrantes. Les données sont copiées dans le tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB Processus des données hors bande.

### <a name="return-value"></a>Valeur de retour

En cas d’erreur, `Receive` le nombre d’octets reçus. Si la connexion a été fermée, elle revient 0. Dans le cas contraire, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAENOTCONN La prise n’est pas connectée.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais la prise n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN La prise a été arrêtée; il n’est `Receive` pas possible de `ShutDown` faire appel à une prise après a été invoqué avec *nHow* réglé à 0 ou 2.

- WSAEWOULDBLOCK La prise est marquée comme `Receive` non-blocage et l’opération bloquerait.

- WSAEMSGSIZE Le datagram était trop grand pour s’adapter au tampon spécifié et a été tronqué.

- WSAEINVAL La prise n’a `Bind`pas été liée avec .

- WSAECONNABORTED Le circuit virtuel a été avorté en raison d’un délai d’attente ou d’une autre défaillance.

- WSAECONNRESET Le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour les prises de flux ou de datagramme connectées et est utilisée pour lire les données entrantes.

Pour les prises de type SOCK_STREAM, autant d’informations disponibles à l’heure actuelle jusqu’à la taille du tampon fourni sont retournées. Si la prise a été configurée pour la réception en ligne de données hors bande (option de prise SO_OOBINLINE) et que les données hors bande ne sont pas lues, seules les données hors bande seront retournées. L’application peut `IOCtlSIOCATMARK` utiliser l’option ou [OnOutOfBandData](#onoutofbanddata) pour déterminer si d’autres données hors bande restent à lire.

Pour les prises de datagram, les données sont extraites du premier datagram enqueued, jusqu’à la taille du tampon fourni. Si le datagram est plus grand que le tampon fourni, le tampon est rempli avec `Receive` la première partie du datagram, les données excédentaires sont perdues, et retourne une valeur de SOCKET_ERROR avec le code d’erreur défini à WSAEMSGSIZE. Si aucune donnée entrante n’est disponible à la prise, une valeur de SOCKET_ERROR est retournée avec le code d’erreur défini à WSAEWOULDBLOCK. La fonction de rappel [OnReceive](#onreceive) peut être utilisée pour déterminer quand plus de données arrivent.

Si la prise est de type SOCK_STREAM et le côté distant a `Receive` arrêté la connexion gracieusement, un sera complet immédiatement avec 0 octets reçus. Si la connexion a `Receive` été réinitialisée, un échouera avec l’erreur WSAECONNRESET.

`Receive`devrait être appelé une seule fois pour chaque fois [CAsyncSocket::OnReceive](#onreceive) est appelé.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket::RecevoirDe

Appelez cette fonction membre pour recevoir un datagram et stocker l’adresse source dans la structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) ou dans *rSocketAddress*.

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
Un tampon pour les données entrantes.

*nBufLen (en)*<br/>
La longueur de *lpBuf* dans les octets.

*rSocketAddress (en)*<br/>
Référence à `CString` un objet qui reçoit une adresse IP numéro pointillé.

*rSocketPort (en)*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Un pointeur vers une structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) qui détient l’adresse source au retour.

*lpSockAddrLen*<br/>
Un pointeur sur la longueur de l’adresse source dans *lpSockAddr* dans les octets.

*nFlags*<br/>
Spécifie la façon dont l’appel est fait. La sémantique de cette fonction est déterminée par les options de prise et le *paramètre nFlags.* Ce dernier est construit en combinant l’une des valeurs suivantes avec l’opérateur **C OU** :

- MSG_PEEK Jetez un coup d’œil aux données entrantes. Les données sont copiées dans le tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB Processus des données hors bande.

### <a name="return-value"></a>Valeur de retour

En cas d’erreur, `ReceiveFrom` le nombre d’octets reçus. Si la connexion a été fermée, elle revient 0. Dans le cas contraire, une valeur de SOCKET_ERROR est retournée, `GetLastError`et un code d’erreur spécifique peut être récupéré par appel . Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *L’argument lpSockAddrLen* était invalide : le tampon *lpSockAddr* était trop petit pour accueillir l’adresse des pairs.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAEINVAL La prise n’a `Bind`pas été liée avec .

- WSAENOTCONN La prise n’est pas connectée (SOCK_STREAM seulement).

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais la prise n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN La prise a été arrêtée; il n’est `ReceiveFrom` pas possible de `ShutDown` faire appel à une prise après a été invoqué avec *nHow* réglé à 0 ou 2.

- WSAEWOULDBLOCK La prise est marquée comme `ReceiveFrom` non-blocage et l’opération bloquerait.

- WSAEMSGSIZE Le datagram était trop grand pour s’adapter au tampon spécifié et a été tronqué.

- WSAECONNABORTED Le circuit virtuel a été avorté en raison d’un délai d’attente ou d’une autre défaillance.

- WSAECONNRESET Le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour lire les données entrantes sur une prise (éventuellement connectée) et capturer l’adresse à partir de laquelle les données ont été envoyées.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket::ReceiveFromEx](#receivefromex).

Pour les prises de type SOCK_STREAM, autant d’informations disponibles à l’heure actuelle jusqu’à la taille du tampon fourni sont retournées. Si la prise a été configurée pour la réception en ligne de données hors bande (option de prise SO_OOBINLINE) et que les données hors bande ne sont pas lues, seules les données hors bande seront retournées. L’application peut `IOCtlSIOCATMARK` utiliser `OnOutOfBandData` l’option ou pour déterminer si d’autres données hors bande restent à lire. Les paramètres *lpSockAddr* et *lpSockAddrLen* sont ignorés pour SOCK_STREAM douilles.

Pour les prises de datagram, les données sont extraites du premier datagram enqueued, jusqu’à la taille du tampon fourni. Si le datagram est plus grand que le tampon fourni, le tampon est rempli `ReceiveFrom` de la première partie du message, les données excédentaires sont perdues et renvoie une valeur de SOCKET_ERROR avec le code d’erreur défini à WSAEMSGSIZE.

Si *lpSockAddr* n’est paszero, et que la prise est de type SOCK_DGRAM, l’adresse réseau de la prise qui a envoyé les données est copiée sur la structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) correspondante. La valeur soulignée par *lpSockAddrLen* est parasélisée à la taille de cette structure, et est modifiée au retour pour indiquer la taille réelle de l’adresse stockée là-bas. Si aucune donnée entrante n’est `ReceiveFrom` disponible à la prise, l’appel attend que les données arrivent à moins que la prise ne soit nonblocking. Dans ce cas, une valeur de SOCKET_ERROR est retournée avec le code d’erreur réglé sur WSAEWOULDBLOCK. Le `OnReceive` rappel peut être utilisé pour déterminer quand plus de données arrivent.

Si la prise est de type SOCK_STREAM et le côté distant a `ReceiveFrom` arrêté la connexion gracieusement, un sera complet immédiatement avec 0 octets reçus.

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket::ReceiveDeEx

Appelez cette fonction membre pour recevoir un datagram et stocker l’adresse source dans la structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) ou dans *rSocketAddress* (poignées adresses IPv6).

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
Un tampon pour les données entrantes.

*nBufLen (en)*<br/>
La longueur de *lpBuf* dans les octets.

*rSocketAddress (en)*<br/>
Référence à `CString` un objet qui reçoit une adresse IP numéro pointillé.

*rSocketPort (en)*<br/>
Référence à un UINT qui stocke un port.

*nFlags*<br/>
Spécifie la façon dont l’appel est fait. La sémantique de cette fonction est déterminée par les options de prise et le *paramètre nFlags.* Ce dernier est construit en combinant l’une des valeurs suivantes avec l’opérateur **C OU** :

- MSG_PEEK Jetez un coup d’œil aux données entrantes. Les données sont copiées dans le tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB Processus des données hors bande.

### <a name="return-value"></a>Valeur de retour

En cas d’erreur, `ReceiveFromEx` le nombre d’octets reçus. Si la connexion a été fermée, elle revient 0. Dans le cas contraire, une valeur de SOCKET_ERROR est retournée, `GetLastError`et un code d’erreur spécifique peut être récupéré par appel . Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *L’argument lpSockAddrLen* était invalide : le tampon *lpSockAddr* était trop petit pour accueillir l’adresse des pairs.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAEINVAL La prise n’a `Bind`pas été liée avec .

- WSAENOTCONN La prise n’est pas connectée (SOCK_STREAM seulement).

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais la prise n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN La prise a été arrêtée; il n’est `ReceiveFromEx` pas possible de `ShutDown` faire appel à une prise après a été invoqué avec *nHow* réglé à 0 ou 2.

- WSAEWOULDBLOCK La prise est marquée comme `ReceiveFromEx` non-blocage et l’opération bloquerait.

- WSAEMSGSIZE Le datagram était trop grand pour s’adapter au tampon spécifié et a été tronqué.

- WSAECONNABORTED Le circuit virtuel a été avorté en raison d’un délai d’attente ou d’une autre défaillance.

- WSAECONNRESET Le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour lire les données entrantes sur une prise (éventuellement connectée) et capturer l’adresse à partir de laquelle les données ont été envoyées.

Cette fonction est la même que [CAsyncSocket::ReceiveDe](#receivefrom) excepté qu’il gère les adresses IPv6 ainsi que les protocoles plus anciens.

Pour les prises de type SOCK_STREAM, autant d’informations disponibles à l’heure actuelle jusqu’à la taille du tampon fourni sont retournées. Si la prise a été configurée pour la réception en ligne de données hors bande (option de prise SO_OOBINLINE) et que les données hors bande ne sont pas lues, seules les données hors bande seront retournées. L’application peut `IOCtlSIOCATMARK` utiliser `OnOutOfBandData` l’option ou pour déterminer si d’autres données hors bande restent à lire. Les paramètres *lpSockAddr* et *lpSockAddrLen* sont ignorés pour SOCK_STREAM douilles.

Pour les prises de datagram, les données sont extraites du premier datagram enqueued, jusqu’à la taille du tampon fourni. Si le datagram est plus grand que le tampon fourni, le tampon est rempli `ReceiveFromEx` de la première partie du message, les données excédentaires sont perdues et renvoie une valeur de SOCKET_ERROR avec le code d’erreur défini à WSAEMSGSIZE.

Si *lpSockAddr* n’est paszero, et que la prise est de type SOCK_DGRAM, l’adresse réseau de la prise qui a envoyé les données est copiée sur la structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) correspondante. La valeur soulignée par *lpSockAddrLen* est parasélisée à la taille de cette structure, et est modifiée au retour pour indiquer la taille réelle de l’adresse stockée là-bas. Si aucune donnée entrante n’est `ReceiveFromEx` disponible à la prise, l’appel attend que les données arrivent à moins que la prise ne soit nonblocking. Dans ce cas, une valeur de SOCKET_ERROR est retournée avec le code d’erreur réglé sur WSAEWOULDBLOCK. Le `OnReceive` rappel peut être utilisé pour déterminer quand plus de données arrivent.

Si la prise est de type SOCK_STREAM et le côté distant a `ReceiveFromEx` arrêté la connexion gracieusement, un sera complet immédiatement avec 0 octets reçus.

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket::Envoyer

Appelez cette fonction de membre pour envoyer des données sur une prise connectée.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Un tampon contenant les données à transmettre.

*nBufLen (en)*<br/>
La longueur des données dans *lpBuf* dans les octets.

*nFlags*<br/>
Spécifie la façon dont l’appel est fait. La sémantique de cette fonction est déterminée par les options de prise et le *paramètre nFlags.* Ce dernier est construit en combinant l’une des valeurs suivantes avec l’opérateur **C OU** :

- MSG_DONTROUTE précise que les données ne doivent pas faire l’objet d’un itinéraire. Un fournisseur windows Sockets peut choisir d’ignorer ce drapeau.

- MSG_OOB Envoyer des données hors bande (SOCK_STREAM seulement).

### <a name="return-value"></a>Valeur de retour

En cas d’erreur, `Send` renvoie le nombre total de caractères envoyés. (Notez que cela peut être inférieur au nombre indiqué par *nBufLen*.) Dans le cas contraire, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES L’adresse demandée est une adresse de radiodiffusion, mais le drapeau approprié n’a pas été fixé.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAEFAULT *L’argument lpBuf* n’est pas dans une partie valide de l’espace d’adresse utilisateur.

- WSAENETRESET La connexion doit être réinitialisée parce que la mise en œuvre de Windows Sockets l’a abandonnée.

- WSAENOBUFS La implémentation de Windows Sockets signale une impasse tampon.

- WSAENOTCONN La prise n’est pas connectée.

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais la prise n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN La prise a été arrêtée; il n’est `Send` pas possible de `ShutDown` faire appel à une prise après a été invoqué avec *nHow* réglé à 1 ou 2.

- WSAEWOULDBLOCK La prise est marquée comme non-blocage et l’opération demandée bloquerait.

- WSAEMSGSIZE La prise est de type SOCK_DGRAM, et le datagram est plus grand que le maximum pris en charge par la mise en œuvre de Windows Sockets.

- WSAEINVAL La prise n’a `Bind`pas été liée avec .

- WSAECONNABORTED Le circuit virtuel a été avorté en raison d’un délai d’attente ou d’une autre défaillance.

- WSAECONNRESET Le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

`Send`est utilisé pour écrire des données sortantes sur les prises de flux ou de datagram connectées. Pour les prises de datagram, il faut prendre soin de ne pas dépasser la taille `iMaxUdpDg` maximale des paquets IP `AfxSocketInit`des sous-filets sous-jacents, qui est donnée par l’élément de la structure [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) retourné par . Si les données sont trop longues pour passer atomiquement à travers le protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée via `GetLastError`, et aucune donnée n’est transmise.

Notez que pour une prise de `Send` datagram, l’achèvement réussi d’un n’indique pas que les données ont été livrées avec succès.

Sur `CAsyncSocket` les objets de type SOCK_STREAM, le nombre d’octets écrits peut être compris entre 1 et la longueur demandée, en fonction de la disponibilité des tampons sur les hôtes locaux et étrangers.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CAsyncSocket::OnSend](#onsend).

## <a name="casyncsocketsendto"></a><a name="sendto"></a>CAsyncSocket::SendTo

Appelez cette fonction de membre pour envoyer des données à une destination spécifique.

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
Un tampon contenant les données à transmettre.

*nBufLen (en)*<br/>
La longueur des données dans *lpBuf* dans les octets.

*nHostPort (nHostPort)*<br/>
Le port identifiant l’application de prise.

*lpszHostAddress*<br/>
L’adresse réseau de la prise à laquelle cet objet est connecté : un nom de machine tel que « ftp.microsoft.com » ou un numéro pointillé tel que « 128.56.22.8 ».

*nFlags*<br/>
Spécifie la façon dont l’appel est fait. La sémantique de cette fonction est déterminée par les options de prise et le *paramètre nFlags.* Ce dernier est construit en combinant l’une des valeurs suivantes avec l’opérateur **C OU** :

- MSG_DONTROUTE précise que les données ne doivent pas faire l’objet d’un itinéraire. Un fournisseur windows Sockets peut choisir d’ignorer ce drapeau.

- MSG_OOB Envoyer des données hors bande (SOCK_STREAM seulement).

*lpSockAddr*<br/>
Un pointeur vers une structure [SOCKADDR](/windows/win32/winsock/sockaddr-2) qui contient l’adresse de la prise cible.

*nSockAddrLen (en)*<br/>
La longueur de l’adresse en *lpSockAddr* dans les octets.

### <a name="return-value"></a>Valeur de retour

En cas d’erreur, `SendTo` renvoie le nombre total de caractères envoyés. (Notez que cela peut être inférieur au nombre indiqué par *nBufLen*.) Dans le cas contraire, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES L’adresse demandée est une adresse de radiodiffusion, mais le drapeau approprié n’a pas été fixé.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAEFAULT Les paramètres *lpBuf* ou *lpSockAddr* ne font pas partie de l’espace d’adresse utilisateur, ou *l’argument lpSockAddr* est trop petit (moins que la taille d’une structure [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL Le nom de l’hôte est invalide.

- WSAENETRESET La connexion doit être réinitialisée parce que la mise en œuvre de Windows Sockets l’a abandonnée.

- WSAENOBUFS La implémentation de Windows Sockets signale une impasse tampon.

- WSAENOTCONN La prise n’est pas connectée (SOCK_STREAM seulement).

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais la prise n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN La prise a été arrêtée; il n’est `SendTo` pas possible de `ShutDown` faire appel à une prise après a été invoqué avec *nHow* réglé à 1 ou 2.

- WSAEWOULDBLOCK La prise est marquée comme non-blocage et l’opération demandée bloquerait.

- WSAEMSGSIZE La prise est de type SOCK_DGRAM, et le datagram est plus grand que le maximum pris en charge par la mise en œuvre de Windows Sockets.

- WSAECONNABORTED Le circuit virtuel a été avorté en raison d’un délai d’attente ou d’une autre défaillance.

- WSAECONNRESET Le circuit virtuel a été réinitialisé par le côté distant.

- WSAEADDRNOTAVAIL L’adresse spécifiée n’est pas disponible à partir de la machine locale.

- Les adresses WSAEAFNOSUPPORT dans la famille spécifiée ne peuvent pas être utilisées avec cette prise.

- WSAEDESTADDRREQ Une adresse de destination est requise.

- WSAENETUNREACH Le réseau ne peut pas être atteint à partir de cet hôte pour le moment.

### <a name="remarks"></a>Notes

`SendTo`est utilisé sur datagram ou des prises de flux et est utilisé pour écrire des données sortantes sur une prise. Pour les prises de datagram, il faut prendre soin de ne pas dépasser la taille `iMaxUdpDg` maximale des paquets IP des sous-filets sous-jacents, qui est donnée par l’élément de la structure [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) rempli par [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si les données sont trop longues pour passer atomiquement à travers le protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée, et aucune donnée n’est transmise.

Notez que l’achèvement réussi d’un `SendTo` n’indique pas que les données ont été livrées avec succès.

`SendTo`n’est utilisé que sur une prise de SOCK_DGRAM pour envoyer un datagram à une prise spécifique identifiée par le *paramètre lpSockAddr.*

Pour envoyer une émission (sur un SOCK_DGRAM seulement), l’adresse dans le paramètre *lpSockAddr* doit être construite à l’aide de l’adresse IP spéciale INADDR_BROADCAST (définie dans le fichier d’en-tête Windows Sockets WINSOCK. H) avec le numéro de port prévu. Ou, si le paramètre *lpszHostAddress* est NULL, la prise est configurée pour diffusion. Il est généralement déconseillé qu’un datagram de radiodiffusion dépasse la taille à laquelle la fragmentation peut se produire, ce qui implique que la partie de données du datagram (à l’exclusion des en-têtes) ne doit pas dépasser 512 octets.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket::SendToEx](#sendtoex).

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket::SendToEx

Appelez cette fonction de membre pour envoyer des données à une destination spécifique (gère les adresses IPv6).

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
Un tampon contenant les données à transmettre.

*nBufLen (en)*<br/>
La longueur des données dans *lpBuf* dans les octets.

*nHostPort (nHostPort)*<br/>
Le port identifiant l’application de prise.

*lpszHostAddress*<br/>
L’adresse réseau de la prise à laquelle cet objet est connecté : un nom de machine tel que « ftp.microsoft.com » ou un numéro pointillé tel que « 128.56.22.8 ».

*nFlags*<br/>
Spécifie la façon dont l’appel est fait. La sémantique de cette fonction est déterminée par les options de prise et le *paramètre nFlags.* Ce dernier est construit en combinant l’une des valeurs suivantes avec l’opérateur **C OU** :

- MSG_DONTROUTE précise que les données ne doivent pas faire l’objet d’un itinéraire. Un fournisseur windows Sockets peut choisir d’ignorer ce drapeau.

- MSG_OOB Envoyer des données hors bande (SOCK_STREAM seulement).

### <a name="return-value"></a>Valeur de retour

En cas d’erreur, `SendToEx` renvoie le nombre total de caractères envoyés. (Notez que cela peut être inférieur au nombre indiqué par *nBufLen*.) Dans le cas contraire, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES L’adresse demandée est une adresse de radiodiffusion, mais le drapeau approprié n’a pas été fixé.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAEFAULT Les paramètres *lpBuf* ou *lpSockAddr* ne font pas partie de l’espace d’adresse utilisateur, ou *l’argument lpSockAddr* est trop petit (moins que la taille d’une structure [SOCKADDR).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL Le nom de l’hôte est invalide.

- WSAENETRESET La connexion doit être réinitialisée parce que la mise en œuvre de Windows Sockets l’a abandonnée.

- WSAENOBUFS La implémentation de Windows Sockets signale une impasse tampon.

- WSAENOTCONN La prise n’est pas connectée (SOCK_STREAM seulement).

- WSAENOTSOCK Le descripteur n’est pas une prise.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais la prise n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN La prise a été arrêtée; il n’est `SendToEx` pas possible de `ShutDown` faire appel à une prise après a été invoqué avec *nHow* réglé à 1 ou 2.

- WSAEWOULDBLOCK La prise est marquée comme non-blocage et l’opération demandée bloquerait.

- WSAEMSGSIZE La prise est de type SOCK_DGRAM, et le datagram est plus grand que le maximum pris en charge par la mise en œuvre de Windows Sockets.

- WSAECONNABORTED Le circuit virtuel a été avorté en raison d’un délai d’attente ou d’une autre défaillance.

- WSAECONNRESET Le circuit virtuel a été réinitialisé par le côté distant.

- WSAEADDRNOTAVAIL L’adresse spécifiée n’est pas disponible à partir de la machine locale.

- Les adresses WSAEAFNOSUPPORT dans la famille spécifiée ne peuvent pas être utilisées avec cette prise.

- WSAEDESTADDRREQ Une adresse de destination est requise.

- WSAENETUNREACH Le réseau ne peut pas être atteint à partir de cet hôte pour le moment.

### <a name="remarks"></a>Notes

Cette méthode est la même que [CAsyncSocket::SendTo](#sendto) sauf qu’il gère les adresses IPv6 ainsi que les protocoles plus anciens.

`SendToEx`est utilisé sur datagram ou des prises de flux et est utilisé pour écrire des données sortantes sur une prise. Pour les prises de datagram, il faut prendre soin de ne pas dépasser la taille `iMaxUdpDg` maximale des paquets IP des sous-filets sous-jacents, qui est donnée par l’élément de la structure [WSADATA](/windows/win32/api/winsock2/ns-winsock2-wsadata) rempli par [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si les données sont trop longues pour passer atomiquement à travers le protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée, et aucune donnée n’est transmise.

Notez que l’achèvement réussi d’un `SendToEx` n’indique pas que les données ont été livrées avec succès.

`SendToEx`n’est utilisé que sur une prise de SOCK_DGRAM pour envoyer un datagram à une prise spécifique identifiée par le *paramètre lpSockAddr.*

Pour envoyer une émission (sur un SOCK_DGRAM seulement), l’adresse dans le paramètre *lpSockAddr* doit être construite à l’aide de l’adresse IP spéciale INADDR_BROADCAST (définie dans le fichier d’en-tête Windows Sockets WINSOCK. H) avec le numéro de port prévu. Ou, si le paramètre *lpszHostAddress* est NULL, la prise est configurée pour diffusion. Il est généralement déconseillé qu’un datagram de radiodiffusion dépasse la taille à laquelle la fragmentation peut se produire, ce qui implique que la partie de données du datagram (à l’exclusion des en-têtes) ne doit pas dépasser 512 octets.

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket::SetSockOpt

Appelez cette fonction de membre pour définir une option de prise.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Paramètres

*nOptionName (en)*<br/>
L’option de prise pour laquelle la valeur doit être définie.

*lpOptionValue*<br/>
Un pointeur à la mémoire tampon dans laquelle la valeur de l’option demandée est fournie.

*nOptionLen*<br/>
La taille du tampon *lpOptionValue* dans les octets.

*nLevel (en)*<br/>
le niveau auquel l’option est définie; les seuls niveaux pris en charge sont SOL_SOCKET et IPPROTO_TCP.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *lpOptionValue* n’est pas dans une partie valide de l’espace d’adresse du processus.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAEINVAL *nLevel nLevel n’est* pas valide, ou les informations dans *lpOptionValue* ne sont pas valides.

- WSAENETRESET Connection a été chronométré lorsque SO_KEEPALIVE est réglée.

- WSAENOPROTOOPT L’option est inconnue ou non supportée. En particulier, SO_BROADCAST n’est pas pris en charge sur les prises de SOCK_STREAM de type, tandis que les SO_DONTLINGER, les SO_KEEPALIVE, les SO_LINGER et les SO_OOBINLINE ne sont pas pris en charge sur des prises de type SOCK_DGRAM.

- WSAENOTCONN Connexion a été réinitialisée lorsque SO_KEEPALIVE est définie.

- WSAENOTSOCK Le descripteur n’est pas une prise.

### <a name="remarks"></a>Notes

`SetSockOpt`définit la valeur actuelle d’une option de prise associée à une prise de tout type, dans n’importe quel état. Bien que les options puissent exister à plusieurs niveaux de protocole, cette spécification ne définit que les options qui existent au niveau le plus élevé de « prise ». Les options affectent les opérations de prise, telles que la réception de données accélérées dans le flux de données normal, la question de savoir si les messages de diffusion peuvent être envoyés sur la prise, et ainsi de suite.

Il existe deux types d’options de prise : les options Boolean qui permettent ou désactivent une fonctionnalité ou un comportement, et des options qui nécessitent une valeur ou une structure d’intégrage. Pour activer une option Boolean, *lpOptionValue* pointe vers un intégrateur nonzero. Pour désactiver l’option *lpOptionValue* pointe vers un intégrant égal à zéro. *nOptionLen* devrait être `sizeof(BOOL)` égal pour les options Boolean. Pour d’autres options, *lpOptionValue* pointe vers l’intégrant ou la structure qui contient la valeur désirée pour l’option, et *nOptionLen* est la longueur de l’intégrant ou de la structure.

SO_LINGER contrôle les mesures prises lorsque des données non disponibles sont `Close` alignées sur une prise et la fonction est appelée pour fermer la prise.

Par défaut, une prise ne peut pas être liée (voir [Bind)](#bind)à une adresse locale qui est déjà utilisée. À l’occasion, cependant, il peut être souhaitable de « réutiliser » une adresse de cette façon. Étant donné que chaque connexion est identifiée de façon unique par la combinaison d’adresses locales et distantes, il n’y a aucun problème avec avoir deux prises liées à la même adresse locale tant que les adresses distantes sont différentes.

Pour informer l’implémentation `Bind` de Windows Sockets qu’un appel sur une prise ne doit pas être refusé parce que l’adresse souhaitée est `Bind` déjà utilisée par une autre prise, l’application doit définir l’option SO_REUSEADDR prise pour la prise avant d’émettre l’appel. Notez que l’option n’est `Bind` interprétée qu’au moment de l’appel : il n’est donc pas nécessaire (mais inoffensif) de définir `Bind` l’option sur une prise qui ne doit pas être liée à une adresse existante, et le réglage ou la réinitialisation de l’option après l’appel n’a aucun effet sur cette prise ou toute autre prise.

Une application peut demander que la mise en œuvre de Windows Sockets permette l’utilisation de paquets « en cours » sur les connexions du Protocole de contrôle de transmission (TCP) en allumant l’option de prise SO_KEEPALIVE. Une implémentation de Windows Sockets n’a pas besoin de prendre en charge l’utilisation de keep-alives: si elle le fait, la sémantique précise sont spécifiques à la mise en œuvre, mais devrait se conformer à la section 4.2.3.6 de RFC 1122: "Exigences pour les hôtes Internet - Couches de communication." Si une connexion est supprimée à la suite de "keep-alives", le code d’erreur WSAENETRESET est retourné à tous les appels en cours sur la prise, et tous les appels ultérieurs échoueront avec WSAENOTCONN.

L’option TCP_NODELAY désactive l’algorithme Nagle. L’algorithme Nagle est utilisé pour réduire le nombre de petits paquets envoyés par un hôte en tamponnant les données d’envoi non reconnues jusqu’à ce qu’un paquet grandeur nature puisse être envoyé. Cependant, pour certaines applications cet algorithme peut entraver les performances, et TCP_NODELAY peut être utilisé pour l’éteindre. Les auteurs d’applications ne doivent pas établir de TCP_NODELAY à moins que l’impact de cette mesure ne soit bien compris et souhaité, car la mise en TCP_NODELAY peut avoir un impact négatif important sur les performances du réseau. TCP_NODELAY is the only supported socket option which uses level IPPROTO_TCP; toutes les autres options utilisent le niveau SOL_SOCKET.

Certaines implémentations de Windows Sockets fournissent des informations de débbug de sortie si l’option SO_DEBUG est définie par une application.

Les options suivantes `SetSockOpt`sont prises en charge pour . Le type identifie le type de données traitées par *lpOptionValue*.

|Value|Type|Signification|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|Autoriser la transmission de messages de diffusion sur la prise.|
|SO_DEBUG|BOOL|Enregistrer les informations de débogage.|
|SO_DONTLINGER|BOOL|Ne bloquez `Close` pas l’attente d’envoi de données non disponibles. La définition de cette option équivaut `l_onoff` à définir SO_LINGER avec un ensemble à zéro.|
|SO_DONTROUTE|BOOL|Ne pas itinéraire: envoyer directement à l’interface.|
|SO_KEEPALIVE|BOOL|Envoyez des garder en vie.|
|SO_LINGER|`struct LINGER`|S’attardez sur `Close` si des données non ense de suite sont présentes.|
|SO_OOBINLINE|BOOL|Recevez des données hors bande dans le flux de données normal.|
|SO_RCVBUF|**int**|Spécifier la taille du tampon pour les réceptions.|
|SO_REUSEADDR|BOOL|Laissez la prise être liée à une adresse qui est déjà utilisée. (Voir [Bind](#bind).)|
|SO_SNDBUF|**int**|Spécifier la taille du tampon pour les envois.|
|TCP_NODELAY|BOOL|Désactive l'algorithme Nagle pour la fusion des envois.|

Berkeley Software Distribution (BSD) `SetSockOpt` options non prises en charge sont les suivantes:

|Value|Type|Signification|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Socket est à l’écoute|
|SO_ERROR|**int**|Obtenez le statut d’erreur et clair.|
|SO_RCVLOWAT|**int**|Recevez une faible marque d’eau.|
|SO_RCVTIMEO|**int**|Délai d’attente de réception|
|SO_SNDLOWAT|**int**|Envoyez une marque basse d’eau.|
|SO_SNDTIMEO|**int**|Envoyez un délai d’attente.|
|SO_TYPE|**int**|Type de la prise.|
|IP_OPTIONS||Définissez le champ des options en en-tête IP.|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket::ShutDown

Appelez cette fonction de membre pour désactiver envoie, reçoit, ou les deux sur la prise.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Paramètres

*Nhow*<br/>
Un drapeau qui décrit quels types d’opérations ne seront plus autorisés, en utilisant les valeurs énumérées suivantes :

- **reçoit 0**

- **envoie 1**

- **les deux 2**

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction de membre :

- WSANOTINITIALISED Un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN La mise en œuvre de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL *nComment* n’est pas valide.

- WSAEINPROGRESS Une opération de blocage de Windows Sockets est en cours.

- WSAENOTCONN La prise n’est pas connectée (SOCK_STREAM seulement).

- WSAENOTSOCK Le descripteur n’est pas une prise.

### <a name="remarks"></a>Notes

`ShutDown`est utilisé sur tous les types de prises pour désactiver la réception, la transmission, ou les deux. Si *nHow* est 0, les réceptions ultérieures sur la prise seront refusées. Cela n’a aucun effet sur les couches de protocole inférieure.

Pour le Protocole de contrôle de transmission (TCP), la fenêtre TCP n’est pas modifiée et les données entrantes seront acceptées (mais non reconnues) jusqu’à ce que la fenêtre soit épuisée. Pour le protocole De datagram utilisateur (UDP), les datagram entrants sont acceptés et mis en file d’attente. En aucun cas un paquet d’erreur ICMP ne sera généré. Si *nHow* est 1, les envois suivants sont refusés. Pour les prises TCP, un FIN sera envoyé. Réglage *nComment* à 2 désactive à la fois envoie et reçoit comme décrit ci-dessus.

Notez `ShutDown` que ne ferme pas la prise, et les ressources `Close` attachées à la prise ne seront pas libérées jusqu’à ce qu’elle soit appelée. Une application ne doit pas compter sur la possibilité de réutiliser une prise une fois qu’elle a été arrêtée. En particulier, une implémentation de Windows Sockets n’est pas nécessaire pour prendre en charge l’utilisation d’une `Connect` telle prise.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketsocket"></a><a name="socket"></a>CASyncSocket::Socket

Alloue une poignée de prise.

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>Paramètres

*nSocketType (en)*<br/>
Spécifie `SOCK_STREAM` ou `SOCK_DGRAM`.

*Levent*<br/>
Un petit-s qui spécifie une combinaison d’événements réseau dans lesquels l’application est intéressée.

- `FD_READ`: Vous voulez recevoir une notification de préparation à la lecture.

- `FD_WRITE`: Vous voulez recevoir une notification de préparation à l’écriture.

- `FD_OOB`: Vous souhaitez recevoir une notification de l’arrivée des données hors bande.

- `FD_ACCEPT`: Vous souhaitez recevoir une notification des connexions entrantes.

- `FD_CONNECT`: Vous souhaitez recevoir une notification de connexion terminée.

- `FD_CLOSE`: Vous voulez recevoir une notification de fermeture de prise.

*nProtocolType (en)*<br/>
Protocole à utiliser avec la prise qui est spécifique à la famille d’adresse indiquée.

*nAddressFormat (en)*<br/>
Adressez-vous aux spécifications familiales.

### <a name="return-value"></a>Valeur de retour

Retours `TRUE` sur `FALSE` le succès, sur l’échec.

### <a name="remarks"></a>Notes

Cette méthode alloue une poignée de prise. Il n’appelle pas [CAsyncSocket::Bind](#bind) pour lier la prise à `Bind` une adresse spécifiée, de sorte que vous devez appeler plus tard pour lier la prise à une adresse spécifiée. Vous pouvez utiliser [CAsyncSocket::SetSockOpt](#setsockopt) pour définir l’option de prise avant qu’elle ne soit liée.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSocket, classe](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
