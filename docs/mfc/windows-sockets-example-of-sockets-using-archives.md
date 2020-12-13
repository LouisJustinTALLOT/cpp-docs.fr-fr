---
description: 'En savoir plus sur : Windows Sockets : exemple de sockets utilisant des Archives'
title: 'Windows Sockets : exemple de sockets utilisant des archives'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 726df9093f71a7c72fc72794044a417c5425d2a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132924"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets : exemple de sockets utilisant des archives

Cet article présente un exemple d’utilisation de la classe [CSocket](../mfc/reference/csocket-class.md). L’exemple utilise des `CArchive` objets pour sérialiser des données via un Socket. Notez qu’il ne s’agit pas de documenter la sérialisation vers ou à partir d’un fichier.

L’exemple suivant illustre la façon dont vous utilisez l’Archive pour envoyer et recevoir des données par le biais d' `CSocket` objets. L’exemple est conçu de sorte que deux instances de l’application (sur le même ordinateur ou sur des ordinateurs différents sur le réseau) échangent des données. Une instance envoie des données que l’autre instance reçoit et accuse réception. L’une des applications peut lancer un échange et peut agir en tant que serveur ou client pour l’autre application. La fonction suivante est définie dans la classe d’affichage de l’application :

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

L’élément le plus important de cet exemple est que sa structure est parallèle à celle d’une `Serialize` fonction MFC. La `PacketSerialize` fonction membre se compose d’une **`if`** instruction avec une **`else`** clause. La fonction reçoit deux références [CArchive](../mfc/reference/carchive-class.md) comme paramètres : *arData* et *arAck*. Si l’objet Archive *arData* est défini pour le stockage (envoi), la **`if`** branche s’exécute ; sinon, si *arData* est défini pour le chargement (réception), la fonction prend la **`else`** branche. Pour plus d’informations sur la sérialisation dans MFC, consultez [sérialisation](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
> L’objet Archive *arAck* est supposé être l’opposé de *arData*. Si *arData* est pour l’envoi, *arAck* reçoit et la réciproque est true.

Pour l’envoi, l’exemple de fonction effectue une boucle pendant un nombre de fois donné, à chaque fois que des données aléatoires sont générées à des fins de démonstration. Votre application obtient des données réelles à partir d’une source, telle qu’un fichier. L’opérateur d’insertion de l’archive *arData* ( **<<** ) est utilisé pour envoyer un flux de trois blocs de données consécutifs :

- Un « en-tête » qui spécifie la nature des données (dans ce cas, la valeur de la variable *bValue* et le nombre de copies qui seront envoyées).

   Les deux éléments sont générés de manière aléatoire pour cet exemple.

- Nombre spécifié de copies des données.

   La **`for`** boucle interne envoie *bValue* le nombre de fois spécifié.

- Chaîne appelée *strText* que le destinataire affiche à son utilisateur.

Pour la réception, la fonction fonctionne de la même manière, à ceci près qu’elle utilise l’opérateur d’extraction () de l’archive **>>** pour obtenir des données à partir de l’archive. L’application réceptrice vérifie les données qu’elle reçoit, affiche le message final « reçu », puis renvoie un message indiquant « envoyé » pour l’affichage de l’application émettrice.

Dans ce modèle de communication, le mot « received » (reçu), le message envoyé dans la variable *strText* , est destiné à être affiché à l’autre extrémité de la communication. il indique donc à l’utilisateur destinataire qu’un certain nombre de paquets de données ont été reçus. Le récepteur répond avec une chaîne similaire qui indique « envoyé », pour l’afficher sur l’écran de l’expéditeur d’origine. La réception des deux chaînes indique qu’une communication réussie s’est produite.

> [!CAUTION]
> Si vous écrivez un programme client MFC pour communiquer avec des serveurs (non-MFC) établis, n'envoyez pas les objets C++ à l'archive. À moins que le serveur ne soit une application MFC qui comprenne les types d’objets que vous souhaitez envoyer, il ne peut pas recevoir et désérialiser vos objets. Un exemple de l’article [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md) affiche une communication de ce type.

Pour plus d’informations, consultez Spécification Windows Sockets : **htonl**, **htons**, **ntohl**, **ntohs**. En outre, pour plus d’informations, consultez :

- [Windows Sockets : dérivation à partir des classes de Sockets](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets : fonctionnement des sockets avec les Archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : Présentation](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive :: IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive :: Operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive :: Operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive :: Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject :: Serialize](../mfc/reference/cobject-class.md#serialize)
