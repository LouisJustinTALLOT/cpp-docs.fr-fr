---
title: CSocket (classe)
ms.date: 11/04/2016
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854545"
---
# <a name="csocket-class"></a>CSocket (classe)

Dérive de `CAsyncSocket`, hérite de son encapsulation de l’API Windows Sockets et représente un niveau d’abstraction plus élevé que celui d’un objet `CAsyncSocket`.

## <a name="syntax"></a>Syntaxe

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CSocket :: CSocket](#csocket)|Construit un objet `CSocket`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CSocket :: Attach](#attach)|Attache un handle de SOCKET à un objet `CSocket`.|
|[CSocket :: CancelBlockingCall](#cancelblockingcall)|Annule un appel bloquant qui est actuellement en cours.|
|[CSocket :: Create](#create)|Crée un Socket.|
|[CSocket :: FromHandle](#fromhandle)|Retourne un pointeur vers un objet `CSocket`, à partir d’un handle de SOCKET.|
|[CSocket :: IsBlocking](#isblocking)|Détermine si un appel bloquant est en cours.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[CSocket :: OnMessagePending](#onmessagepending)|Appelé pour traiter les messages en attente en attendant qu’un appel bloquant se termine.|

## <a name="remarks"></a>Notes

`CSocket` fonctionne avec les classes `CSocketFile` et `CArchive` pour gérer l’envoi et la réception des données.

Un objet `CSocket` fournit également un blocage, ce qui est essentiel pour l’opération synchrone de `CArchive`. Les fonctions de blocage, telles que `Receive`, `Send`, `ReceiveFrom`, `SendTo`et `Accept` (toutes héritées de `CAsyncSocket`), ne retournent pas d’erreur `WSAEWOULDBLOCK` dans `CSocket`. Au lieu de cela, ces fonctions attendent que l’opération se termine. En outre, l’appel d’origine se termine avec l’erreur WSAEINTR si `CancelBlockingCall` est appelée alors que l’une de ces fonctions bloque.

Pour utiliser un objet `CSocket`, appelez le constructeur, puis appelez `Create` pour créer le handle de SOCKET sous-jacent (SOCKET de type). Les paramètres par défaut de `Create` créer un socket de flux, mais si vous n’utilisez pas le socket avec un objet `CArchive`, vous pouvez spécifier un paramètre pour créer un socket de datagramme à la place, ou effectuer une liaison à un port spécifique pour créer un socket serveur. Connectez-vous à un socket client à l’aide de `Connect` côté client et `Accept` côté serveur. Créez ensuite un objet `CSocketFile` et associez-le à l’objet `CSocket` dans le constructeur `CSocketFile`. Ensuite, créez un objet `CArchive` pour l’envoi et un pour la réception de données (si nécessaire), puis associez-les à l’objet `CSocketFile` dans le constructeur `CArchive`. Une fois les communications terminées, détruisez les objets `CArchive`, `CSocketFile`et `CSocket`. Le type de données SOCKET est décrit dans l’article [Windows Sockets : Background](../../mfc/windows-sockets-background.md).

Lorsque vous utilisez `CArchive` avec `CSocketFile` et `CSocket`, vous pouvez rencontrer une situation dans laquelle `CSocket::Receive` entre une boucle (par `PumpMessages(FD_READ)`) en attente de la quantité d’octets demandée. Cela est dû au fait que Windows Sockets n’autorise qu’un seul appel de réception par FD_READ notification, mais `CSocketFile` et `CSocket` autoriser plusieurs appels de réception par FD_READ. Si vous recevez une FD_READ lorsqu’il n’y a aucune donnée à lire, l’application se bloque. Si vous ne recevez jamais un autre FD_READ, l’application cesse de communiquer sur le Socket.

Vous pouvez résoudre ce problème comme suit. Dans la méthode `OnReceive` de votre classe Socket, appelez `CAsyncSocket::IOCtl(FIONREAD, ...)` avant d’appeler la méthode `Serialize` de votre classe de message lorsque les données attendues à lire à partir du socket dépassent la taille d’un paquet TCP (unité de transmission maximale du support réseau, généralement au moins 1096 octets). Si la taille des données disponibles est inférieure à celle nécessaire, attendez que toutes les données soient reçues, puis démarrez l’opération de lecture.

Dans l’exemple suivant, `m_dwExpected` est le nombre approximatif d’octets que l’utilisateur s’attend à recevoir. Il est supposé que vous le déclarez ailleurs dans votre code.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  Lorsque vous utilisez des sockets MFC dans des threads secondaires dans une application MFC liée de manière statique, vous devez appeler `AfxSocketInit` dans chaque thread qui utilise des sockets pour initialiser les bibliothèques de Sockets. Par défaut, `AfxSocketInit` est appelé uniquement dans le thread principal.

Pour plus d’informations, consultez [Windows Sockets dans MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets : fonctionnement des sockets avec les archives](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets : séquence d’opérations](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets : exemple de sockets utilisant des archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Spécifications

**En-tête :** AfxSock. h

##  <a name="attach"></a>CSocket :: Attach

Appelez cette fonction membre pour attacher le handle de `hSocket` à un objet `CSocket`.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle vers un Socket.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la fonction aboutit.

### <a name="remarks"></a>Notes

Le handle de SOCKET est stocké dans le membre de données [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) de l’objet.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>CSocket :: CancelBlockingCall

Appelez cette fonction membre pour annuler un appel bloquant en cours.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Notes

Cette fonction annule toute opération de blocage en suspens pour ce Socket. L’appel de blocage d’origine se termine dès que possible avec l’erreur WSAEINTR.

Dans le cas d’une opération de `Connect` bloquante, l’implémentation de Windows Sockets met fin à l’appel bloquant dès que possible, mais il n’est pas possible que les ressources de socket soient libérées tant que la connexion n’est pas terminée (et qu’elle n’a pas été réinitialisée) ou a expiré. Cela peut être perceptible uniquement si l’application tente immédiatement d’ouvrir un nouveau socket (si aucun socket n’est disponible) ou de se connecter au même homologue.

L’annulation d’une opération autre que `Accept` peut rendre le socket dans un état indéterminé. Si une application annule une opération de blocage sur un socket, la seule opération que l’application peut dépendre de la possibilité d’effectuer sur le socket est un appel à `Close`, bien que d’autres opérations puissent fonctionner sur certaines implémentations de Windows Sockets. Si vous souhaitez une portabilité maximale pour votre application, vous devez veiller à ne pas dépendre de l’exécution d’opérations après une annulation.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>CSocket :: Create

Appelez la fonction membre **Create** après avoir construit un objet Socket pour créer le socket Windows et l’attacher.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Paramètres

*nSocketPort*<br/>
Un port particulier à utiliser avec le socket, ou 0 si vous souhaitez que MFC sélectionne un port.

*nSocketType*<br/>
SOCK_STREAM ou SOCK_DGRAM.

*lpszSocketAddress*<br/>
Pointeur vers une chaîne contenant l’adresse réseau du socket connecté, un nombre en pointillés tel que « 128.56.22.8 ». Le passage de la chaîne NULL pour ce paramètre indique que l’instance de `CSocket` doit écouter l’activité des clients sur toutes les interfaces réseau.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction réussit ; Sinon, il peut s’agir de la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant `GetLastError`.

### <a name="remarks"></a>Notes

`Create` appelle ensuite `Bind` pour lier le socket à l’adresse spécifiée. Les types de sockets suivants sont pris en charge :

- SOCK_STREAM fournit des flux d’octets séquencés, fiables, bidirectionnels basés sur une connexion. Utilise le protocole TCP (Transmission Control Protocol) pour la famille d’adresses Internet.

- SOCK_DGRAM prend en charge les datagrammes, qui sont des mémoires tampons non fiables, sans connexion, d’une longueur maximale fixe (généralement petite). Utilise le protocole UDP (User Datagram Protocol) pour la famille d’adresses Internet. Pour utiliser cette option, vous ne devez pas utiliser le socket avec un objet `CArchive`.

    > [!NOTE]
    >  La fonction membre `Accept` accepte une référence à un nouvel objet `CSocket` vide comme paramètre. Vous devez construire cet objet avant d’appeler `Accept`. Gardez à l’esprit que si cet objet Socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet Socket.

Pour plus d’informations sur les sockets de flux et de datagrammes, consultez les articles [Windows Sockets : arrière-plan](../../mfc/windows-sockets-background.md), [Windows Sockets : ports et adresses de sockets](../../mfc/windows-sockets-ports-and-socket-addresses.md), et [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>CSocket :: CSocket

Construit un objet `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Notes

Après la construction, vous devez appeler la fonction membre `Create`.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>CSocket :: FromHandle

Retourne un pointeur vers un objet `CSocket`.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle vers un Socket.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CSocket`, ou NULL s’il n’existe aucun objet `CSocket` attaché à *hSocket*.

### <a name="remarks"></a>Notes

Lorsqu’un handle de SOCKET est attribué à un objet `CSocket` n’est pas attaché au descripteur, la fonction membre retourne la valeur NULL et ne crée pas d’objet temporaire.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>CSocket :: IsBlocking

Appelez cette fonction membre pour déterminer si un appel bloquant est en cours.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le socket est bloquant ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>CSocket :: OnMessagePending

Remplacez cette fonction membre pour rechercher des messages spécifiques de Windows et y répondre dans votre Socket.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le message a été géré ; Sinon, 0.

### <a name="remarks"></a>Notes

Il s’agit d’un substituable avancé.

Le Framework appelle `OnMessagePending` tandis que le socket pompe les messages Windows pour vous permettre de traiter les messages présentant un intérêt pour votre application. Pour obtenir des exemples d’utilisation de `OnMessagePending`, consultez l’article [Windows Sockets : dérivation à partir des classes de socket](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Voir aussi

[CAsyncSocket, classe](../../mfc/reference/casyncsocket-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket, classe](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
