---
title: 'Windows Sockets : L’ordre des octets'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: ca572ad32a9a46756cacf0221d80b2953b710723
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278091"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets : L’ordre des octets

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article traite de l’ordre des octets. Les autres problèmes sont décrits dans les articles : [Windows Sockets : Blocage](../mfc/windows-sockets-blocking.md) et [Windows Sockets : Conversion de chaînes en](../mfc/windows-sockets-converting-strings.md).

Si vous utilisez ou dériver de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devez gérer ces problèmes vous-même. Si vous utilisez ou dériver de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gèrera.

## <a name="byte-ordering"></a>L’ordre des octets

Architectures d’ordinateur différentes stockent parfois les données à l’aide de primauté des octets différents. Par exemple, les ordinateurs basés sur Intel stocker des données dans l’ordre inverse des machines de Macintosh (Motorola). L’ordre d’octet Intel, appelé « little-Endian, » est également l’inverse du réseau standard « big-Endian ». Le tableau suivant décrit ces termes.

### <a name="big--and-little-endian-byte-ordering"></a>L’ordre des octets big - et Little-Endian

|L’ordre des octets|Signification|
|-------------------|-------------|
|Big-Endian|L’octet le plus significatif est à l’extrémité gauche d’un mot.|
|Little-Endian|L’octet le plus significatif est à l’extrémité droite d’un mot.|

En règle générale, vous n’avez pas à vous soucier de conversion d’ordre d’octet pour les données que vous envoyez et recevez via le réseau, mais il existe des situations dans lesquelles vous devez convertir les ordres des octets.

## <a name="when-you-must-convert-byte-orders"></a>Lorsque vous devez convertir les ordres des octets

Vous devez convertir les ordres des octets dans les situations suivantes :

- Vous transmettez des informations qui doivent être interprétées par le réseau, par opposition aux données que vous envoyez à un autre ordinateur. Par exemple, vous pouvez passer les ports et adresses, le réseau doit comprendre.

- L’application serveur avec lequel vous communiquez n’est pas une application MFC (et vous n’avez pas de code source pour celle-ci). Ce code appelle pour octets, des conversions si les deux ordinateurs ne partagent pas le même ordre d’octet.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Quand il est inutile convertir les ordres des octets

Vous pouvez éviter le travail de conversion de primauté des octets dans les situations suivantes :

- Les ordinateurs sur les deux extrémités peuvent engagez à ne pas échanger des octets, et les deux ordinateurs utilisent le même ordre d’octet.

- Le serveur avec laquelle vous communiquez est une application MFC.

- Vous avez le code source pour le serveur que vous communiquez avec, donc vous pouvez de spécifier explicitement si vous devez convertir les ordres des octets ou non.

- Vous pouvez porter le serveur à MFC. Cela est assez facile à faire, et le résultat est généralement plus petit et plus rapide de code.

Utilisation de [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devez gérer toutes les conversions d’ordre d’octet nécessaire vous-même. Windows Sockets standardise le modèle d’ordre d’octet « big-Endian » et fournit des fonctions pour effectuer des conversions entre cet ordre et d’autres. [CArchive](../mfc/reference/carchive-class.md), toutefois, que vous utilisez avec [CSocket](../mfc/reference/csocket-class.md), utilise l’ordre inverse (« little-Endian »), mais `CArchive` s’occupe des détails des conversions d’ordre d’octet pour vous. En utilisant ce classement standard dans vos applications, ou à l’aide des fonctions de conversion Windows Sockets : ordre d’octet, vous pouvez rendre votre code plus portable.

La solution idéale pour l’utilisation de sockets MFC est lorsque vous écrivez les deux extrémités de la communication : à l’aide de MFC aux deux extrémités. Si vous écrivez une application qui communique avec les applications non-MFC, tel qu’un serveur FTP, vous aurez probablement besoin gérer la permutation d’octets vous-même avant de passer des données à l’objet archive, à l’aide les routines de conversion Windows Sockets **ntohs**, **ntohl**, **htons**, et **htonl**. Un exemple de ces fonctions utilisé dans la communication avec une application non-MFC apparaît plus loin dans cet article.

> [!NOTE]
>  Lorsque l’autre extrémité de la communication n’est pas une application MFC, vous devez également éviter les objets C++ dérivés de diffusion en continu `CObject` dans votre archivage, car le destinataire ne sera pas en mesure de les gérer. Consultez la remarque dans [Windows Sockets : Utilisation de Sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md).

Pour plus d’informations sur les ordres des octets, consultez la spécification Windows Sockets, disponible dans le SDK Windows.

## <a name="a-byte-order-conversion-example"></a>Un exemple de Conversion d’ordre d’octet

L’exemple suivant montre une fonction de sérialisation pour un `CSocket` objet qui utilise une archive. Il illustre également l’utilisation des fonctions de conversion d’ordre d’octet dans l’API de Sockets Windows.

Cet exemple présente un scénario dans lequel vous écrivez un client qui communique avec une application de serveur non-MFC pour lequel vous n’avez aucun accès au code source. Dans ce scénario, vous devez supposer que le serveur non-MFC utilise l’ordre des octets réseau standard. En revanche, votre application cliente MFC utilise un `CArchive` de l’objet avec un `CSocket` objet, et `CArchive` utilise l’ordre d’octet de « little-Endian », l’inverse du réseau standard.

Supposons que le serveur non-MFC avec lequel vous souhaitez communiquer comporte un protocole établi pour un paquet de message comme suit :

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

En termes MFC, cela est exprimé comme suit :

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

En C++, un **struct** est essentiellement la même chose en tant que classe. Le `Message` structure peut avoir des fonctions membres, tels que le `Serialize` fonction membre déclarée ci-dessus. Le `Serialize` fonction membre peut ressembler à ceci :

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

Cet exemple appelle des conversions d’ordre d’octet de données, car il existe une incompatibilité claire entre l’ordre des octets de l’application de serveur non-MFC sur une extrémité et le `CArchive` utilisé dans votre application cliente MFC à l’autre extrémité. L’exemple illustre plusieurs des fonctions de conversion d’ordre d’octet qui fournit de Windows Sockets. Le tableau suivant décrit ces fonctions.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows Sockets : ordre d’octet avec les fonctions de Conversion

|Fonction|Objectif|
|--------------|-------------|
|**ntohs**|Convertir une quantité de 16 bits à partir de l’ordre d’octet du réseau à l’ordre d’octet hôte (big-Endian à little-Endian).|
|**ntohl**|Convertir une quantité 32 bits à partir de l’ordre d’octet du réseau à l’ordre d’octet hôte (big-Endian à little-Endian).|
|**Htons**|Convertir une quantité de 16 bits de l’hôte à l’ordre d’octet du réseau (little-Endian à big-Endian).|
|**Htonl**|Convertir une quantité 32 bits de l’hôte à l’ordre d’octet du réseau (little-Endian à big-Endian).|

Un autre point de cet exemple est que lorsque l’application de socket à l’autre extrémité de la communication est une application non-MFC, vous devez éviter d’effectuer ce qui suit :

`ar << pMsg;`

où `pMsg` est un pointeur vers un objet C++ dérivé de classe `CObject`. Cela envoie des informations MFC supplémentaires associées aux objets et le serveur ne comprendront pas, comme il le ferait s’il s’agissait d’une application MFC.

Pour plus d'informations, voir :

- [Windows Sockets : À l’aide de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : En arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : Sockets de Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : Sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
