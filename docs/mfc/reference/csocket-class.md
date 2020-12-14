---
description: 'En savoir plus sur : CSocket, classe'
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
ms.openlocfilehash: e04fc0b453c4d4172fcd286b142d029bda0eb5dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345106"
---
# <a name="csocket-class"></a>CSocket (classe)

Dérive de `CAsyncSocket` , hérite de son encapsulation de l’API Windows Sockets et représente un niveau d’abstraction plus élevé que celui d’un `CAsyncSocket` objet.

## <a name="syntax"></a>Syntaxe

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSocket :: CSocket](#csocket)|Construit un objet `CSocket`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSocket :: Attach](#attach)|Attache un handle de SOCKET à un `CSocket` objet.|
|[CSocket :: CancelBlockingCall](#cancelblockingcall)|Annule un appel bloquant qui est actuellement en cours.|
|[CSocket :: Create](#create)|Crée un Socket.|
|[CSocket :: FromHandle](#fromhandle)|Retourne un pointeur vers un `CSocket` objet, à partir d’un handle de Socket.|
|[CSocket :: IsBlocking](#isblocking)|Détermine si un appel bloquant est en cours.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CSocket :: OnMessagePending](#onmessagepending)|Appelé pour traiter les messages en attente en attendant qu’un appel bloquant se termine.|

## <a name="remarks"></a>Notes

`CSocket` fonctionne avec `CSocketFile` les classes et `CArchive` pour gérer l’envoi et la réception de données.

Un `CSocket` objet fournit également un blocage, ce qui est essentiel pour l’opération synchrone de `CArchive` . Les fonctions de blocage, telles que,,, `Receive` `Send` `ReceiveFrom` `SendTo` et `Accept` (toutes héritées de `CAsyncSocket` ), ne retournent pas d' `WSAEWOULDBLOCK` erreur dans `CSocket` . Au lieu de cela, ces fonctions attendent que l’opération se termine. En outre, l’appel d’origine se termine avec l’erreur WSAEINTR si `CancelBlockingCall` est appelé alors que l’une de ces fonctions bloque.

Pour utiliser un `CSocket` objet, appelez le constructeur, puis appelez `Create` pour créer le handle de Socket sous-jacent (Socket de type). Les paramètres par défaut de `Create` créent un socket de flux, mais si vous n’utilisez pas le socket avec un `CArchive` objet, vous pouvez spécifier un paramètre pour créer un socket de datagramme à la place, ou effectuer une liaison à un port spécifique pour créer un socket serveur. Connectez-vous à un socket client en utilisant `Connect` côté client et côté `Accept` serveur. Créez ensuite un `CSocketFile` objet et associez-le à l' `CSocket` objet dans le `CSocketFile` constructeur. Ensuite, créez un `CArchive` objet pour l’envoi et un pour la réception de données (si nécessaire), puis associez-les à l' `CSocketFile` objet dans le `CArchive` constructeur. Une fois les communications terminées, détruisez les `CArchive` `CSocketFile` objets, et `CSocket` . Le type de données SOCKET est décrit dans l’article [Windows Sockets : Background](../../mfc/windows-sockets-background.md).

Quand vous utilisez `CArchive` avec `CSocketFile` et `CSocket` , vous pouvez rencontrer une situation dans laquelle `CSocket::Receive` entre une boucle (par `PumpMessages(FD_READ)` ) en attente de la quantité d’octets demandée. Cela est dû au fait que Windows Sockets n’autorise qu’un seul appel de réception par FD_READ notification, mais `CSocketFile` et `CSocket` autorise plusieurs appels de réception par FD_READ. Si vous recevez une FD_READ lorsqu’il n’y a aucune donnée à lire, l’application se bloque. Si vous ne recevez jamais un autre FD_READ, l’application cesse de communiquer sur le Socket.

Vous pouvez résoudre ce problème comme suit. Dans la `OnReceive` méthode de votre classe Socket, appelez `CAsyncSocket::IOCtl(FIONREAD, ...)` avant d’appeler la `Serialize` méthode de votre classe de message lorsque les données attendues à lire à partir du socket dépassent la taille d’un paquet TCP (unité de transmission maximale du support réseau, généralement au moins 1096 octets). Si la taille des données disponibles est inférieure à celle nécessaire, attendez que toutes les données soient reçues, puis démarrez l’opération de lecture.

Dans l’exemple suivant, `m_dwExpected` représente le nombre approximatif d’octets que l’utilisateur s’attend à recevoir. Il est supposé que vous le déclarez ailleurs dans votre code.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
> Lorsque vous utilisez des sockets MFC dans des threads secondaires dans une application MFC liée de manière statique, vous devez appeler `AfxSocketInit` dans chaque thread qui utilise des sockets pour initialiser les bibliothèques de Sockets. Par défaut, `AfxSocketInit` est appelé uniquement dans le thread principal.

Pour plus d’informations, consultez [Windows Sockets dans MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets : fonctionnement des sockets avec les archives](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets : séquence d’opérations](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets : exemple de sockets utilisant des archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Spécifications

**En-tête :** AfxSock. h

## <a name="csocketattach"></a><a name="attach"></a> CSocket :: Attach

Appelez cette fonction membre pour attacher le `hSocket` handle à un `CSocket` objet.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle vers un Socket.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si la fonction aboutit.

### <a name="remarks"></a>Notes

Le handle de SOCKET est stocké dans le membre de données [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) de l’objet.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

## <a name="csocketcancelblockingcall"></a><a name="cancelblockingcall"></a> CSocket :: CancelBlockingCall

Appelez cette fonction membre pour annuler un appel bloquant en cours.

```cpp
void CancelBlockingCall();
```

### <a name="remarks"></a>Notes

Cette fonction annule toute opération de blocage en suspens pour ce Socket. L’appel de blocage d’origine se termine dès que possible avec l’erreur WSAEINTR.

Dans le cas d’une opération de blocage `Connect` , l’implémentation de Windows Sockets met fin à l’appel bloquant dès que possible, mais il n’est pas possible que les ressources de socket soient libérées tant que la connexion n’est pas terminée (puis réinitialisée) ou n’a pas expiré. Cela peut être perceptible uniquement si l’application tente immédiatement d’ouvrir un nouveau socket (si aucun socket n’est disponible) ou de se connecter au même homologue.

L’annulation d’une opération autre que `Accept` peut quitter le socket dans un état indéterminé. Si une application annule une opération de blocage sur un socket, la seule opération que l’application peut dépendre de la possibilité d’effectuer sur le socket est un appel à `Close` , bien que d’autres opérations puissent fonctionner sur certaines implémentations de Windows Sockets. Si vous souhaitez une portabilité maximale pour votre application, vous devez veiller à ne pas dépendre de l’exécution d’opérations après une annulation.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcreate"></a><a name="create"></a> CSocket :: Create

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
Pointeur vers une chaîne contenant l’adresse réseau du socket connecté, un nombre en pointillés tel que « 128.56.22.8 ». Le passage de la chaîne NULL pour ce paramètre indique que l' `CSocket` instance doit écouter l’activité des clients sur toutes les interfaces réseau.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction réussit ; Sinon, elle a la valeur 0, et un code d’erreur spécifique peut être récupéré en appelant `GetLastError` .

### <a name="remarks"></a>Notes

`Create` appelle ensuite `Bind` pour lier le socket à l’adresse spécifiée. Les types de sockets suivants sont pris en charge :

- SOCK_STREAM fournit des flux d’octets séquencés, fiables, bidirectionnels basés sur une connexion. Utilise le protocole TCP (Transmission Control Protocol) pour la famille d’adresses Internet.

- SOCK_DGRAM prend en charge les datagrammes, qui sont des mémoires tampons non fiables, sans connexion, d’une longueur maximale fixe (généralement petite). Utilise le protocole UDP (User Datagram Protocol) pour la famille d’adresses Internet. Pour utiliser cette option, vous ne devez pas utiliser le socket avec un `CArchive` objet.

    > [!NOTE]
    >  La `Accept` fonction membre accepte une référence à un nouvel objet vide `CSocket` comme paramètre. Vous devez construire cet objet avant d’appeler `Accept` . Gardez à l’esprit que si cet objet Socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet Socket.

Pour plus d’informations sur les sockets de flux et de datagrammes, consultez les articles [Windows Sockets : arrière-plan](../../mfc/windows-sockets-background.md), [Windows Sockets : ports et adresses de sockets](../../mfc/windows-sockets-ports-and-socket-addresses.md), et [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcsocket"></a><a name="csocket"></a> CSocket :: CSocket

Construit un objet `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Notes

Après la construction, vous devez appeler la `Create` fonction membre.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketfromhandle"></a><a name="fromhandle"></a> CSocket :: FromHandle

Retourne un pointeur vers un `CSocket` objet.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient un handle vers un Socket.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un `CSocket` objet, ou null s’il n’y a aucun `CSocket` objet attaché à *hSocket*.

### <a name="remarks"></a>Notes

Lorsqu’il reçoit un handle de SOCKET, si un `CSocket` objet n’est pas attaché au descripteur, la fonction membre retourne la valeur null et ne crée pas d’objet temporaire.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketisblocking"></a><a name="isblocking"></a> CSocket :: IsBlocking

Appelez cette fonction membre pour déterminer si un appel bloquant est en cours.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le socket est bloquant ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketonmessagepending"></a><a name="onmessagepending"></a> CSocket :: OnMessagePending

Remplacez cette fonction membre pour rechercher des messages spécifiques de Windows et y répondre dans votre Socket.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le message a été géré ; Sinon, 0.

### <a name="remarks"></a>Notes

Il s’agit d’un substituable avancé.

Le Framework appelle `OnMessagePending` alors que le socket pompe les messages Windows pour vous permettre de traiter les messages présentant un intérêt pour votre application. Pour obtenir des exemples de la façon dont vous pouvez utiliser `OnMessagePending` , consultez l’article [Windows Sockets : dérivation à partir des classes de socket](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Voir aussi

[CAsyncSocket (classe)](../../mfc/reference/casyncsocket-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket (classe)](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
