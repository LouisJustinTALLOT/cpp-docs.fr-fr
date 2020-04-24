---
title: CSocket, classe
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
ms.openlocfilehash: 730bea34354b008d641ecc28e7368f79efad12a7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751155"
---
# <a name="csocket-class"></a>CSocket, classe

Dérive de `CAsyncSocket`, hérite de son encapsulation de l’API Windows Sockets, `CAsyncSocket` et représente un niveau plus élevé d’abstraction que celle d’un objet.

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
|[CSocket::Attach](#attach)|Attache une poignée SOCKET `CSocket` à un objet.|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Annule un appel de blocage qui est actuellement en cours.|
|[CSocket::Créer](#create)|Crée une prise.|
|[CSocket::DeHandle](#fromhandle)|Renvoie un `CSocket` pointeur à un objet, étant donné une poignée SOCKET.|
|[CSocket::IsBlocking](#isblocking)|Détermine si un appel de blocage est en cours.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|Appelé à traiter les messages en attente en attendant qu’un appel de blocage soit terminé.|

## <a name="remarks"></a>Notes

`CSocket`travaille avec `CSocketFile` `CArchive` les classes et de gérer l’envoi et la réception de données.

Un `CSocket` objet fournit également le blocage, qui est `CArchive`essentiel au fonctionnement synchrone de . Blocking fonctions, `Receive`telles `Send` `ReceiveFrom`que `SendTo`, `Accept` , , `CAsyncSocket`et (tous `WSAEWOULDBLOCK` hérités de ), ne retournent pas une erreur dans `CSocket`. Au lieu de cela, ces fonctions attendent jusqu’à ce que l’opération se termine. En outre, l’appel d’origine se terminera `CancelBlockingCall` avec l’erreur WSAEINTR si elle est appelée alors que l’une de ces fonctions bloque.

Pour utiliser `CSocket` un objet, appelez le `Create` constructeur, puis appelez pour créer la poignée SOCKET sous-jacente (type SOCKET). Les paramètres par `Create` défaut de créer une prise de flux, mais `CArchive` si vous n’utilisez pas la prise avec un objet, vous pouvez spécifier un paramètre pour créer une prise de datagram à la place, ou se lier à un port spécifique pour créer une prise de serveur. Connectez-vous à `Connect` une prise client `Accept` en utilisant du côté du client et du côté du serveur. Ensuite, `CSocketFile` créez un objet `CSocket` et associez-le à l’objet dans le `CSocketFile` constructeur. Ensuite, créez `CArchive` un objet pour l’envoi et un pour `CSocketFile` recevoir des `CArchive` données (au besoin), puis associez-les à l’objet dans le constructeur. Lorsque les communications sont `CArchive` `CSocketFile`terminées, détruisez le , , et les `CSocket` objets. Le type de données SOCKET est décrit dans l’article [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

Lorsque vous `CArchive` `CSocketFile` utilisez `CSocket`avec et , `CSocket::Receive` vous pouvez rencontrer `PumpMessages(FD_READ)`une situation où entre une boucle (par ) en attente du montant demandé des octets. C’est parce que les prises Windows n’autorisent qu’un seul appel de recv par FD_READ notification, mais `CSocketFile` et `CSocket` permettent plusieurs appels de recv par FD_READ. Si vous obtenez un FD_READ lorsqu’il n’y a pas de données à lire, l’application est suspendue. Si vous n’obtenez jamais un autre FD_READ, l’application cesse de communiquer sur la prise.

Vous pouvez résoudre ce problème comme suit. Dans `OnReceive` la méthode de votre `CAsyncSocket::IOCtl(FIONREAD, ...)` classe de `Serialize` prise, appelez avant d’appeler la méthode de votre classe de message lorsque les données attendues à lire à partir de la prise dépasse la taille d’un paquet TCP (unité de transmission maximale du support réseau, généralement au moins 1096 octets). Si la taille des données disponibles est inférieure aux besoins, attendez que toutes les données soient reçues et seulement alors commencez l’opération de lecture.

Dans l’exemple `m_dwExpected` suivant, se trouve le nombre approximatif d’octets que l’utilisateur s’attend à recevoir. On suppose que vous le déclarez ailleurs dans votre code.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
> Lorsque vous utilisez des prises MFC dans des threads secondaires dans `AfxSocketInit` une application MFC statiquement liée, vous devez appeler dans chaque thread qui utilise des prises pour initialiser les bibliothèques de prises. Par défaut, `AfxSocketInit` est appelé uniquement dans le fil principal.

Pour plus d’informations, voir [Windows Sockets in MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md), Windows [Sockets: How Sockets with Archives Work](../../mfc/windows-sockets-how-sockets-with-archives-work.md), Windows [Sockets: Sequence of Operations](../../mfc/windows-sockets-sequence-of-operations.md), Windows [Sockets: Example of Sockets Using Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Spécifications

**En-tête:** afxsock.h

## <a name="csocketattach"></a><a name="attach"></a>CSocket::Attach

Appelez cette fonction de `hSocket` membre `CSocket` pour attacher la poignée à un objet.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient une poignée à une prise.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si la fonction aboutit.

### <a name="remarks"></a>Notes

La poignée SOCKET est stockée dans le membre de données [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) de l’objet.

Pour plus d’informations, voir [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

## <a name="csocketcancelblockingcall"></a><a name="cancelblockingcall"></a>CSocket::CancelBlockingCall

Appelez cette fonction de membre pour annuler un appel de blocage actuellement en cours.

```cpp
void CancelBlockingCall();
```

### <a name="remarks"></a>Notes

Cette fonction annule toute opération de blocage en suspens pour cette prise. L’appel de blocage d’origine se terminera dès que possible avec l’erreur WSAEINTR.

Dans le cas `Connect` d’une opération de blocage, l’implémentation de Windows Sockets mettra fin à l’appel de blocage dès que possible, mais il peut ne pas être possible que les ressources de prise soient libérées tant que la connexion n’a pas été achevée (et ensuite réinitialisée) ou qu’elle soit désintégée. Cela ne sera probablement perceptible que si l’application tente immédiatement d’ouvrir une nouvelle prise (si aucune prise n’est disponible), ou de se connecter au même pair.

Annuler toute opération `Accept` autre que peut laisser la prise dans un état indéterminé. Si une application annule une opération de blocage sur une prise, la seule opération que l’application `Close`peut dépendre de la possibilité d’effectuer sur la prise est un appel à , bien que d’autres opérations peuvent fonctionner sur certaines implémentations Windows Sockets. Si vous désirez une portabilité maximale pour votre demande, vous devez faire attention de ne pas dépendre des opérations d’exécution après une annulation.

Pour plus d’informations, voir [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcreate"></a><a name="create"></a>CSocket::Créer

Appelez la fonction **membre Create** après la construction d’un objet de prise pour créer la prise Windows et l’attacher.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Paramètres

*nSocketPort (en)*<br/>
Un port particulier à utiliser avec la prise, ou 0 si vous voulez que MFC sélectionne un port.

*nSocketType (en)*<br/>
SOCK_STREAM ou SOCK_DGRAM.

*lpszSocketAddress*<br/>
Un pointeur à une chaîne contenant l’adresse réseau de la prise connectée, un numéro pointillé tel que "128.56.22.8". Passer la chaîne NULL pour `CSocket` ce paramètre indique que l’instance doit écouter l’activité client sur toutes les interfaces réseau.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction est réussie; sinon 0, et un code d’erreur `GetLastError`spécifique peut être récupéré en appelant .

### <a name="remarks"></a>Notes

`Create`appelle `Bind` ensuite à lier la prise à l’adresse spécifiée. Les types de prises suivants sont pris en charge :

- SOCK_STREAM Fournit des flux d’accessoires séquencés, fiables, bidirectionnels basés sur la connexion. Utilise le protocole de contrôle de transmission (TCP) pour la famille d’adresses Internet.

- SOCK_DGRAM prend en charge les datagrammes, qui sont des tampons sans connexion et peu fiables d’une longueur maximale fixe (généralement petite). Utilise le protocole de datagram d’utilisateur (UDP) pour la famille d’adresses Internet. Pour utiliser cette option, vous ne devez `CArchive` pas utiliser la prise avec un objet.

    > [!NOTE]
    >  La `Accept` fonction membre fait référence à `CSocket` un nouvel objet vide comme paramètre. Vous devez construire cet `Accept`objet avant d’appeler . Gardez à l’esprit que si cet objet de prise sort de portée, la connexion se ferme. N’appelez `Create` pas pour ce nouvel objet de prise.

Pour plus d’informations sur les prises de flux et de datagram, voir les articles [Windows Sockets: Background](../../mfc/windows-sockets-background.md), [Windows Sockets: Ports and Socket Addresses](../../mfc/windows-sockets-ports-and-socket-addresses.md), et Windows [Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcsocket"></a><a name="csocket"></a>CSocket::CSocket

Construit un objet `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Notes

Après la construction, `Create` vous devez appeler la fonction membre.

Pour plus d’informations, voir [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketfromhandle"></a><a name="fromhandle"></a>CSocket::DeHandle

Retourne un pointeur à un `CSocket` objet.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Paramètres

*hSocket*<br/>
Contient une poignée à une prise.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CSocket` vers un objet, `CSocket` ou NULL s’il n’y a pas d’objet attaché à *hSocket*.

### <a name="remarks"></a>Notes

Lorsqu’on lui donne une `CSocket` poignée SOCKET, si un objet n’est pas attaché à la poignée, la fonction membre renvoie NULL et ne crée pas d’objet temporaire.

Pour plus d’informations, voir [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketisblocking"></a><a name="isblocking"></a>CSocket::IsBlocking

Appelez cette fonction de membre pour déterminer si un appel de blocage est en cours.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la prise bloque; sinon 0.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketonmessagepending"></a><a name="onmessagepending"></a>CSocket::OnMessagePending

Remplacez cette fonction de membre pour rechercher des messages particuliers de Windows et y répondre dans votre prise.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le message a été manipulé; sinon 0.

### <a name="remarks"></a>Notes

C’est un avancé primordial.

Le cadre `OnMessagePending` appelle pendant que la prise pompe les messages Windows pour vous donner l’occasion de traiter les messages d’intérêt pour votre application. Pour des exemples `OnMessagePending`de la façon dont vous pourriez utiliser , voir l’article [Windows Sockets: Deriving from Socket Classes](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Pour plus d’informations, voir [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Voir aussi

[Classe CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile, classe](../../mfc/reference/csocketfile-class.md)
