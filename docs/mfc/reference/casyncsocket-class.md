---
title: CAsyncSocket (classe)
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
ms.openlocfilehash: 4e14052d400268a8852298113ba9b51fda713dc8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418887"
---
# <a name="casyncsocket-class"></a>CAsyncSocket (classe)

Représente un socket Windows, un point de terminaison de communication réseau.

## <a name="syntax"></a>Syntaxe

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CAsyncSocket :: CAsyncSocket](#casyncsocket)|Construit un objet `CAsyncSocket`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CAsyncSocket :: Accept](#accept)|Accepte une connexion sur le Socket.|
|[CAsyncSocket :: AsyncSelect](#asyncselect)|Demande une notification d’événement pour le Socket.|
|[CAsyncSocket :: Attach](#attach)|Attache un handle de socket à un objet `CAsyncSocket`.|
|[CAsyncSocket :: bind](#bind)|Associe une adresse locale au socket.|
|[CAsyncSocket :: Close](#close)|Ferme le Socket.|
|[CAsyncSocket :: Connect](#connect)|Établit une connexion à un socket homologue.|
|[CAsyncSocket :: Create](#create)|Crée un Socket.|
|[CAsyncSocket ::D Etach](#detach)|Détache un handle de socket d’un objet `CAsyncSocket`.|
|[CAsyncSocket :: FromHandle](#fromhandle)|Retourne un pointeur vers un objet `CAsyncSocket`, à partir d’un handle de Socket.|
|[CAsyncSocket :: GetLastError](#getlasterror)|Obtient l’état d’erreur pour la dernière opération qui a échoué.|
|[CAsyncSocket :: GetPeerName](#getpeername)|Obtient l’adresse du socket homologue auquel le socket est connecté.|
|[CAsyncSocket :: GetPeerNameEx](#getpeernameex)|Obtient l’adresse du socket homologue auquel le socket est connecté (gère les adresses IPv6).|
|[CAsyncSocket :: GetSockName](#getsockname)|Obtient le nom local d’un Socket.|
|[CAsyncSocket :: GetSockNameEx](#getsocknameex)|Obtient le nom local d’un socket (gère les adresses IPv6).|
|[CAsyncSocket :: GetSockOpt](#getsockopt)|Récupère une option de Socket.|
|[CAsyncSocket :: IOCtl](#ioctl)|Contrôle le mode du Socket.|
|[CAsyncSocket :: Listen](#listen)|Établit un socket pour écouter les demandes de connexion entrante.|
|[CAsyncSocket :: Receive](#receive)|Reçoit des données à partir du Socket.|
|[CAsyncSocket :: ReceiveFrom](#receivefrom)|Reçoit un datagramme et stocke l’adresse source.|
|[CAsyncSocket :: ReceiveFromEx](#receivefromex)|Reçoit un datagramme et stocke l’adresse source (gère les adresses IPv6).|
|[CAsyncSocket :: Send](#send)|Envoie des données à un socket connecté.|
|[CAsyncSocket :: SendTo](#sendto)|Envoie des données vers une destination spécifique.|
|[CAsyncSocket :: SendToEx](#sendtoex)|Envoie des données vers une destination spécifique (gère les adresses IPv6).|
|[CAsyncSocket :: SetSockOpt](#setsockopt)|Définit une option de Socket.|
|[CAsyncSocket :: ShutDown](#shutdown)|Désactive les appels de `Send` et/ou de `Receive` sur le Socket.|
|[CASyncSocket :: Socket](#socket)|Alloue un handle de Socket.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[CAsyncSocket :: OnAccept](#onaccept)|Avertit un socket d’écoute qu’il peut accepter les demandes de connexion en attente en appelant `Accept`.|
|[CAsyncSocket :: OnClose](#onclose)|Avertit un socket que le socket auquel il est connecté s’est fermé.|
|[CAsyncSocket :: OnConnect](#onconnect)|Avertit un socket de connexion que la tentative de connexion est terminée, qu’elle soit réussie ou erronée.|
|[CAsyncSocket :: OnOutOfBandData](#onoutofbanddata)|Avertit un socket de réception qu’il y a des données hors bande à lire sur le socket, généralement un message urgent.|
|[CAsyncSocket :: OnReceive](#onreceive)|Avertit un socket d’écoute qu’il y a des données à récupérer en appelant `Receive`.|
|[CAsyncSocket :: OnSend](#onsend)|Avertit un socket qu’il peut envoyer des données en appelant `Send`.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|----------|-----------------|
|[CAsyncSocket :: Operator =](#operator_eq)|Assigne une nouvelle valeur à un objet `CAsyncSocket`.|
|[CAsyncSocket :: Operator, SOCKET](#operator_socket)|Utilisez cet opérateur pour récupérer le handle de SOCKET de l’objet `CAsyncSocket`.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CAsyncSocket :: m_hSocket](#m_hsocket)|Indique le handle de SOCKET attaché à cet objet `CAsyncSocket`.|

## <a name="remarks"></a>Notes

La classe `CAsyncSocket` encapsule l’API des fonctions de socket Windows, en fournissant une abstraction orientée objet pour les programmeurs qui souhaitent utiliser Windows Sockets conjointement avec MFC.

Cette classe est basée sur l’hypothèse que vous comprenez les communications réseau. Vous êtes chargé de gérer le blocage, les différences d’ordre d’octet et les conversions entre des chaînes de jeu de caractères multioctets (MBCS) et Unicode. Si vous souhaitez une interface plus pratique qui gère ces problèmes pour vous, consultez la classe [CSocket](../../mfc/reference/csocket-class.md).

Pour utiliser un objet `CAsyncSocket`, appelez son constructeur, puis appelez la fonction [Create](#create) pour créer le handle de Socket sous-jacent (type `SOCKET`), à l’exception des sockets acceptés. Pour un socket serveur, appelez la fonction membre [Listen](#listen) , et pour un socket client, appelez la fonction membre [Connect](#connect) . Le socket serveur doit appeler la fonction [Accept](#accept) lors de la réception d’une demande de connexion. Utilisez les fonctions de `CAsyncSocket` restantes pour effectuer des communications entre les sockets. Une fois l’opération terminée, détruisez l’objet `CAsyncSocket` s’il a été créé sur le tas. le destructeur appelle automatiquement la fonction [Close](#close) . Le type de données SOCKET est décrit dans l’article [Windows Sockets : Background](../../mfc/windows-sockets-background.md).

> [!NOTE]
>  Lorsque vous utilisez des sockets MFC dans des threads secondaires dans une application MFC liée de manière statique, vous devez appeler `AfxSocketInit` dans chaque thread qui utilise des sockets pour initialiser les bibliothèques de Sockets. Par défaut, `AfxSocketInit` est appelé uniquement dans le thread principal.

Pour plus d’informations, consultez [Windows Sockets : utilisation de la classe CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) et des Articles connexes., ainsi que l' [API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Spécifications

**En-tête :** AfxSock. h

##  <a name="accept"></a>CAsyncSocket :: Accept

Appelez cette fonction membre pour accepter une connexion sur un Socket.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Paramètres

*rConnectedSocket*<br/>
Référence identifiant un nouveau socket qui est disponible pour la connexion.

*lpSockAddr*<br/>
Pointeur vers une structure [sockaddr](/windows/win32/winsock/sockaddr-2) qui reçoit l’adresse du socket de connexion, tel qu’il est connu sur le réseau. Le format exact de l’argument *lpSockAddr* est déterminé par la famille d’adresses établie lors de la création du Socket. Si *lpSockAddr* et/ou *lpSockAddrLen* sont égaux à null, aucune information sur l’adresse distante du socket accepté n’est retournée.

*lpSockAddrLen*<br/>
Pointeur vers la longueur de l’adresse dans *lpSockAddr* en octets. *LpSockAddrLen* est un paramètre de résultat de valeur : il doit initialement contenir la quantité d’espace vers laquelle pointe *lpSockAddr*; en cas de retour, elle contient la longueur réelle (en octets) de l’adresse retournée.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT l’argument *lpSockAddrLen* est trop petit (inférieur à la taille d’une structure [sockaddr](/windows/win32/winsock/sockaddr-2) ).

- WSAEINPROGRESS un appel de blocage de Windows Sockets est en cours.

- WSAEINVAL `Listen` n’a pas été appelé avant d’accepter.

- WSAEMFILE la file d’attente est vide lors de l’entrée à accepter et aucun descripteur n’est disponible.

- WSAENOBUFS aucun espace de mémoire tampon n’est disponible.

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEOPNOTSUPP le socket référencé n’est pas un type qui prend en charge le service orienté connexion.

- WSAEWOULDBLOCK le socket est marqué comme non bloquant et aucune connexion n’est présente pour être acceptée.

### <a name="remarks"></a>Notes

Cette routine extrait la première connexion de la file d’attente des connexions en attente, crée un nouveau socket avec les mêmes propriétés que ce socket et l’attache à *rConnectedSocket*. Si aucune connexion en attente n’est présente dans la file d’attente, `Accept` retourne zéro et `GetLastError` retourne une erreur. Le socket accepté ( *rConnectedSocket)* ne peut pas être utilisé pour accepter plus de connexions. Le socket d’origine reste ouvert et à l’écoute.

L’argument *lpSockAddr* est un paramètre de résultat qui est rempli avec l’adresse du socket de connexion, tel qu’il est connu de la couche de communication. `Accept` est utilisé avec les types de sockets basés sur une connexion tels que SOCK_STREAM.

##  <a name="asyncselect"></a>CAsyncSocket :: AsyncSelect

Appelez cette fonction membre pour demander une notification d’événement pour un Socket.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Paramètres

*lEvent*<br/>
Masque de masque qui spécifie une combinaison d’événements réseau qui intéressent l’application.

- FD_READ souhaitez recevoir une notification de préparation pour la lecture.

- FD_WRITE souhaitez recevoir une notification lorsque les données sont disponibles pour la lecture.

- FD_OOB souhaitez recevoir la notification de l’arrivée des données hors bande.

- FD_ACCEPT souhaitez recevoir la notification des connexions entrantes.

- FD_CONNECT souhaitez recevoir la notification des résultats de la connexion.

- FD_CLOSE souhaitez recevoir une notification lorsqu’un socket a été fermé par un homologue.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL indique que l’un des paramètres spécifiés n’était pas valide.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour spécifier les fonctions de notification de rappel MFC qui seront appelées pour le Socket. `AsyncSelect` définit automatiquement ce socket en mode non bloquant. Pour plus d’informations, consultez l’article [Windows Sockets : notifications de socket](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="attach"></a>CAsyncSocket :: Attach

Appelez cette fonction membre pour attacher le handle *hSocket* à un objet `CAsyncSocket`.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle vers un Socket.

*lEvent*<br/>
Masque de masque qui spécifie une combinaison d’événements réseau qui intéressent l’application.

- FD_READ souhaitez recevoir une notification de préparation pour la lecture.

- FD_WRITE souhaitez recevoir une notification lorsque les données sont disponibles pour la lecture.

- FD_OOB souhaitez recevoir la notification de l’arrivée des données hors bande.

- FD_ACCEPT souhaitez recevoir la notification des connexions entrantes.

- FD_CONNECT souhaitez recevoir la notification des résultats de la connexion.

- FD_CLOSE souhaitez recevoir une notification lorsqu’un socket a été fermé par un homologue.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la fonction aboutit.

### <a name="remarks"></a>Notes

Le handle de SOCKET est stocké dans le membre de données [m_hSocket](#m_hsocket) de l’objet.

##  <a name="bind"></a>CAsyncSocket :: bind

Appelez cette fonction membre pour associer une adresse locale au socket.

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
Port identifiant l’application de Socket.

*lpszSocketAddress*<br/>
L’adresse réseau, un nombre en pointillés tel que « 128.56.22.8 ». Le passage de la chaîne NULL pour ce paramètre indique que l’instance de `CAsyncSocket` doit écouter l’activité des clients sur toutes les interfaces réseau.

*lpSockAddr*<br/>
Pointeur vers une structure [sockaddr](/windows/win32/winsock/sockaddr-2) qui contient l’adresse à assigner à ce Socket.

*nSockAddrLen*<br/>
Longueur, en octets, de l’adresse dans *lpSockAddr* .

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). La liste suivante décrit quelques-unes des erreurs qui peuvent être retournées. Pour obtenir une liste complète, consultez [codes d’erreur de Windows Sockets](/windows/win32/winsock/windows-sockets-error-codes-2).

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE l’adresse spécifiée est déjà utilisée. (Consultez l’option SO_REUSEADDR Socket sous [SetSockOpt](#setsockopt).)

- WSAEFAULT l’argument *nSockAddrLen* est trop petit (inférieur à la taille d’une structure [sockaddr](/windows/win32/winsock/sockaddr-2) ).

- WSAEINPROGRESS un appel de blocage de Windows Sockets est en cours.

- WSAEAFNOSUPPORT la famille d’adresses spécifiée n’est pas prise en charge par ce port.

- WSAEINVAL le socket est déjà lié à une adresse.

- WSAENOBUFS pas assez de mémoires tampons disponibles, trop de connexions.

- WSAENOTSOCK le descripteur n’est pas un Socket.

### <a name="remarks"></a>Notes

Cette routine est utilisée sur un socket de datagramme ou de flux non connecté, avant les appels `Connect` ou `Listen` suivants. Avant de pouvoir accepter les demandes de connexion, un socket de serveur d’écoute doit sélectionner un numéro de port et le rendre connu aux sockets Windows en appelant `Bind`. `Bind` établit l’association locale (adresse hôte/numéro de port) du socket en affectant un nom local à un socket sans nom.

##  <a name="casyncsocket"></a>CAsyncSocket :: CAsyncSocket

Construit un objet Socket vide.

```
CAsyncSocket();
```

### <a name="remarks"></a>Notes

Après avoir construit l’objet, vous devez appeler sa fonction membre `Create` pour créer la structure de données de SOCKET et lier son adresse. (Côté serveur d’une communication Windows Sockets, lorsque le socket d’écoute crée un socket à utiliser dans l’appel `Accept`, vous n’appelez pas `Create` pour ce Socket.)

##  <a name="close"></a>CAsyncSocket :: Close

Ferme le Socket.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Cette fonction libère le descripteur de socket afin que d’autres références à ce dernier échouent avec l’erreur WSAENOTSOCK. S’il s’agit de la dernière référence au Socket sous-jacent, les informations de nom et les données mises en file d’attente associées sont ignorées. Le destructeur de l’objet Socket appelle `Close` pour vous.

Pour `CAsyncSocket`, mais pas pour `CSocket`, la sémantique des `Close` est affectée par les options de socket SO_LINGER et SO_DONTLINGER. Pour plus d’informations, consultez fonction membre `GetSockOpt`.

##  <a name="connect"></a>CAsyncSocket :: Connect

Appelez cette fonction membre pour établir une connexion à un socket de flux ou de datagramme non connecté.

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
Adresse réseau du socket auquel cet objet est connecté : un nom d’ordinateur tel que « ftp.microsoft.com » ou un nombre en pointillés tel que « 128.56.22.8 ».

*nHostPort*<br/>
Port identifiant l’application de Socket.

*lpSockAddr*<br/>
Pointeur vers une structure [sockaddr](/windows/win32/winsock/sockaddr-2) qui contient l’adresse du socket connecté.

*nSockAddrLen*<br/>
Longueur, en octets, de l’adresse dans *lpSockAddr* .

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Si cela indique un code d’erreur WSAEWOULDBLOCK et que votre application utilise les rappels substituables, votre application reçoit un message d' `OnConnect` lorsque l’opération de connexion est terminée. Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE l’adresse spécifiée est déjà utilisée.

- WSAEINPROGRESS un appel de blocage de Windows Sockets est en cours.

- WSAEADDRNOTAVAIL l’adresse spécifiée n’est pas disponible à partir de l’ordinateur local.

- Les adresses WSAEAFNOSUPPORT de la famille spécifiée ne peuvent pas être utilisées avec ce Socket.

- WSAECONNREFUSED la tentative de connexion a été rejetée.

- WSAEDESTADDRREQ une adresse de destination est requise.

- WSAEFAULT l’argument *nSockAddrLen* est incorrect.

- WSAEINVAL adresse d’hôte non valide.

- WSAEISCONN le socket est déjà connecté.

- WSAEMFILE aucun autre descripteur de fichier n’est disponible.

- WSAENETUNREACH le réseau ne peut pas être atteint à partir de cet hôte pour l’instant.

- WSAENOBUFS aucun espace de mémoire tampon n’est disponible. Impossible de connecter le Socket.

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAETIMEDOUT tentative de connexion a expiré sans établir de connexion.

- WSAEWOULDBLOCK le socket est marqué comme étant non bloquant et la connexion ne peut pas être effectuée immédiatement.

### <a name="remarks"></a>Notes

Si le socket est indépendant, les valeurs uniques sont affectées à l’association locale par le système et le socket est marqué comme étant lié. Notez que si le champ d’adresse de la structure de nom ne comporte que des zéros, `Connect` retourne la valeur zéro. Pour afficher les informations d’erreur étendues, appelez la fonction membre `GetLastError`.

Pour les sockets de flux (de type SOCK_STREAM), une connexion active est lancée sur l’hôte étranger. Lorsque l’appel de socket se termine correctement, le socket est prêt à envoyer/recevoir des données.

Pour un socket datagramme (type SOCK_DGRAM), une destination par défaut est définie, qui sera utilisée lors des appels de `Send` et de `Receive` suivants.

##  <a name="create"></a>CAsyncSocket :: Create

Appelez la fonction membre `Create` après avoir construit un objet Socket pour créer le socket Windows et l’attacher.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Paramètres

*nSocketPort*<br/>
Un port bien connu à utiliser avec le socket, ou 0 si vous souhaitez que Windows Sockets sélectionne un port.

*nSocketType*<br/>
SOCK_STREAM ou SOCK_DGRAM.

*lEvent*<br/>
Masque de masque qui spécifie une combinaison d’événements réseau qui intéressent l’application.

- FD_READ souhaitez recevoir une notification de préparation pour la lecture.

- FD_WRITE souhaitez recevoir des notifications de préparation à l’écriture.

- FD_OOB souhaitez recevoir la notification de l’arrivée des données hors bande.

- FD_ACCEPT souhaitez recevoir la notification des connexions entrantes.

- FD_CONNECT souhaitez recevoir la notification de la connexion terminée.

- FD_CLOSE souhaitez recevoir la notification de la fermeture du Socket.

*lpszSockAddress*<br/>
Pointeur vers une chaîne contenant l’adresse réseau du socket connecté, un nombre en pointillés tel que « 128.56.22.8 ». Le passage de la chaîne NULL pour ce paramètre indique que l’instance de `CAsyncSocket` doit écouter l’activité des clients sur toutes les interfaces réseau.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEAFNOSUPPORT la famille d’adresses spécifiée n’est pas prise en charge.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAEMFILE aucun autre descripteur de fichier n’est disponible.

- WSAENOBUFS aucun espace de mémoire tampon n’est disponible. Impossible de créer le Socket.

- WSAEPROTONOSUPPORT le port spécifié n’est pas pris en charge.

- WSAEPROTOTYPE le type de port spécifié est incorrect pour ce Socket.

- WSAESOCKTNOSUPPORT le type de socket spécifié n’est pas pris en charge dans cette famille d’adresses.

### <a name="remarks"></a>Notes

`Create` appelle [Socket](#socket) et, en cas de réussite, il appelle [Bind](#bind) pour lier le socket à l’adresse spécifiée. Les types de sockets suivants sont pris en charge :

- SOCK_STREAM fournit des flux d’octets séquencés, fiables, en duplex intégral et basés sur les connexions. Utilise le protocole TCP (Transmission Control Protocol) pour la famille d’adresses Internet.

- SOCK_DGRAM prend en charge les datagrammes, qui sont des paquets non fiables, sans connexion, d’une longueur maximale fixe (généralement petite). Utilise le protocole UDP (User Datagram Protocol) pour la famille d’adresses Internet.

    > [!NOTE]
    >  La fonction membre `Accept` accepte une référence à un nouvel objet `CSocket` vide comme paramètre. Vous devez construire cet objet avant d’appeler `Accept`. Gardez à l’esprit que si cet objet Socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet Socket.

> [!IMPORTANT]
> `Create` n’est **pas** thread-safe.  Si vous l’appelez dans un environnement multithread où il peut être appelé simultanément par différents threads, veillez à protéger chaque appel avec un mutex ou un autre verrou de synchronisation.

Pour plus d’informations sur les sockets de flux et de datagrammes, consultez les articles [Windows Sockets : arrière-plan](../../mfc/windows-sockets-background.md) et [Windows Sockets : ports et adresses de sockets](../../mfc/windows-sockets-ports-and-socket-addresses.md) et [API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

##  <a name="detach"></a>CAsyncSocket ::D Etach

Appelez cette fonction membre pour détacher le handle de SOCKET dans le *m_hSocket* membre de données de l’objet `CAsyncSocket` et définissez *m_hSocket* sur la valeur null.

```
SOCKET Detach();
```

##  <a name="fromhandle"></a>CAsyncSocket :: FromHandle

Retourne un pointeur vers un objet `CAsyncSocket`.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle vers un Socket.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CAsyncSocket`, ou NULL s’il n’existe aucun objet `CAsyncSocket` attaché à *hSocket*.

### <a name="remarks"></a>Notes

Lorsqu’un handle de SOCKET est attribué à un objet `CAsyncSocket` n’est pas attaché au descripteur, la fonction membre retourne la valeur NULL.

##  <a name="getlasterror"></a>CAsyncSocket :: GetLastError

Appelez cette fonction membre pour obtenir l’état d’erreur de la dernière opération qui a échoué.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Valeur de retour

La valeur de retour indique le code d’erreur de la dernière routine de l’API Windows Sockets effectuée par ce thread.

### <a name="remarks"></a>Notes

Quand une fonction membre particulière indique qu’une erreur s’est produite, `GetLastError` doit être appelée pour récupérer le code d’erreur approprié. Consultez les descriptions des fonctions membres individuelles pour obtenir la liste des codes d’erreur applicables.

Pour plus d’informations sur les codes d’erreur, consultez [API Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2).

##  <a name="getpeername"></a>CAsyncSocket :: GetPeerName

Appelez cette fonction membre pour recevoir l’adresse du socket homologue auquel ce Socket est connecté.

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
Référence à un objet `CString` qui reçoit une adresse IP de nombre en pointillés.

*rPeerPort*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Pointeur vers la structure [sockaddr](/windows/win32/winsock/sockaddr-2) qui reçoit le nom du socket homologue.

*lpSockAddrLen*<br/>
Pointeur vers la longueur de l’adresse dans *lpSockAddr* en octets. Au retour, l’argument *lpSockAddrLen* contient la taille réelle de *lpSockAddr* retournée en octets.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT l’argument *lpSockAddrLen* n’est pas assez grand.

- WSAEINPROGRESS un appel de blocage de Windows Sockets est en cours.

- WSAENOTCONN le socket n’est pas connecté.

- WSAENOTSOCK le descripteur n’est pas un Socket.

### <a name="remarks"></a>Notes

Pour gérer les adresses IPv6, utilisez [CAsyncSocket :: GetPeerNameEx](#getpeernameex).

##  <a name="getpeernameex"></a>CAsyncSocket :: GetPeerNameEx

Appelez cette fonction membre pour récupérer l’adresse du socket homologue auquel ce Socket est connecté (gère les adresses IPv6).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Paramètres

*rPeerAddress*<br/>
Référence à un objet `CString` qui reçoit une adresse IP de nombre en pointillés.

*rPeerPort*<br/>
Référence à un UINT qui stocke un port.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT l’argument *lpSockAddrLen* n’est pas assez grand.

- WSAEINPROGRESS un appel de blocage de Windows Sockets est en cours.

- WSAENOTCONN le socket n’est pas connecté.

- WSAENOTSOCK le descripteur n’est pas un Socket.

### <a name="remarks"></a>Notes

Cette fonction est identique à [CAsyncSocket :: getpeername](#getpeername) , à ceci près qu’elle gère les adresses IPv6 ainsi que les protocoles plus anciens.

##  <a name="getsockname"></a>CAsyncSocket :: GetSockName

Appelez cette fonction membre pour obtenir le nom local d’un Socket.

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
Référence à un objet `CString` qui reçoit une adresse IP de nombre en pointillés.

*rSocketPort*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Pointeur vers une structure [sockaddr](/windows/win32/winsock/sockaddr-2) qui reçoit l’adresse du Socket.

*lpSockAddrLen*<br/>
Pointeur vers la longueur de l’adresse dans *lpSockAddr* en octets.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT l’argument *lpSockAddrLen* n’est pas assez grand.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEINVAL le socket n’a pas été lié à une adresse avec `Bind`.

### <a name="remarks"></a>Notes

Cet appel est particulièrement utile quand un appel de `Connect` a été effectué sans commencer par `Bind` d’abord. Cet appel offre le seul moyen par lequel vous pouvez déterminer l’association locale qui a été définie par le système.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket :: GetSockNameEx](#getsocknameex)

##  <a name="getsocknameex"></a>CAsyncSocket :: GetSockNameEx

Appelez cette fonction membre pour obtenir le nom local d’un socket (gère les adresses IPv6).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Paramètres

*rSocketAddress*<br/>
Référence à un objet `CString` qui reçoit une adresse IP de nombre en pointillés.

*rSocketPort*<br/>
Référence à un UINT qui stocke un port.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT l’argument *lpSockAddrLen* n’est pas assez grand.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEINVAL le socket n’a pas été lié à une adresse avec `Bind`.

### <a name="remarks"></a>Notes

Cet appel est identique à [CAsyncSocket :: GetSockName](#getsockname) , à ceci près qu’il gère les adresses IPv6 ainsi que les protocoles plus anciens.

Cet appel est particulièrement utile quand un appel de `Connect` a été effectué sans commencer par `Bind` d’abord. Cet appel offre le seul moyen par lequel vous pouvez déterminer l’association locale qui a été définie par le système.

##  <a name="getsockopt"></a>CAsyncSocket :: GetSockOpt

Appelez cette fonction membre pour récupérer une option de Socket.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Paramètres

*nOptionName*<br/>
Option de socket pour laquelle la valeur doit être récupérée.

*lpOptionValue*<br/>
Pointeur vers la mémoire tampon dans laquelle la valeur de l’option demandée doit être retournée. La valeur associée à l’option sélectionnée est retournée dans la mémoire tampon *lpOptionValue*. L’entier pointé par *lpOptionLen* doit contenir à l’origine la taille de cette mémoire tampon en octets. et au retour, elle sera définie sur la taille de la valeur retournée. Pour SO_LINGER, il s’agit de la taille d’une structure `LINGER` ; pour toutes les autres options, il s’agit de la taille d’un BOOL ou d’un **entier**, en fonction de l’option. Consultez la liste des options et leur taille dans la section Notes.

*lpOptionLen*<br/>
Pointeur vers la taille de la mémoire tampon *lpOptionValue* en octets.

*nLevel*<br/>
Niveau auquel l’option est définie ; les seuls niveaux pris en charge sont SOL_SOCKET et IPPROTO_TCP.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Si une option n’a jamais été définie avec `SetSockOpt`, `GetSockOpt` retourne la valeur par défaut de l’option. Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT l’argument *lpOptionLen* n’était pas valide.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAENOPROTOOPT l’option est inconnue ou n’est pas prise en charge. En particulier, SO_BROADCAST n’est pas pris en charge sur les sockets de type SOCK_STREAM, tandis que SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER et SO_OOBINLINE ne sont pas pris en charge sur les sockets de type SOCK_DGRAM.

- WSAENOTSOCK le descripteur n’est pas un Socket.

### <a name="remarks"></a>Notes

`GetSockOpt` récupère la valeur actuelle d’une option de socket associée à un socket de tout type, dans n’importe quel État, et stocke le résultat dans *lpOptionValue*. Les options affectent les opérations de socket, telles que le routage de paquets, le transfert de données hors bande, etc.

Les options suivantes sont prises en charge pour les `GetSockOpt`. Le type identifie le type de données adressé par *lpOptionValue*. L’option TCP_NODELAY utilise le niveau IPPROTO_TCP ; toutes les autres options utilisent le niveau SOL_SOCKET.

|Valeur|Type|Signification|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Le socket est à l’écoute.|
|SO_BROADCAST|BOOL|Le socket est configuré pour la transmission des messages de diffusion.|
|SO_DEBUG|BOOL|Le débogage est activé.|
|SO_DONTLINGER|BOOL|Si la valeur est true, l’option SO_LINGER est désactivée.|
|SO_DONTROUTE|BOOL|Le routage est désactivé.|
|SO_ERROR|**int**|Récupérez l’état d’erreur et désactivez.|
|SO_KEEPALIVE|BOOL|Les connexions persistantes sont envoyées.|
|SO_LINGER|`struct LINGER`|Retourne les options de Lingo actuelles.|
|SO_OOBINLINE|BOOL|Les données hors bande sont reçues dans le flux de données normal.|
|SO_RCVBUF|int|Taille de la mémoire tampon pour les réceptions.|
|SO_REUSEADDR|BOOL|Le socket peut être lié à une adresse qui est déjà en cours d’utilisation.|
|SO_SNDBUF|**int**|Taille de la mémoire tampon pour les envois.|
|SO_TYPE|**int**|Type du socket (par exemple, SOCK_STREAM).|
|TCP_NODELAY|BOOL|Désactive l'algorithme Nagle pour la fusion des envois.|

Les options BSD (Berkeley Software Distribution) ne sont pas prises en charge pour les `GetSockOpt` sont les suivantes :

|Valeur|Type|Signification|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Recevoir un seuil inférieur.|
|SO_RCVTIMEO|**int**|Délai d’attente de réception.|
|SO_SNDLOWAT|**int**|Envoyer une borne basse.|
|SO_SNDTIMEO|**int**|Délai d’attente d’envoi.|
|IP_OPTIONS||Obtient les options dans l’en-tête IP.|
|TCP_MAXSEG|**int**|Obtient la taille maximale du segment TCP.|

L’appel de `GetSockOpt` avec une option non prise en charge entraîne le renvoi d’un code d’erreur WSAENOPROTOOPT à partir de `GetLastError`.

##  <a name="ioctl"></a>CAsyncSocket :: IOCtl

Appelez cette fonction membre pour contrôler le mode d’un Socket.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Paramètres

*lCommand*<br/>
Commande à exécuter sur le Socket.

*lpArgument*<br/>
Pointeur vers un paramètre pour *lCommand*.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL *lCommand* n’est pas une commande valide, ou *lpArgument* n’est pas un paramètre acceptable pour *lCommand*, ou la commande n’est pas applicable au type de Socket fourni.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAENOTSOCK le descripteur n’est pas un Socket.

### <a name="remarks"></a>Notes

Cette routine peut être utilisée sur n’importe quel Socket dans n’importe quel état. Il est utilisé pour obtenir ou récupérer les paramètres de fonctionnement associés au socket, indépendamment du protocole et du sous-système de communication. Les commandes suivantes sont prises en charge :

- FIONBIO active ou désactive le mode non bloquant sur le Socket. Le paramètre *lpArgument* pointe vers un `DWORD`, qui est différent de zéro si le mode non bloquant est activé et zéro s’il doit être désactivé. Si `AsyncSelect` a été émis sur un socket, toute tentative d’utilisation d' `IOCtl` pour redéfinir le socket en mode blocage échoue avec WSAEINVAL. Pour rétablir le socket en mode blocage et empêcher l’erreur WSAEINVAL, une application doit d’abord désactiver `AsyncSelect` en appelant `AsyncSelect` avec le paramètre *lEvent* égal à 0, puis appeler `IOCtl`.

- FIONREAD Déterminez le nombre maximal d’octets pouvant être lus à l’aide d’un appel de `Receive` à partir de ce Socket. Le paramètre *lpArgument* pointe vers un `DWORD` dans lequel `IOCtl` stocke le résultat. Si ce Socket est de type SOCK_STREAM, FIONREAD retourne la quantité totale de données qui peuvent être lues dans une seule `Receive`; C’est normalement le même que la quantité totale de données en file d’attente sur le Socket. Si ce Socket est de type SOCK_DGRAM, FIONREAD retourne la taille du premier datagramme mis en file d’attente sur le Socket.

- SIOCATMARK déterminer si toutes les données hors bande ont été lues. Cela s’applique uniquement à un socket de type SOCK_STREAM qui a été configuré pour la réception en ligne de toutes les données hors bande (SO_OOBINLINE). Si aucune donnée hors bande n’est en attente de lecture, l’opération retourne une valeur différente de zéro. Dans le cas contraire, elle retourne 0, et le `Receive` suivant ou `ReceiveFrom` exécuté sur le socket récupère une partie ou la totalité des données précédant la marque. l’application doit utiliser l’opération SIOCATMARK pour déterminer si des données sont conservées. Si des données normales précèdent les données « urgentes » (hors bande), elles seront reçues dans l’ordre. (Notez qu’un `Receive` ou `ReceiveFrom` ne mélangera jamais les données hors bande et normales dans le même appel.) Le paramètre *lpArgument* pointe vers un `DWORD` dans lequel `IOCtl` stocke le résultat.

Cette fonction est un sous-ensemble de `ioctl()` tel qu’il est utilisé dans les sockets Berkeley. En particulier, il n’y a aucune commande qui est équivalente à FIOASYNC, tandis que SIOCATMARK est la seule commande au niveau du socket qui est prise en charge.

##  <a name="listen"></a>CAsyncSocket :: Listen

Appelez cette fonction membre pour écouter les demandes de connexion entrante.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Paramètres

*nConnectionBacklog*<br/>
Longueur maximale que peut atteindre la file d’attente des connexions en attente. La plage valide est comprise entre 1 et 5.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEADDRINUSE tentative d’écoute sur une adresse en cours d’utilisation.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAEINVAL le socket n’a pas été lié à `Bind` ou est déjà connecté.

- WSAEISCONN le socket est déjà connecté.

- WSAEMFILE aucun autre descripteur de fichier n’est disponible.

- WSAENOBUFS aucun espace de mémoire tampon n’est disponible.

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEOPNOTSUPP le socket référencé n’est pas d’un type qui prend en charge l’opération `Listen`.

### <a name="remarks"></a>Notes

Pour accepter les connexions, le socket est d’abord créé avec `Create`, un backlog pour les connexions entrantes est spécifié avec `Listen`, puis les connexions sont acceptées avec `Accept`. `Listen` s’applique uniquement aux sockets qui prennent en charge les connexions, c’est-à-dire à ceux de type SOCK_STREAM. Ce Socket est placé en mode « passif » où les connexions entrantes sont acceptées et mises en file d’attente d’acceptation par le processus.

Cette fonction est généralement utilisée par les serveurs (ou toute application qui souhaite accepter des connexions) qui peuvent avoir plusieurs demandes de connexion à la fois : si une demande de connexion arrive avec la file d’attente pleine, le client reçoit une erreur avec l’indication WSAECONNREFUSED.

`Listen` tente de continuer à fonctionner de façon rationnelle lorsqu’il n’y a pas de ports disponibles (descripteurs). Il acceptera les connexions jusqu’à ce que la file d’attente soit vidée. Si les ports deviennent disponibles, un appel ultérieur à `Listen` ou `Accept` rechargera la file d’attente dans le « backlog » actuel ou le plus récent, si possible, et reprendrea l’écoute des connexions entrantes.

##  <a name="m_hsocket"></a>CAsyncSocket :: m_hSocket

Contient le handle de SOCKET pour le socket encapsulé par cet objet `CAsyncSocket`.

```
SOCKET m_hSocket;
```

##  <a name="onaccept"></a>CAsyncSocket :: OnAccept

Appelé par l’infrastructure pour informer un socket d’écoute qu’il peut accepter les demandes de connexion en attente en appelant la fonction membre [Accept](#accept) .

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
Erreur la plus récente sur un Socket. Les codes d’erreur suivants s’appliquent à la fonction membre `OnAccept` :

- **0** la fonction a été exécutée avec succès.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : notifications de sockets](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onclose"></a>CAsyncSocket :: OnClose

Appelé par l’infrastructure pour notifier à ce socket que le socket connecté est fermé par son processus.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
Erreur la plus récente sur un Socket. Les codes d’erreur suivants s’appliquent à la fonction membre `OnClose` :

- **0** la fonction a été exécutée avec succès.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAECONNRESET la connexion a été réinitialisée par le côté distant.

- WSAECONNABORTED la connexion a été abandonnée en raison d’un dépassement de délai d’attente ou d’un autre échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : notifications de sockets](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onconnect"></a>CAsyncSocket :: OnConnect

Appelé par l’infrastructure pour notifier ce socket de connexion que sa tentative de connexion est terminée, qu’il soit avec succès ou erroné.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
Erreur la plus récente sur un Socket. Les codes d’erreur suivants s’appliquent à la fonction membre `OnConnect` :

- **0** la fonction a été exécutée avec succès.

- WSAEADDRINUSE l’adresse spécifiée est déjà utilisée.

- WSAEADDRNOTAVAIL l’adresse spécifiée n’est pas disponible à partir de l’ordinateur local.

- Les adresses WSAEAFNOSUPPORT de la famille spécifiée ne peuvent pas être utilisées avec ce Socket.

- WSAECONNREFUSED la tentative de connexion a été rejetée de force.

- WSAEDESTADDRREQ une adresse de destination est requise.

- WSAEFAULT l’argument *lpSockAddrLen* est incorrect.

- WSAEINVAL le socket est déjà lié à une adresse.

- WSAEISCONN le socket est déjà connecté.

- WSAEMFILE aucun autre descripteur de fichier n’est disponible.

- WSAENETUNREACH le réseau ne peut pas être atteint à partir de cet hôte pour l’instant.

- WSAENOBUFS aucun espace de mémoire tampon n’est disponible. Impossible de connecter le Socket.

- WSAENOTCONN le socket n’est pas connecté.

- WSAENOTSOCK le descripteur est un fichier et non un Socket.

- WSAETIMEDOUT la tentative de connexion a expiré sans établir de connexion.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Dans [CSocket](../../mfc/reference/csocket-class.md), la fonction de notification `OnConnect` n’est jamais appelée. Pour les connexions, il vous suffit d’appeler `Connect`, qui retournera lorsque la connexion sera terminée (avec succès ou par erreur). La façon dont les notifications de connexion sont gérées est un détail d’implémentation MFC.

Pour plus d’informations, consultez [Windows Sockets : notifications de sockets](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

##  <a name="onoutofbanddata"></a>CAsyncSocket :: OnOutOfBandData

Appelée par l’infrastructure pour notifier au socket de réception que le socket d’envoi a des données hors bande à envoyer.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
Erreur la plus récente sur un Socket. Les codes d’erreur suivants s’appliquent à la fonction membre `OnOutOfBandData` :

- **0** la fonction a été exécutée avec succès.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Les données hors bande sont un canal logiquement indépendant qui est associé à chaque paire de sockets connectés de type SOCK_STREAM. Le canal est généralement utilisé pour envoyer des données urgentes.

MFC prend en charge les données hors bande, mais les utilisateurs de la classe `CAsyncSocket` sont déconseillés de l’utiliser. Le moyen le plus simple consiste à créer un deuxième Socket pour transmettre ces données. Pour plus d’informations sur les données hors bande, consultez [Windows Sockets : notifications de sockets](../../mfc/windows-sockets-socket-notifications.md).

##  <a name="onreceive"></a>CAsyncSocket :: OnReceive

Appelé par l’infrastructure pour notifier à ce socket que des données dans la mémoire tampon peuvent être récupérées en appelant la fonction membre `Receive`.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
Erreur la plus récente sur un Socket. Les codes d’erreur suivants s’appliquent à la fonction membre `OnReceive` :

- **0** la fonction a été exécutée avec succès.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : notifications de sockets](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

##  <a name="onsend"></a>CAsyncSocket :: OnSend

Appelée par l’infrastructure pour informer le socket qu’il peut désormais envoyer des données en appelant la fonction membre `Send`.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Paramètres

*nErrorCode*<br/>
Erreur la plus récente sur un Socket. Les codes d’erreur suivants s’appliquent à la fonction membre `OnSend` :

- **0** la fonction a été exécutée avec succès.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : notifications de sockets](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

##  <a name="operator_eq"></a>CAsyncSocket :: Operator =

Assigne une nouvelle valeur à un objet `CAsyncSocket`.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Paramètres

*rSrc*<br/>
Référence à un objet `CAsyncSocket` existant.

### <a name="remarks"></a>Notes

Appelez cette fonction pour copier un objet `CAsyncSocket` existant vers un autre objet `CAsyncSocket`.

##  <a name="operator_socket"></a>CAsyncSocket :: Operator, SOCKET

Utilisez cet opérateur pour récupérer le handle de SOCKET de l’objet `CAsyncSocket`.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, handle de l’objet SOCKET ; Sinon, NULL.

### <a name="remarks"></a>Notes

Vous pouvez utiliser le handle pour appeler des API Windows directement.

##  <a name="receive"></a>CAsyncSocket :: Receive

Appelez cette fonction membre pour recevoir des données à partir d’un Socket.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Mémoire tampon pour les données entrantes.

*nBufLen*<br/>
Longueur de *lpBuf* en octets.

*nFlags*<br/>
Spécifie la façon dont l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le paramètre *nFlags* . Ce dernier est construit en combinant l’une des valeurs suivantes à l' C++ aide de l’opérateur **or** :

- MSG_PEEK lire les données entrantes. Les données sont copiées dans la mémoire tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB traiter les données hors bande.

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `Receive` retourne le nombre d’octets reçus. Si la connexion a été fermée, elle retourne 0. Sinon, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAENOTCONN le socket n’est pas connecté.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `Receive` sur un socket après l’appel de `ShutDown` avec *nHow* défini sur 0 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme étant non bloquant et l’opération `Receive` se bloquerait.

- WSAEMSGSIZE le datagramme était trop grand pour tenir dans la mémoire tampon spécifiée et a été tronqué.

- WSAEINVAL le socket n’a pas été lié à `Bind`.

- WSAECONNABORTED le circuit virtuel a été abandonné en raison d’un dépassement de délai d’attente ou d’un autre échec.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour les sockets de flux ou de datagrammes connectés et est utilisée pour lire les données entrantes.

Pour les sockets de type SOCK_STREAM, toutes les informations actuellement disponibles jusqu’à la taille de la mémoire tampon fournie sont retournées. Si le socket a été configuré pour la réception en ligne de données hors bande (option de socket SO_OOBINLINE) et si les données hors bande ne sont pas lues, seules les données hors bande sont retournées. L’application peut utiliser l’option `IOCtlSIOCATMARK` ou [OnOutOfBandData](#onoutofbanddata) pour déterminer si des données hors bande restent à lire.

Pour les sockets de datagrammes, les données sont extraites du premier datagramme mis en file d’attente, jusqu’à la taille de la mémoire tampon fournie. Si le datagramme est plus grand que la mémoire tampon fournie, la mémoire tampon est remplie avec la première partie du datagramme, les données excédentaires sont perdues et `Receive` retourne une valeur de SOCKET_ERROR avec le code d’erreur défini sur WSAEMSGSIZE. Si aucune donnée entrante n’est disponible au niveau du socket, la valeur SOCKET_ERROR est retournée avec le code d’erreur défini sur WSAEWOULDBLOCK. La fonction de rappel [OnReceive](#onreceive) peut être utilisée pour déterminer quand des données supplémentaires arrivent.

Si le socket est de type SOCK_STREAM et que le côté distant a arrêté la connexion normalement, un `Receive` se termine immédiatement avec 0 octets reçus. Si la connexion a été réinitialisée, un `Receive` échouera avec l’erreur WSAECONNRESET.

`Receive` doit être appelée une seule fois pour chaque fois que [CAsyncSocket :: OnReceive](#onreceive) est appelé.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CAsyncSocket :: OnReceive](#onreceive).

##  <a name="receivefrom"></a>CAsyncSocket :: ReceiveFrom

Appelez cette fonction membre pour recevoir un datagramme et stocker l’adresse source dans la structure [sockaddr](/windows/win32/winsock/sockaddr-2) ou dans *rSocketAddress*.

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
Mémoire tampon pour les données entrantes.

*nBufLen*<br/>
Longueur de *lpBuf* en octets.

*rSocketAddress*<br/>
Référence à un objet `CString` qui reçoit une adresse IP de nombre en pointillés.

*rSocketPort*<br/>
Référence à un UINT qui stocke un port.

*lpSockAddr*<br/>
Pointeur vers une structure [sockaddr](/windows/win32/winsock/sockaddr-2) qui contient l’adresse source lors du retour.

*lpSockAddrLen*<br/>
Pointeur vers la longueur de l’adresse source dans *lpSockAddr* en octets.

*nFlags*<br/>
Spécifie la façon dont l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le paramètre *nFlags* . Ce dernier est construit en combinant l’une des valeurs suivantes à l' C++ aide de l’opérateur **or** :

- MSG_PEEK lire les données entrantes. Les données sont copiées dans la mémoire tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB traiter les données hors bande.

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `ReceiveFrom` retourne le nombre d’octets reçus. Si la connexion a été fermée, elle retourne 0. Sinon, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant `GetLastError`. Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT l’argument *lpSockAddrLen* n’était pas valide : la mémoire tampon *lpSockAddr* était trop petite pour accueillir l’adresse homologue.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAEINVAL le socket n’a pas été lié à `Bind`.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `ReceiveFrom` sur un socket après l’appel de `ShutDown` avec *nHow* défini sur 0 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme étant non bloquant et l’opération `ReceiveFrom` se bloquerait.

- WSAEMSGSIZE le datagramme était trop grand pour tenir dans la mémoire tampon spécifiée et a été tronqué.

- WSAECONNABORTED le circuit virtuel a été abandonné en raison d’un dépassement de délai d’attente ou d’un autre échec.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour lire les données entrantes sur un socket (éventuellement connecté) et capturer l’adresse à partir de laquelle les données ont été envoyées.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket :: ReceiveFromEx](#receivefromex).

Pour les sockets de type SOCK_STREAM, toutes les informations actuellement disponibles jusqu’à la taille de la mémoire tampon fournie sont retournées. Si le socket a été configuré pour la réception en ligne de données hors bande (option de socket SO_OOBINLINE) et si les données hors bande ne sont pas lues, seules les données hors bande sont retournées. L’application peut utiliser l’option `IOCtlSIOCATMARK` ou `OnOutOfBandData` pour déterminer si des données hors bande restent à lire. Les paramètres *lpSockAddr* et *lpSockAddrLen* sont ignorés pour les sockets SOCK_STREAM.

Pour les sockets de datagrammes, les données sont extraites du premier datagramme mis en file d’attente, jusqu’à la taille de la mémoire tampon fournie. Si le datagramme est plus grand que la mémoire tampon fournie, la mémoire tampon est remplie avec la première partie du message, les données excédentaires sont perdues et `ReceiveFrom` retourne une valeur de SOCKET_ERROR avec le code d’erreur défini sur WSAEMSGSIZE.

Si *lpSockAddr* est différent de zéro et que le socket est de type SOCK_DGRAM, l’adresse réseau du socket qui a envoyé les données est copiée dans la structure [sockaddr](/windows/win32/winsock/sockaddr-2) correspondante. La valeur pointée par *lpSockAddrLen* est initialisée à la taille de cette structure et est modifiée au retour pour indiquer la taille réelle de l’adresse qui y est stockée. Si aucune donnée entrante n’est disponible au niveau du socket, le `ReceiveFrom` appel attend que les données arrivent, sauf si le socket n’est pas bloqué. Dans ce cas, la valeur SOCKET_ERROR est retournée avec le code d’erreur défini sur WSAEWOULDBLOCK. Le rappel `OnReceive` peut être utilisé pour déterminer quand des données supplémentaires arrivent.

Si le socket est de type SOCK_STREAM et que le côté distant a arrêté la connexion normalement, un `ReceiveFrom` se termine immédiatement avec 0 octets reçus.

##  <a name="receivefromex"></a>CAsyncSocket :: ReceiveFromEx

Appelez cette fonction membre pour recevoir un datagramme et stocker l’adresse source dans la structure [sockaddr](/windows/win32/winsock/sockaddr-2) ou dans *rSocketAddress* (gère les adresses IPv6).

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
Mémoire tampon pour les données entrantes.

*nBufLen*<br/>
Longueur de *lpBuf* en octets.

*rSocketAddress*<br/>
Référence à un objet `CString` qui reçoit une adresse IP de nombre en pointillés.

*rSocketPort*<br/>
Référence à un UINT qui stocke un port.

*nFlags*<br/>
Spécifie la façon dont l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le paramètre *nFlags* . Ce dernier est construit en combinant l’une des valeurs suivantes à l' C++ aide de l’opérateur **or** :

- MSG_PEEK lire les données entrantes. Les données sont copiées dans la mémoire tampon, mais ne sont pas supprimées de la file d’attente d’entrée.

- MSG_OOB traiter les données hors bande.

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `ReceiveFromEx` retourne le nombre d’octets reçus. Si la connexion a été fermée, elle retourne 0. Sinon, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant `GetLastError`. Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT l’argument *lpSockAddrLen* n’était pas valide : la mémoire tampon *lpSockAddr* était trop petite pour accueillir l’adresse homologue.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAEINVAL le socket n’a pas été lié à `Bind`.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `ReceiveFromEx` sur un socket après l’appel de `ShutDown` avec *nHow* défini sur 0 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme étant non bloquant et l’opération `ReceiveFromEx` se bloquerait.

- WSAEMSGSIZE le datagramme était trop grand pour tenir dans la mémoire tampon spécifiée et a été tronqué.

- WSAECONNABORTED le circuit virtuel a été abandonné en raison d’un dépassement de délai d’attente ou d’un autre échec.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

Cette fonction est utilisée pour lire les données entrantes sur un socket (éventuellement connecté) et capturer l’adresse à partir de laquelle les données ont été envoyées.

Cette fonction est identique à [CAsyncSocket :: ReceiveFrom](#receivefrom) , à ceci près qu’elle gère les adresses IPv6 ainsi que les protocoles plus anciens.

Pour les sockets de type SOCK_STREAM, toutes les informations actuellement disponibles jusqu’à la taille de la mémoire tampon fournie sont retournées. Si le socket a été configuré pour la réception en ligne de données hors bande (option de socket SO_OOBINLINE) et si les données hors bande ne sont pas lues, seules les données hors bande sont retournées. L’application peut utiliser l’option `IOCtlSIOCATMARK` ou `OnOutOfBandData` pour déterminer si des données hors bande restent à lire. Les paramètres *lpSockAddr* et *lpSockAddrLen* sont ignorés pour les sockets SOCK_STREAM.

Pour les sockets de datagrammes, les données sont extraites du premier datagramme mis en file d’attente, jusqu’à la taille de la mémoire tampon fournie. Si le datagramme est plus grand que la mémoire tampon fournie, la mémoire tampon est remplie avec la première partie du message, les données excédentaires sont perdues et `ReceiveFromEx` retourne une valeur de SOCKET_ERROR avec le code d’erreur défini sur WSAEMSGSIZE.

Si *lpSockAddr* est différent de zéro et que le socket est de type SOCK_DGRAM, l’adresse réseau du socket qui a envoyé les données est copiée dans la structure [sockaddr](/windows/win32/winsock/sockaddr-2) correspondante. La valeur pointée par *lpSockAddrLen* est initialisée à la taille de cette structure et est modifiée au retour pour indiquer la taille réelle de l’adresse qui y est stockée. Si aucune donnée entrante n’est disponible au niveau du socket, le `ReceiveFromEx` appel attend que les données arrivent, sauf si le socket n’est pas bloqué. Dans ce cas, la valeur SOCKET_ERROR est retournée avec le code d’erreur défini sur WSAEWOULDBLOCK. Le rappel `OnReceive` peut être utilisé pour déterminer quand des données supplémentaires arrivent.

Si le socket est de type SOCK_STREAM et que le côté distant a arrêté la connexion normalement, un `ReceiveFromEx` se termine immédiatement avec 0 octets reçus.

##  <a name="send"></a>CAsyncSocket :: Send

Appelez cette fonction membre pour envoyer des données sur un socket connecté.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Mémoire tampon qui contient les données à transmettre.

*nBufLen*<br/>
Longueur des données en *lpBuf* en octets.

*nFlags*<br/>
Spécifie la façon dont l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le paramètre *nFlags* . Ce dernier est construit en combinant l’une des valeurs suivantes à l' C++ aide de l’opérateur **or** :

- MSG_DONTROUTE spécifie que les données ne doivent pas être soumises au routage. Un fournisseur Windows Sockets peut choisir d’ignorer cet indicateur.

- MSG_OOB envoyer des données hors bande (SOCK_STREAM uniquement).

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `Send` retourne le nombre total de caractères envoyés. (Notez que ce nombre peut être inférieur au nombre indiqué par *nBufLen*.) Sinon, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES l’adresse demandée est une adresse de diffusion, mais l’indicateur approprié n’a pas été défini.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAEFAULT l’argument *lpBuf* n’est pas dans une partie valide de l’espace d’adressage de l’utilisateur.

- WSAENETRESET la connexion doit être réinitialisée, car l’implémentation de Windows Sockets l’a supprimée.

- WSAENOBUFS l’implémentation de Windows Sockets signale un blocage de mémoire tampon.

- WSAENOTCONN le socket n’est pas connecté.

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `Send` sur un socket après l’appel de `ShutDown` avec *nHow* défini sur 1 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme étant non bloquant et l’opération demandée est bloquée.

- WSAEMSGSIZE le socket est de type SOCK_DGRAM, et le datagramme est plus grand que le nombre maximal pris en charge par l’implémentation de Windows Sockets.

- WSAEINVAL le socket n’a pas été lié à `Bind`.

- WSAECONNABORTED le circuit virtuel a été abandonné en raison d’un dépassement de délai d’attente ou d’un autre échec.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

### <a name="remarks"></a>Notes

`Send` est utilisé pour écrire des données sortantes sur des sockets de flux ou de datagrammes connectés. Pour les sockets datagrammes, il faut veiller à ne pas dépasser la taille maximale des paquets IP des sous-réseaux sous-jacents, qui est donnée par l’élément `iMaxUdpDg` de la structure [wsadata,](/windows/win32/api/winsock2/ns-winsock2-wsadata) retournée par `AfxSocketInit`. Si les données sont trop longues pour être transmises atomiquement par le biais du protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée via `GetLastError`et aucune donnée n’est transmise.

Notez que, pour un socket datagramme, l’achèvement réussi d’une `Send` n’indique pas que les données ont été correctement remises.

Sur `CAsyncSocket` objets de type SOCK_STREAM, le nombre d’octets écrits peut être compris entre 1 et la longueur demandée, en fonction de la disponibilité de la mémoire tampon sur les hôtes locaux et étrangers.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CAsyncSocket :: OnSend](#onsend).

##  <a name="sendto"></a>CAsyncSocket :: SendTo

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
Mémoire tampon qui contient les données à transmettre.

*nBufLen*<br/>
Longueur des données en *lpBuf* en octets.

*nHostPort*<br/>
Port identifiant l’application de Socket.

*lpszHostAddress*<br/>
Adresse réseau du socket auquel cet objet est connecté : un nom d’ordinateur tel que « ftp.microsoft.com » ou un nombre en pointillés tel que « 128.56.22.8 ».

*nFlags*<br/>
Spécifie la façon dont l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le paramètre *nFlags* . Ce dernier est construit en combinant l’une des valeurs suivantes à l' C++ aide de l’opérateur **or** :

- MSG_DONTROUTE spécifie que les données ne doivent pas être soumises au routage. Un fournisseur Windows Sockets peut choisir d’ignorer cet indicateur.

- MSG_OOB envoyer des données hors bande (SOCK_STREAM uniquement).

*lpSockAddr*<br/>
Pointeur vers une structure [sockaddr](/windows/win32/winsock/sockaddr-2) qui contient l’adresse du socket cible.

*nSockAddrLen*<br/>
Longueur, en octets, de l’adresse dans *lpSockAddr* .

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `SendTo` retourne le nombre total de caractères envoyés. (Notez que ce nombre peut être inférieur au nombre indiqué par *nBufLen*.) Sinon, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES l’adresse demandée est une adresse de diffusion, mais l’indicateur approprié n’a pas été défini.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAEFAULT les paramètres *lpBuf* ou *lpSockAddr* ne font pas partie de l’espace d’adressage de l’utilisateur, ou l’argument *lpSockAddr* est trop petit (inférieur à la taille d’une structure [sockaddr](/windows/win32/winsock/sockaddr-2) ).

- WSAEINVAL le nom d’hôte n’est pas valide.

- WSAENETRESET la connexion doit être réinitialisée, car l’implémentation de Windows Sockets l’a supprimée.

- WSAENOBUFS l’implémentation de Windows Sockets signale un blocage de mémoire tampon.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `SendTo` sur un socket après l’appel de `ShutDown` avec *nHow* défini sur 1 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme étant non bloquant et l’opération demandée est bloquée.

- WSAEMSGSIZE le socket est de type SOCK_DGRAM, et le datagramme est plus grand que le nombre maximal pris en charge par l’implémentation de Windows Sockets.

- WSAECONNABORTED le circuit virtuel a été abandonné en raison d’un dépassement de délai d’attente ou d’un autre échec.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

- WSAEADDRNOTAVAIL l’adresse spécifiée n’est pas disponible à partir de l’ordinateur local.

- Les adresses WSAEAFNOSUPPORT de la famille spécifiée ne peuvent pas être utilisées avec ce Socket.

- WSAEDESTADDRREQ une adresse de destination est requise.

- WSAENETUNREACH le réseau ne peut pas être atteint à partir de cet hôte pour l’instant.

### <a name="remarks"></a>Notes

`SendTo` est utilisé sur les sockets de datagramme ou de flux et est utilisé pour écrire des données sortantes sur un Socket. Pour les sockets de datagramme, il faut veiller à ne pas dépasser la taille maximale des paquets IP des sous-réseaux sous-jacents, qui est donnée par l’élément `iMaxUdpDg` de la structure [wsadata,](/windows/win32/api/winsock2/ns-winsock2-wsadata) remplie par [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si les données sont trop longues pour être transmises atomiquement par le biais du protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée et aucune donnée n’est transmise.

Notez que l’aboutissement d’une `SendTo` n’indique pas que les données ont été correctement remises.

`SendTo` est utilisé uniquement sur un socket SOCK_DGRAM pour envoyer un datagramme à un socket spécifique identifié par le paramètre *lpSockAddr* .

Pour envoyer une diffusion (sur un SOCK_DGRAM uniquement), l’adresse dans le paramètre *lpSockAddr* doit être construite à l’aide de l’adresse IP spéciale INADDR_BROADCAST (définie dans le fichier d’en-tête Windows Sockets Winsock. H) ainsi que le numéro de port souhaité. Ou, si le paramètre *lpszHostAddress* est null, le socket est configuré pour la diffusion. Il est généralement déconseillé pour un datagramme de diffusion de dépasser la taille à laquelle la fragmentation peut se produire, ce qui implique que la partie des données du datagramme (à l’exclusion des en-têtes) ne doit pas dépasser 512 octets.

Pour gérer les adresses IPv6, utilisez [CAsyncSocket :: SendToEx](#sendtoex).

##  <a name="sendtoex"></a>CAsyncSocket :: SendToEx

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
Mémoire tampon qui contient les données à transmettre.

*nBufLen*<br/>
Longueur des données en *lpBuf* en octets.

*nHostPort*<br/>
Port identifiant l’application de Socket.

*lpszHostAddress*<br/>
Adresse réseau du socket auquel cet objet est connecté : un nom d’ordinateur tel que « ftp.microsoft.com » ou un nombre en pointillés tel que « 128.56.22.8 ».

*nFlags*<br/>
Spécifie la façon dont l’appel est effectué. La sémantique de cette fonction est déterminée par les options de socket et le paramètre *nFlags* . Ce dernier est construit en combinant l’une des valeurs suivantes à l' C++ aide de l’opérateur **or** :

- MSG_DONTROUTE spécifie que les données ne doivent pas être soumises au routage. Un fournisseur Windows Sockets peut choisir d’ignorer cet indicateur.

- MSG_OOB envoyer des données hors bande (SOCK_STREAM uniquement).

### <a name="return-value"></a>Valeur de retour

Si aucune erreur ne se produit, `SendToEx` retourne le nombre total de caractères envoyés. (Notez que ce nombre peut être inférieur au nombre indiqué par *nBufLen*.) Sinon, une valeur de SOCKET_ERROR est retournée, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEACCES l’adresse demandée est une adresse de diffusion, mais l’indicateur approprié n’a pas été défini.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAEFAULT les paramètres *lpBuf* ou *lpSockAddr* ne font pas partie de l’espace d’adressage de l’utilisateur, ou l’argument *lpSockAddr* est trop petit (inférieur à la taille d’une structure [sockaddr](/windows/win32/winsock/sockaddr-2) ).

- WSAEINVAL le nom d’hôte n’est pas valide.

- WSAENETRESET la connexion doit être réinitialisée, car l’implémentation de Windows Sockets l’a supprimée.

- WSAENOBUFS l’implémentation de Windows Sockets signale un blocage de mémoire tampon.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un Socket.

- WSAEOPNOTSUPP MSG_OOB a été spécifié, mais le socket n’est pas de type SOCK_STREAM.

- WSAESHUTDOWN le socket a été arrêté ; Il n’est pas possible d’appeler `SendToEx` sur un socket après l’appel de `ShutDown` avec *nHow* défini sur 1 ou 2.

- WSAEWOULDBLOCK le socket est marqué comme étant non bloquant et l’opération demandée est bloquée.

- WSAEMSGSIZE le socket est de type SOCK_DGRAM, et le datagramme est plus grand que le nombre maximal pris en charge par l’implémentation de Windows Sockets.

- WSAECONNABORTED le circuit virtuel a été abandonné en raison d’un dépassement de délai d’attente ou d’un autre échec.

- WSAECONNRESET le circuit virtuel a été réinitialisé par le côté distant.

- WSAEADDRNOTAVAIL l’adresse spécifiée n’est pas disponible à partir de l’ordinateur local.

- Les adresses WSAEAFNOSUPPORT de la famille spécifiée ne peuvent pas être utilisées avec ce Socket.

- WSAEDESTADDRREQ une adresse de destination est requise.

- WSAENETUNREACH le réseau ne peut pas être atteint à partir de cet hôte pour l’instant.

### <a name="remarks"></a>Notes

Cette méthode est identique à [CAsyncSocket :: SendTo](#sendto) , sauf qu’elle gère les adresses IPv6 ainsi que les protocoles plus anciens.

`SendToEx` est utilisé sur les sockets de datagramme ou de flux et est utilisé pour écrire des données sortantes sur un Socket. Pour les sockets de datagramme, il faut veiller à ne pas dépasser la taille maximale des paquets IP des sous-réseaux sous-jacents, qui est donnée par l’élément `iMaxUdpDg` de la structure [wsadata,](/windows/win32/api/winsock2/ns-winsock2-wsadata) remplie par [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit). Si les données sont trop longues pour être transmises atomiquement par le biais du protocole sous-jacent, l’erreur WSAEMSGSIZE est retournée et aucune donnée n’est transmise.

Notez que l’aboutissement d’une `SendToEx` n’indique pas que les données ont été correctement remises.

`SendToEx` est utilisé uniquement sur un socket SOCK_DGRAM pour envoyer un datagramme à un socket spécifique identifié par le paramètre *lpSockAddr* .

Pour envoyer une diffusion (sur un SOCK_DGRAM uniquement), l’adresse dans le paramètre *lpSockAddr* doit être construite à l’aide de l’adresse IP spéciale INADDR_BROADCAST (définie dans le fichier d’en-tête Windows Sockets Winsock. H) ainsi que le numéro de port souhaité. Ou, si le paramètre *lpszHostAddress* est null, le socket est configuré pour la diffusion. Il est généralement déconseillé pour un datagramme de diffusion de dépasser la taille à laquelle la fragmentation peut se produire, ce qui implique que la partie des données du datagramme (à l’exclusion des en-têtes) ne doit pas dépasser 512 octets.

##  <a name="setsockopt"></a>CAsyncSocket :: SetSockOpt

Appelez cette fonction membre pour définir une option de Socket.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Paramètres

*nOptionName*<br/>
Option de socket pour laquelle la valeur doit être définie.

*lpOptionValue*<br/>
Pointeur vers la mémoire tampon dans laquelle la valeur de l’option demandée est fournie.

*nOptionLen*<br/>
Taille de la mémoire tampon *lpOptionValue* en octets.

*nLevel*<br/>
Niveau auquel l’option est définie ; les seuls niveaux pris en charge sont SOL_SOCKET et IPPROTO_TCP.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEFAULT *lpOptionValue* ne fait pas partie d’un espace d’adressage de processus valide.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAEINVAL *nLevel* n’est pas valide ou les informations de *lpOptionValue* ne sont pas valides.

- La connexion WSAENETRESET a dépassé le délai d’attente lors de la définition de SO_KEEPALIVE.

- WSAENOPROTOOPT l’option est inconnue ou n’est pas prise en charge. En particulier, SO_BROADCAST n’est pas pris en charge sur les sockets de type SOCK_STREAM, tandis que SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER et SO_OOBINLINE ne sont pas pris en charge sur les sockets de type SOCK_DGRAM.

- La connexion WSAENOTCONN a été réinitialisée lorsque SO_KEEPALIVE est définie.

- WSAENOTSOCK le descripteur n’est pas un Socket.

### <a name="remarks"></a>Notes

`SetSockOpt` définit la valeur actuelle d’une option de socket associée à un socket de tout type, dans n’importe quel état. Bien que les options puissent exister à plusieurs niveaux de protocole, cette spécification définit uniquement les options qui existent au niveau « socket » le plus élevé. Les options affectent les opérations de socket, par exemple si les données expédiées sont reçues dans le flux de données normal, si les messages de diffusion peuvent être envoyés sur le socket, et ainsi de suite.

Il existe deux types d’options de socket : les options booléennes qui activent ou désactivent une fonctionnalité ou un comportement, et les options qui requièrent une valeur ou une structure entière. Pour activer une option booléenne, *lpOptionValue* pointe vers un entier différent de zéro. Pour désactiver l’option *lpOptionValue* pointe vers un entier égal à zéro. *nOptionLen* doit être égal à `sizeof(BOOL)` pour les options booléennes. Pour les autres options, *lpOptionValue* pointe vers l’entier ou la structure qui contient la valeur souhaitée pour l’option, tandis que *nOptionLen* est la longueur de l’entier ou de la structure.

SO_LINGER contrôle l’action entreprise lorsque les données non envoyées sont mises en file d’attente sur un socket et que la fonction `Close` est appelée pour fermer le Socket.

Par défaut, un socket ne peut pas être lié (voir [Bind](#bind)) à une adresse locale qui est déjà en cours d’utilisation. Toutefois, il peut être souhaitable de « réutiliser » une adresse de cette manière. Étant donné que chaque connexion est identifiée de manière unique par la combinaison d’adresses locales et distantes, il n’y a aucun problème avec deux sockets liés à la même adresse locale tant que les adresses distantes sont différentes.

Pour informer l’implémentation de Windows Sockets qu’un appel de `Bind` sur un socket ne doit pas être interdit, car l’adresse souhaitée est déjà utilisée par un autre Socket, l’application doit définir l’option de socket SO_REUSEADDR pour le socket avant d’émettre l’appel de `Bind`. Notez que l’option est interprétée uniquement au moment de l’appel de `Bind` : il est donc inutile (mais inoffensif) de définir l’option sur un socket qui ne doit pas être lié à une adresse existante, et la définition ou la réinitialisation de l’option après l’appel de `Bind` n’a aucun effet sur ce Socket ou sur un autre.

Une application peut demander que l’implémentation de Windows Sockets autorise l’utilisation de paquets « Keep-Alive » sur les connexions TCP (Transmission Control Protocol) en activant l’option SO_KEEPALIVE Socket. Une implémentation de Windows Sockets n’a pas besoin de prendre en charge l’utilisation des connexions persistantes : si c’est le cas, la sémantique précise est spécifique à l’implémentation, mais elle doit être conforme à la section 4.2.3.6 du document RFC 1122 : « configuration requise pour les hôtes Internet — couches de communication ». Si une connexion est supprimée à la suite de l’activité « Keep-Alive », le code d’erreur WSAENETRESET est renvoyé à tous les appels en cours sur le socket, et les appels suivants échouent avec WSAENOTCONN.

L’option TCP_NODELAY désactive l’algorithme Nagle. L’algorithme Nagle est utilisé pour réduire le nombre de petits paquets envoyés par un hôte en la mise en mémoire tampon des données d’envoi non acquittées jusqu’à ce qu’un paquet de taille réelle puisse être envoyé. Toutefois, pour certaines applications, cet algorithme peut nuire aux performances et TCP_NODELAY peut être utilisé pour le désactiver. Les enregistreurs d’applications ne doivent pas définir TCP_NODELAY, sauf si l’impact de cette action est bien compris et souhaité, car la définition de TCP_NODELAY peut avoir un impact négatif significatif sur les performances du réseau. TCP_NODELAY est la seule option de socket prise en charge qui utilise le niveau IPPROTO_TCP ; toutes les autres options utilisent le niveau SOL_SOCKET.

Certaines implémentations de Windows Sockets fournissent des informations de débogage de sortie si l’option SO_DEBUG est définie par une application.

Les options suivantes sont prises en charge pour les `SetSockOpt`. Le type identifie le type de données adressé par *lpOptionValue*.

|Valeur|Type|Signification|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|Autorise la transmission des messages de diffusion sur le Socket.|
|SO_DEBUG|BOOL|Enregistrer les informations de débogage.|
|SO_DONTLINGER|BOOL|Ne bloquez pas les `Close` en attente d’envoi de données non envoyées. La définition de cette option revient à définir SO_LINGER avec `l_onoff` définie sur zéro.|
|SO_DONTROUTE|BOOL|Ne pas Router : envoyer directement à l’interface.|
|SO_KEEPALIVE|BOOL|Envoyer des connexions persistantes.|
|SO_LINGER|`struct LINGER`|Attendre sur `Close` si des données non envoyées sont présentes.|
|SO_OOBINLINE|BOOL|Recevoir des données hors bande dans le flux de données normal.|
|SO_RCVBUF|**int**|Spécifiez la taille de la mémoire tampon pour les réceptions.|
|SO_REUSEADDR|BOOL|Autorisez la liaison du socket à une adresse qui est déjà en cours d’utilisation. (Voir [Bind](#bind).)|
|SO_SNDBUF|**int**|Spécifiez la taille de la mémoire tampon pour les envois.|
|TCP_NODELAY|BOOL|Désactive l'algorithme Nagle pour la fusion des envois.|

Les options BSD (Berkeley Software Distribution) ne sont pas prises en charge pour les `SetSockOpt` sont les suivantes :

|Valeur|Type|Signification|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Le socket est à l’écoute|
|SO_ERROR|**int**|Récupérez l’état d’erreur et désactivez.|
|SO_RCVLOWAT|**int**|Recevoir un seuil inférieur.|
|SO_RCVTIMEO|**int**|Délai d’attente de réception|
|SO_SNDLOWAT|**int**|Envoyer une borne basse.|
|SO_SNDTIMEO|**int**|Délai d’attente d’envoi.|
|SO_TYPE|**int**|Type du Socket.|
|IP_OPTIONS||Définir le champ d’options dans l’en-tête IP.|

##  <a name="shutdown"></a>CAsyncSocket :: ShutDown

Appelez cette fonction membre pour désactiver les envois, les réceptions, ou les deux sur le Socket.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Paramètres

*nHow*<br/>
Indicateur qui décrit les types d’opérations qui ne sont plus autorisés, à l’aide des valeurs énumérées suivantes :

- **reçoit = 0**

- **envois = 1**

- **both = 2**

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant [GetLastError](#getlasterror). Les erreurs suivantes s’appliquent à cette fonction membre :

- WSANOTINITIALISED un [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) réussi doit se produire avant d’utiliser cette API.

- WSAENETDOWN l’implémentation de Windows Sockets a détecté que le sous-système réseau a échoué.

- WSAEINVAL *nHow* n’est pas valide.

- WSAEINPROGRESS une opération de blocage des sockets Windows est en cours.

- WSAENOTCONN le socket n’est pas connecté (SOCK_STREAM uniquement).

- WSAENOTSOCK le descripteur n’est pas un Socket.

### <a name="remarks"></a>Notes

`ShutDown` est utilisé sur tous les types de sockets pour désactiver la réception, la transmission, ou les deux. Si *nHow* a la valeur 0, les réceptions ultérieures sur le socket ne sont pas autorisées. Cela n’a aucun effet sur les couches de protocole inférieures.

Pour le protocole TCP (Transmission Control Protocol), la fenêtre TCP n’est pas modifiée et les données entrantes sont acceptées (mais pas reconnues) jusqu’à ce que la fenêtre soit épuisée. Pour le protocole UDP (User Datagram Protocol), les datagrammes entrants sont acceptés et mis en file d’attente. Dans le cas contraire, un paquet d’erreur ICMP est généré. Si *nHow* est 1, les envois suivants ne sont pas autorisés. Pour les sockets TCP, une FIN sera envoyée. La définition de *nHow* sur la valeur 2 désactive à la fois les envois et les réceptions, comme décrit ci-dessus.

Notez que `ShutDown` ne ferme pas le socket et que les ressources attachées au socket ne sont pas libérées tant que `Close` n’est pas appelé. Une application ne doit pas s’appuyer sur la possibilité de réutiliser un socket une fois qu’il a été arrêté. En particulier, une implémentation de Windows Sockets n’est pas requise pour prendre en charge l’utilisation de `Connect` sur ce type de Socket.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CAsyncSocket :: OnReceive](#onreceive).

##  <a name="socket"></a>CASyncSocket :: Socket

Alloue un handle de Socket.

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
Masque de masque qui spécifie une combinaison d’événements réseau qui intéressent l’application.

- `FD_READ`: vous souhaitez recevoir une notification de préparation pour la lecture.

- `FD_WRITE`: vous souhaitez recevoir une notification de préparation à l’écriture.

- `FD_OOB`: vous souhaitez recevoir une notification de l’arrivée des données hors bande.

- `FD_ACCEPT`: souhaitez recevoir la notification des connexions entrantes.

- `FD_CONNECT`: vous souhaitez recevoir une notification de la connexion terminée.

- `FD_CLOSE`: vous souhaitez recevoir une notification de fermeture de Socket.

*nProtocolType*<br/>
Protocole à utiliser avec le socket qui est spécifique à la famille d’adresses indiquée.

*nAddressFormat*<br/>
Spécification de la famille d’adresses.

### <a name="return-value"></a>Valeur de retour

Retourne `TRUE` en cas de réussite, `FALSE` en cas d’échec.

### <a name="remarks"></a>Notes

Cette méthode alloue un handle de Socket. Il n’appelle pas [CAsyncSocket :: bind](#bind) pour lier le socket à une adresse spécifiée. vous devez donc appeler `Bind` ultérieurement pour lier le socket à une adresse spécifiée. Vous pouvez utiliser [CAsyncSocket :: SetSockOpt](#setsockopt) pour définir l’option de socket avant qu’elle ne soit liée.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSocket, classe](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
