---
description: 'En savoir plus sur : Windows Sockets : classement des octets'
title: 'Windows Sockets : classement des octets'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: d143967fdcc9b4d1dac772bf0fe25b67d70aef53
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118652"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets : classement des octets

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article traite du classement des octets. Les autres problèmes sont abordés dans les articles suivants : [Windows Sockets : Blocking](../mfc/windows-sockets-blocking.md) et [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md).

Si vous utilisez ou dérivez de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devrez gérer ces problèmes vous-même. Si vous utilisez ou dérivez de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gère pour vous.

## <a name="byte-ordering"></a>Classement des octets

Les différentes architectures d’ordinateur stockent parfois des données à l’aide de différentes commandes d’octet. Par exemple, les machines Intel stockent les données dans l’ordre inverse des machines Macintosh (Motorola). L’ordre d’octet Intel, appelé « Little endian », est également l’inverse de l’ordre « Big-endian » standard du réseau. Le tableau suivant décrit ces termes.

### <a name="big--and-little-endian-byte-ordering"></a>Classement des octets Big-and-Little-Endian

|Classement des octets|Signification|
|-------------------|-------------|
|Big-Endian|L’octet le plus significatif se trouve à l’extrémité gauche d’un mot.|
|Little-Endian|L’octet le plus significatif se trouve à l’extrémité droite d’un mot.|

En règle générale, vous n’avez pas à vous soucier de la conversion de l’ordre des octets pour les données que vous envoyez et recevez sur le réseau, mais il existe des situations dans lesquelles vous devez convertir des commandes d’octet.

## <a name="when-you-must-convert-byte-orders"></a>Lorsque vous devez convertir des commandes d’octet

Vous devez convertir les ordres d’octet dans les cas suivants :

- Vous transmettez des informations qui doivent être interprétées par le réseau, par opposition aux données que vous envoyez à un autre ordinateur. Par exemple, vous pouvez transmettre des ports et des adresses que le réseau doit comprendre.

- L’application serveur avec laquelle vous communiquez n’est pas une application MFC (et vous n’avez pas de code source pour celle-ci). Cela requiert des conversions d’ordre d’octet si les deux ordinateurs ne partagent pas le même classement des octets.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Lorsque vous n’avez pas besoin de convertir des commandes d’octet

Vous pouvez éviter le travail de conversion des ordres d’octet dans les cas suivants :

- Les machines situées aux deux extrémités peuvent accepter de ne pas échanger des octets, et les deux ordinateurs utilisent le même ordre d’octet.

- Le serveur avec lequel vous communiquez est une application MFC.

- Vous disposez d’un code source pour le serveur avec lequel vous communiquez. vous pouvez donc indiquer explicitement si vous devez convertir les commandes d’octet ou non.

- Vous pouvez déplacer le serveur vers MFC. C’est assez facile à faire, et le résultat est généralement plus petit et plus rapide.

En utilisant [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devez gérer vous-même toutes les conversions d’ordre d’octet nécessaires. Windows Sockets normalise le modèle d’ordre d’octet « Big-endian » et fournit des fonctions pour effectuer une conversion entre cet ordre et d’autres. [CArchive](../mfc/reference/carchive-class.md), toutefois, que vous utilisez avec [CSocket](../mfc/reference/csocket-class.md), utilise l’ordre inverse (« Little endian »), mais gère `CArchive` les détails des conversions d’ordre d’octet pour vous. En utilisant ce classement standard dans vos applications, ou en utilisant les fonctions de conversion d’ordre d’octet de Windows Sockets, vous pouvez rendre votre code plus portable.

Le cas idéal pour l’utilisation des sockets MFC est lorsque vous écrivez les deux extrémités de la communication : à l’aide de MFC aux deux extrémités. Si vous écrivez une application qui communique avec des applications non-MFC, par exemple un serveur FTP, vous devrez probablement gérer vous-même les échanges d’octets avant de transmettre des données à l’objet archive, à l’aide des routines de conversion Windows Sockets **ntohs**, **ntohl**, **htons** et **htonl**. Un exemple de ces fonctions utilisées dans la communication avec une application non-MFC apparaît plus loin dans cet article.

> [!NOTE]
> Lorsque l’autre terminaison de la communication n’est pas une application MFC, vous devez également éviter de diffuser en continu les objets C++ dérivés de `CObject` dans votre archive, car le destinataire ne pourra pas les gérer. Consultez la remarque dans [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md).

Pour plus d’informations sur les commandes d’octet, consultez la spécification Windows Sockets, disponible dans le SDK Windows.

## <a name="a-byte-order-conversion-example"></a>Exemple de conversion Byte-Order

L’exemple suivant montre une fonction de sérialisation pour un `CSocket` objet qui utilise une archive. Il illustre également l’utilisation des fonctions de conversion de l’ordre des octets dans l’API Windows Sockets.

Cet exemple présente un scénario dans lequel vous écrivez un client qui communique avec une application de serveur non MFC pour laquelle vous n’avez pas accès au code source. Dans ce scénario, vous devez supposer que le serveur non-MFC utilise l’ordre d’octet du réseau standard. En revanche, votre application cliente MFC utilise un `CArchive` objet avec un `CSocket` objet et `CArchive` utilise l’ordre d’octet « Little endian », l’inverse de la norme réseau.

Supposons que le serveur non-MFC avec lequel vous envisagez de communiquer dispose d’un protocole établi pour un paquet de message similaire à ce qui suit :

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

Dans les termes MFC, cela est exprimé comme suit :

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

En C++, a **`struct`** est essentiellement la même chose qu’une classe. La `Message` structure peut avoir des fonctions membres, telles que la `Serialize` fonction membre déclarée ci-dessus. La `Serialize` fonction membre peut se présenter comme suit :

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

Cet exemple appelle les conversions de données d’ordre d’octet en raison d’une incompatibilité claire entre l’ordonnancement des octets de l’application serveur non MFC sur une terminaison et le `CArchive` utilisé dans votre application cliente MFC à l’autre extrémité. L’exemple illustre plusieurs fonctions de conversion d’ordre d’octet fournies par Windows Sockets. Le tableau suivant décrit ces fonctions.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Fonctions de conversion de Windows Sockets Byte-Order

|Fonction|Objectif|
|--------------|-------------|
|**ntohs**|Convertit une quantité de 16 bits de l’ordre d’octet réseau en ordre d’octet hôte (Big-endian à Little endian).|
|**ntohl**|Convertit une quantité 32 bits de l’ordre d’octet réseau en ordre d’octet hôte (Big-endian à Little endian).|
|**Htons**|Convertit une quantité de 16 bits de l’ordre d’octet de l’hôte en ordre d’octet réseau (Little endian à Big endian).|
|**Htonl**|Convertit une quantité 32 bits de l’ordre d’octet de l’hôte en ordre d’octet réseau (Little endian à Big-endian).|

Un autre point de cet exemple est que lorsque l’application de socket à l’autre extrémité de la communication est une application non-MFC, vous devez éviter de procéder comme suit :

`ar << pMsg;`

où `pMsg` est un pointeur vers un objet C++ dérivé de la classe `CObject` . Cela enverra des informations MFC supplémentaires associées aux objets et le serveur ne le comprendra pas, comme s’il s’agissait d’une application MFC.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : Présentation](../mfc/windows-sockets-background.md)

- [Windows Sockets : Sockets de flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagrammes](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
