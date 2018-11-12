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
ms.openlocfilehash: 3c5340a8c65f804747fd8d3c8bd31fb20f80c6ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487280"
---
# <a name="csocket-class"></a>CSocket (classe)

Dérive de `CAsyncSocket`hérite son encapsulation de l’API de Sockets Windows et représente un niveau supérieur d’abstraction à celle d’un `CAsyncSocket` objet.

## <a name="syntax"></a>Syntaxe

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|Construit un objet `CSocket`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSocket::Attach](#attach)|Attache un handle SOCKET à un `CSocket` objet.|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Annule un appel bloquant qui est actuellement en cours.|
|[CSocket::Create](#create)|Crée un socket.|
|[CSocket::FromHandle](#fromhandle)|Retourne un pointeur vers un `CSocket` objet, un handle de SOCKET.|
|[CSocket::IsBlocking](#isblocking)|Détermine si un appel bloquant est en cours d’exécution.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|Appelée pour traiter des messages en attente en attendant un appel de blocage.|

## <a name="remarks"></a>Notes

`CSocket` fonctionne avec les classes `CSocketFile` et `CArchive` pour gérer l’envoi et la réception de données.

Un `CSocket` objet également fournit un blocage, ce qui est essentiel au fonctionnement synchrone de `CArchive`. Blocage des fonctions, telles que `Receive`, `Send`, `ReceiveFrom`, `SendTo`, et `Accept` (hérités à partir de `CAsyncSocket`), ne retournent pas un `WSAEWOULDBLOCK` erreur dans `CSocket`. Au lieu de cela, ces fonctions patienter jusqu'à ce que l’opération se termine. En outre, l’appel d’origine se termine avec l’erreur WSAEINTR si `CancelBlockingCall` est appelée alors qu’une de ces fonctions ne bloque pas.

Pour utiliser un `CSocket` d’objet, appelez le constructeur, puis appelez `Create` pour créer le handle SOCKET sous-jacent (type de SOCKET). Les paramètres par défaut de `Create` créer un socket de flux de données, mais si vous n’utilisez pas le socket avec un `CArchive` objet, vous pouvez spécifier un paramètre pour créer un socket datagramme à la place, ou de la liaison à un port spécifique pour créer un socket de serveur. Se connecter à un socket de client à l’aide `Connect` côté client et `Accept` côté serveur. Puis créez un `CSocketFile` de l’objet et l’associer à la `CSocket` de l’objet dans le `CSocketFile` constructeur. Ensuite, créez un `CArchive` objet pour l’envoi et l’autre pour recevoir des données (si nécessaire), puis les associer avec le `CSocketFile` de l’objet dans le `CArchive` constructeur. Lorsque les communications sont terminées, détruisez le `CArchive`, `CSocketFile`, et `CSocket` objets. Le type de données SOCKET est décrit dans l’article [Windows Sockets : arrière-plan](../../mfc/windows-sockets-background.md).

Lorsque vous utilisez `CArchive` avec `CSocketFile` et `CSocket`, vous pouvez rencontrer une situation où `CSocket::Receive` entre dans une boucle (par `PumpMessages(FD_READ)`) en attente pour le montant demandé d’octets. Il s’agit, car les sockets Windows n'autorise qu’un seul appel reçues par notification FD_READ, mais `CSocketFile` et `CSocket` autoriser plusieurs appels reçus par FD_READ. Si vous obtenez un FD_READ lorsqu’il n’existe aucune donnée à lire, l’application se bloque. Si vous obtenez jamais FD_READ un autre, l’application s’arrête de communiquer via le socket.

Vous pouvez résoudre ce problème comme suit. Dans le `OnReceive` méthode de votre classe socket, appel `CAsyncSocket::IOCtl(FIONREAD, ...)` avant d’appeler le `Serialize` méthode de votre classe de message lorsque les données attendues à lire à partir du socket dépassent la taille d’un paquet TCP (unité de transmission maximale le support de réseau généralement au moins 1096 octets). Si la taille des données disponibles est inférieur au besoin, attendez que toutes les données d’être reçu et ensuite seulement, démarrer l’opération de lecture.

Dans l’exemple suivant, `m_dwExpected` est le nombre approximatif d’octets que l’utilisateur s’attend à recevoir. Il est supposé que vous le déclarer ailleurs dans votre code.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  Lors de l’utilisation de sockets MFC dans les threads secondaires dans une application MFC liée de manière statique, vous devez appeler `AfxSocketInit` dans chaque thread qui utilise des sockets pour initialiser les bibliothèques de socket. Par défaut, `AfxSocketInit` est uniquement appelée dans le thread principal.

Pour plus d’informations, consultez [Windows des Sockets dans MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets : fonctionnement de Sockets avec Archives travail](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets : ordre des opérations](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets : exemple de Sockets utilisant des Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxsock.h

##  <a name="attach"></a>  CSocket::Attach

Appelez cette fonction membre pour attacher le `hSocket` handle vers un `CSocket` objet.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle à un socket.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la fonction aboutit.

### <a name="remarks"></a>Notes

Le handle de SOCKET est stocké dans l’objet [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) membre de données.

Pour plus d’informations, consultez [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall

Appelez cette fonction membre pour annuler un appel bloquant actuellement en cours.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Notes

Cette fonction annule toute opération de blocage en attente pour ce socket. L’appel bloquant d’origine s’arrête dès que possible avec l’erreur WSAEINTR.

Dans le cas d’un blocage `Connect` opération, l’implémentation Windows Sockets va se terminer l’appel bloquant dès que possible, mais il est parfois impossible pour les ressources de socket à être libérée tant que la connexion a terminé (et ensuite été réinitialisé) ou expiration du délai. Cela est susceptible d’être perceptible uniquement si l’application essaie immédiatement pour ouvrir un nouveau socket (si aucun socket n’est disponible), ou pour vous connecter à la même homologue.

Annuler toute opération autre que `Accept` pouvez laisser le socket dans un état indéterminé. Si une application annule une opération de blocage sur un socket, la seule opération que l’application peut dépendre de la possibilité d’effectuer sur le socket est un appel à `Close`, bien que les autres opérations peuvent travailler sur certaines implémentations de Windows Sockets. Si vous le souhaitez une portabilité maximale pour votre application, vous devez être veiller à ne pas dépendent de l’exécution d’opérations après une annulation.

Pour plus d’informations, consultez [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>  CSocket::Create

Appelez le **créer** fonction membre après la construction d’un objet socket pour créer le socket de Windows et l’attacher.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Paramètres

*nSocketPort*<br/>
Un port particulier à utiliser avec le socket, ou 0 si vous souhaitez que MFC pour sélectionner un port.

*nSocketType*<br/>
SOCK_STREAM ou SOCK_DGRAM.

*lpszSocketAddress*<br/>
Un pointeur vers une chaîne contenant l’adresse réseau du socket connecté, un nombre en pointillés tels que « 128.56.22.8 ». En passant la valeur NULL de chaîne pour ce paramètre indique le `CSocket` instance doit écouter les activités des clients sur toutes les interfaces réseau.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; Sinon, 0 et un code d’erreur spécifique peuvent être récupérées en appelant `GetLastError`.

### <a name="remarks"></a>Notes

`Create` appelle ensuite `Bind` pour lier le socket à l’adresse spécifiée. Les types de socket suivants sont pris en charge :

- SOCK_STREAM fournit séquencé, flux d’octets fiables, bidirectionnels, orientés connexion. Utilise le protocole TCP (Transmission Control) pour la famille d’adresses Internet.

- Prend en charge SOCK_DGRAM datagrammes, qui sont des mémoires tampons non fiables, sans connexion, de longueur maximale fixe (généralement réduite). Utilise le protocole UDP (User Datagram) pour la famille d’adresses Internet. Pour utiliser cette option, vous ne devez pas utiliser le socket avec un `CArchive` objet.

    > [!NOTE]
    >  Le `Accept` fonction membre prend une référence à un vide `CSocket` objet comme paramètre. Vous devez créer cet objet avant d’appeler `Accept`. N’oubliez pas que si cet objet socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet socket.

Pour plus d’informations sur les sockets de flux de données et de datagramme, consultez les articles [Windows Sockets : arrière-plan](../../mfc/windows-sockets-background.md), [Windows Sockets : Ports et adresses de Socket](../../mfc/windows-sockets-ports-and-socket-addresses.md), et [Windows Sockets : à l’aide de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>  CSocket::CSocket

Construit un objet `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Notes

Après la construction, vous devez appeler la `Create` fonction membre.

Pour plus d’informations, consultez [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>  CSocket::FromHandle

Retourne un pointeur vers un `CSocket` objet.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle à un socket.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CSocket` de l’objet, ou NULL s’il n’existe aucun `CSocket` objet attaché à *hSocket*.

### <a name="remarks"></a>Notes

En fonction d’un handle de SOCKET, si un `CSocket` objet n’est pas attaché au handle, la fonction membre retourne la valeur NULL et ne crée pas d’un objet temporaire.

Pour plus d’informations, consultez [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>  CSocket::IsBlocking

Appelez cette fonction membre pour déterminer si un appel bloquant est en cours d’exécution.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le socket est blocage ; sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>  CSocket::OnMessagePending

Remplacez cette fonction membre pour rechercher des messages spécifiques à partir de Windows et y répondre dans votre socket.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le message a été géré ; sinon 0.

### <a name="remarks"></a>Notes

Il s’agit d’une avancée substituable.

Le framework appelle `OnMessagePending` tandis que le socket est pompage des messages Windows pour vous permettre de traiter les messages présentant un intérêt pour votre application. Pour obtenir des exemples d’utilisation de `OnMessagePending`, consultez l’article [Windows Sockets : dérivation à partir de Classes de sockets](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Pour plus d’informations, consultez [Windows Sockets : utilisation de Sockets avec des Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Voir aussi

[CAsyncSocket, classe](../../mfc/reference/casyncsocket-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket, classe](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
