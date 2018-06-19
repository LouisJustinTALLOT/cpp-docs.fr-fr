---
title: 'Windows Sockets : Classement des octets | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18fc3f586c7fc8861bfc29dade7b62e741bb0ffc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385155"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets : classement des octets
Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article traite de l’ordre des octets. Les autres problèmes sont traités dans les articles : [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md) et [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md).  
  
 Si vous utilisez ou dériver de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devrez gérer ces problèmes vous-même. Si vous utilisez ou dériver de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gère pour vous.  
  
## <a name="byte-ordering"></a>L’ordre des octets  
 Architectures d’ordinateur différentes stockent parfois des données à l’aide de primauté des octets différents. Par exemple, les ordinateurs basés sur Intel stocker des données dans l’ordre inverse des machines de Macintosh (Motorola). L’ordre des octets Intel, appelé « little-Endian, » est également l’inverse de la commande « big-Endian » standard de réseau. Le tableau suivant explique ces termes.  
  
### <a name="big--and-little-endian-byte-ordering"></a>L’ordre des octets big - et Little-Endian  
  
|L’ordre des octets|Signification|  
|-------------------|-------------|  
|Big-Endian.|L’octet le plus significatif est à l’extrémité gauche d’un mot.|  
|Little-Endian|L’octet le plus significatif est à l’extrémité droite d’un mot.|  
  
 En règle générale, vous n’avez pas à vous soucier de conversion d’ordre d’octet pour les données que vous envoyez et recevez via le réseau, mais il existe des situations dans lesquelles vous devez convertir les ordres des octets.  
  
## <a name="when-you-must-convert-byte-orders"></a>Lorsque vous devez convertir les ordres des octets  
 Vous devez convertir les ordres des octets dans les situations suivantes :  
  
-   Vous transmettez des informations qui doivent être interprétées par le réseau, par opposition aux données que vous envoyez à un autre ordinateur. Par exemple, vous pouvez passer les ports et adresses, le réseau doit comprendre.  
  
-   L’application serveur avec lequel vous communiquez n’est pas une application MFC (et vous n’avez pas de code source pour qu’il). Cette action appelle pour octets, des conversions si les deux ordinateurs ne partagent pas le même ordre d’octet.  
  
## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Lorsque vous n’avez pas à convertir les ordres des octets  
 Vous pouvez éviter le travail de conversion de primauté des octets dans les situations suivantes :  
  
-   Les ordinateurs des deux côtés peuvent engagez à ne pas échanger des octets, et les deux ordinateurs utilisent le même ordre d’octet.  
  
-   Le serveur que vous communiquez avec est une application MFC.  
  
-   Vous avez le code source pour le serveur que vous communiquez avec, afin de savoir explicitement si vous devez convertir les ordres des octets ou non.  
  
-   Vous pouvez déplacer le serveur à MFC. Cela est assez simple, et le résultat est généralement plus petit et plus rapide de code.  
  
 Utilisation de [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devez gérer toutes les conversions nécessaires d’ordre d’octets vous-même. Windows Sockets standardise le modèle d’ordre d’octet « big-Endian » et fournit des fonctions pour convertir entre cette commande et d’autres. [CArchive](../mfc/reference/carchive-class.md), toutefois, que vous pouvez utiliser avec [CSocket](../mfc/reference/csocket-class.md), utilise l’ordre inverse (« little-Endian »), mais `CArchive` prend en charge les détails de conversions d’ordre d’octet pour vous. À l’aide de cette commande standard dans vos applications, ou à l’aide des fonctions de conversion de l’ordre des octets Windows Sockets, vous pouvez rendre votre code plus portable.  
  
 Le cas idéal pour utiliser des sockets MFC est lorsque vous écrivez les deux extrémités de la communication : utilisation de MFC aux deux extrémités. Si vous écrivez une application qui communique avec les applications non-MFC, tel qu’un serveur FTP, vous aurez probablement besoin gérer la permutation d’octets vous-même avant de passer des données à l’objet de l’archive, à l’aide des routines de conversion Windows Sockets **ntohs**, **ntohl**, **htons**, et **htonl**. Un exemple de ces fonctions sont utilisées lors de la communication avec une application non-MFC apparaît plus loin dans cet article.  
  
> [!NOTE]
>  Lorsque l’autre extrémité de la communication n’est pas une application MFC, vous devez également éviter les objets C++ dérivés de diffusion en continu `CObject` à votre archivage, car le destinataire ne sera pas en mesure de les gérer. Consultez la note de [Windows Sockets : utilisation de Sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md).  
  
 Pour plus d’informations sur les ordres des octets, consultez la spécification Windows Sockets, disponible dans le SDK Windows.  
  
## <a name="a-byte-order-conversion-example"></a>Un exemple de Conversion d’ordre d’octet  
 L’exemple suivant illustre une fonction de sérialisation pour un `CSocket` objet qui utilise une archive. Il illustre également à l’aide des fonctions de conversion de l’ordre des octets dans l’API Windows Sockets.  
  
 Cet exemple présente un scénario dans lequel vous écrivez un client qui communique avec une application de serveur non-MFC pour lequel vous ne disposez d’aucun accès au code source. Dans ce scénario, vous devez supposer que le serveur non-MFC utilise l’ordre d’octets réseau standard. En revanche, votre application cliente MFC utilise un `CArchive` de l’objet avec un `CSocket` objet, et `CArchive` utilise l’ordre d’octet « little-Endian », l’inverse du réseau standard.  
  
 Supposons que le serveur non MFC avec lequel vous souhaitez communiquer comporte un protocole établi pour un paquet de message comme suit :  
  
 [!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]  
  
 En termes MFC, cela est exprimé comme suit :  
  
 [!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]  
  
 En C++, un `struct` est essentiellement la même chose en tant que classe. Le `Message` structure peut avoir des fonctions membres, tels que le `Serialize` fonction membre déclarée ci-dessus. Le `Serialize` fonction membre peut ressembler à ceci :  
  
 [!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]  
  
 Cet exemple appelle des conversions de l’ordre des octets de données, car il existe une incompatibilité claire entre l’ordre des octets de l’application de serveur non-MFC à une extrémité et le `CArchive` utilisé dans votre application cliente MFC sur l’autre extrémité. L’exemple illustre plusieurs des fonctions de conversion de l’ordre des octets par Windows Sockets. Le tableau suivant décrit ces fonctions.  
  
### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows Sockets, fonctions de Conversion d’ordre d’octet  
  
|Fonction|Objectif|  
|--------------|-------------|  
|**ntohs**|Convertir une quantité de 16 bits à partir de l’ordre d’octet du réseau à l’ordre d’octet hôte (big-Endian à little-Endian).|  
|**ntohl**|Convertir une quantité 32 bits à partir de l’ordre d’octet du réseau à l’ordre d’octet hôte (big-Endian à little-Endian).|  
|**Htons**|Convertir une quantité de 16 bits à partir de l’hôte à l’ordre d’octet du réseau (little-Endian à big-Endian).|  
|**Htonl**|Convertir une quantité 32 bits à partir de l’hôte à l’ordre d’octet du réseau (little-Endian à big-Endian).|  
  
 Un autre point de cet exemple est que lorsque l’application de socket à l’autre extrémité de la communication est une application non-MFC, vous devez éviter d’effectuer ce qui suit :  
  
 `ar << pMsg;`  
  
 où `pMsg` est un pointeur vers un objet C++ dérivé de classe `CObject`. Cette commande envoie des informations MFC supplémentaires associées aux objets et le serveur ne comprendra pas, comme il le ferait s’il s’agissait d’une application MFC.  
  
 Pour plus d'informations, voir :  
  
-   [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

