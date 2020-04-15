---
title: 'Windows Sockets : classement des octets'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: 50548202483c4d9d4471ad2c600270c4df4503e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371073"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets : classement des octets

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article couvre la commande d’byte. Les autres questions sont abordées dans les articles: [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md) et [Windows Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Si vous utilisez ou dérivez de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous aurez besoin de gérer ces questions vous-même. Si vous utilisez ou dérivez de la classe [CSocket,](../mfc/reference/csocket-class.md)MFC les gère pour vous.

## <a name="byte-ordering"></a>Classement des octets

Différentes architectures de machine stockent parfois des données à l’aide de différentes commandes d’byte. Par exemple, les machines basées sur Intel stockent des données dans l’ordre inverse des machines Macintosh (Motorola). L’ordre d’orte Intel, appelé "petit-Endian", est également l’inverse de la norme réseau "big-Endian" ordre. Le tableau suivant explique ces termes.

### <a name="big--and-little-endian-byte-ordering"></a>Commande de fourre-tout Big- and Little-Endian

|Classement des octets|Signification|
|-------------------|-------------|
|Big-Endian|Le plus important byte est à gauche d’un mot.|
|Petit-Endian|Le plus important byte est sur la bonne extrémité d’un mot.|

En règle générale, vous n’avez pas à vous soucier de la conversion de l’ordre par les et soi pour les données que vous envoyez et recevez sur le réseau, mais il ya des situations dans lesquelles vous devez convertir les commandes byte.

## <a name="when-you-must-convert-byte-orders"></a>Lorsque vous devez convertir les ordres byte

Vous devez convertir les commandes d’byte dans les situations suivantes :

- Vous transmettez des informations qui doivent être interprétées par le réseau, par opposition aux données que vous envoyez à une autre machine. Par exemple, vous pouvez passer des ports et des adresses, que le réseau doit comprendre.

- L’application serveur avec laquelle vous communiquez n’est pas une application MFC (et vous n’avez pas de code source pour elle). Cela nécessite des conversions de commandes d’ente si les deux machines ne partagent pas la même commande d’byte.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Lorsque vous n’avez pas à convertir les ordres byte

Vous pouvez éviter le travail de conversion des commandes d’byte dans les situations suivantes :

- Les machines sur les deux extrémités peuvent convenir de ne pas échanger les octets, et les deux machines utilisent la même commande d’octets.

- Le serveur avec qui vous communiquez est une application MFC.

- Vous avez le code source pour le serveur avec qui vous communiquez, de sorte que vous pouvez dire explicitement si vous devez convertir les commandes byte ou non.

- Vous pouvez porter le serveur à MFC. C’est assez facile à faire, et le résultat est généralement plus petit, code plus rapide.

En travaillant avec [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devez gérer vous-même toutes les conversions nécessaires à l’ordre des bytes. Windows Sockets standardise le modèle de commande par les etc. et fournit des fonctions à convertir entre cet ordre et d’autres. [CArchive](../mfc/reference/carchive-class.md), cependant, que vous utilisez avec [CSocket](../mfc/reference/csocket-class.md), utilise l’ordre `CArchive` opposé ("petit-Endian"), mais prend soin des détails des conversions byte-order pour vous. En utilisant cette commande standard dans vos applications, ou en utilisant windows Sockets byte-order conversion fonctions, vous pouvez rendre votre code plus portable.

Le cas idéal pour l’utilisation des prises MFC est lorsque vous écrivez les deux extrémités de la communication: en utilisant MFC aux deux extrémités. Si vous écrivez une application qui communiquera avec des applications non-MFC, comme un serveur FTP, vous aurez probablement besoin de gérer byte-swapping vous-même avant de passer des données à l’objet d’archives, en utilisant les routines de conversion Windows **Sockets ntohs**, **ntohl**, **htons**, et **htonl**. Un exemple de ces fonctions utilisées dans la communication avec une application non-MFC apparaît plus tard dans cet article.

> [!NOTE]
> Lorsque l’autre extrémité de la communication n’est pas une application MFC, vous devez également éviter de diffuser des objets CMD dérivés de `CObject` votre archive parce que le récepteur ne sera pas en mesure de les gérer. Voir la note dans [Windows Sockets: Using Sockets with Archives](../mfc/windows-sockets-using-sockets-with-archives.md).

Pour plus d’informations sur les commandes de byte, consultez la spécification Windows Sockets, disponible dans le SDK Windows.

## <a name="a-byte-order-conversion-example"></a>Un exemple de conversion byte-Order

L’exemple suivant montre une `CSocket` fonction de sérialisation d’un objet qui utilise une archive. Il illustre également l’utilisation des fonctions de conversion de l’ordre par au fourre-tout dans l’API Windows Sockets.

Cet exemple présente un scénario dans lequel vous écrivez un client qui communique avec une application serveur non-MFC pour laquelle vous n’avez pas accès au code source. Dans ce scénario, vous devez supposer que le serveur non-MFC utilise l’ordre standard de byte réseau. En revanche, votre application client `CArchive` MFC `CSocket` utilise `CArchive` un objet avec un objet, et utilise "petit-Endian" ordre byte, le contraire de la norme réseau.

Supposons que le serveur non-MFC avec lequel vous prévoyez de communiquer a un protocole établi pour un paquet de messages comme ce qui suit:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

En termes MFC, cela serait exprimé comme suit:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

Dans le C, une **struct** est essentiellement la même chose qu’une classe. La `Message` structure peut avoir des fonctions de membre, telles que la `Serialize` fonction membre déclarée ci-dessus. La `Serialize` fonction de membre pourrait ressembler à ceci :

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

Cet exemple nécessite des conversions de données par ordre d’au revoir parce qu’il y a un décalage `CArchive` évident entre la commande de byte de l’application serveur non MFC d’une extrémité et celle utilisée dans votre application client MFC à l’autre extrémité. L’exemple illustre plusieurs des fonctions de conversion de commande d’byte que Windows Sockets fournit. Le tableau suivant décrit ces fonctions.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Fonctions de conversion Windows Sockets Byte-Order

|Fonction|Objectif|
|--------------|-------------|
|**ntohs**|Convertir une quantité de 16 bits de l’ordre de byte réseau pour héberger l’ordre byte (big-Endian à little-Endian).|
|**ntohl (ntohl)**|Convertir une quantité de 32 bits de l’ordre de byte réseau pour héberger l’ordre byte (big-Endian à little-Endian).|
|**Htons Htons**|Convertir une quantité de 16 bits de l’ordre d’hébergement byte à l’ordre de byte réseau (petit-Endian à big-Endian).|
|**Htonl Htonl**|Convertir une quantité de 32 bits de l’ordre d’hébergement byte à l’ordre de byte réseau (petit-Endian à big-Endian).|

Un autre point de cet exemple est que lorsque l’application de prise à l’autre extrémité de la communication est une application non-MFC, vous devez éviter de faire quelque chose comme ce qui suit:

`ar << pMsg;`

où `pMsg` est un pointeur à un `CObject`objet C ' dérivé de la classe . Cela enverra des informations MFC supplémentaires associées aux objets et le serveur ne le comprendra pas, comme il le ferait s’il s’agissait d’une application MFC.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
