---
title: 'Windows Sockets : exemple de sockets utilisant des archives'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 253a65430ae230fbc4deeb9bd5288f28237310d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371086"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets : exemple de sockets utilisant des archives

Cet article présente un exemple d’utilisation de la classe [CSocket](../mfc/reference/csocket-class.md). L’exemple `CArchive` utilise des objets pour sérialiser des données à travers une prise. Notez qu’il ne s’agit pas d’une sérialisation documentaire à l’adresse d’un fichier ou à partir d’un fichier.

L’exemple suivant illustre comment vous utilisez l’archive pour envoyer et recevoir des données via des `CSocket` objets. L’exemple est conçu de sorte que deux instances de l’application (sur la même machine ou sur différentes machines sur le réseau) échangent des données. Une instance envoie des données que l’autre instance reçoit et reconnaît. L’une ou l’autre application peut initier un échange, et soit peut agir comme serveur ou en tant que client de l’autre application. La fonction suivante est définie dans la classe de vue de l’application :

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

La chose la plus importante à propos de cet `Serialize` exemple est que sa structure est parallèle à celle d’une fonction MFC. La `PacketSerialize` fonction membre se compose d’une déclaration **de si** avec une **autre** clause. La fonction reçoit deux références [CArchive](../mfc/reference/carchive-class.md) comme paramètres: *arData* et *arAck*. Si l’objet d’archivage *arData* est défini pour le stockage (envoi), la branche **si** s’exécute; autrement, si *arData* est réglé pour le chargement (recevoir) la fonction prend la **branche d’autre.** Pour plus d’informations sur la sérialisation dans MFC, voir [Serialization](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
> L’objet d’archives *arAck* est supposé être le contraire *d’arData*. Si *arData* est pour l’envoi, *arAck* reçoit, et l’inverse est vrai.

Pour l’envoi, l’exemple fonctionne des boucles pour un nombre spécifié de fois, chaque fois générer des données aléatoires à des fins de démonstration. Votre demande obtiendrait des données réelles de quelque source, comme un fichier. L’opérateur d’insertion de**<<** l’archive *arData* ( ) est utilisé pour envoyer un flux de trois morceaux consécutifs de données :

- Un « en-tête » qui précise la nature des données (dans ce cas, la valeur de la variable *bValue* et le nombre d’exemplaires seront envoyés).

   Les deux éléments sont générés au hasard pour cet exemple.

- Le nombre spécifié de copies des données.

   L’intérieur **pour** la boucle envoie *bValue* le nombre spécifié de fois.

- Une chaîne appelée *strText* que le récepteur affiche à son utilisateur.

Pour la réception, la fonction fonctionne de la même**>>** façon, sauf qu’elle utilise l’opérateur d’extraction de l’archive ( ) pour obtenir des données de l’archive. L’application de réception vérifie les données qu’elle reçoit, affiche le message final "Reçu", puis renvoie un message qui dit "Envoyé" pour l’application d’envoi à afficher.

Dans ce modèle de communication, le mot "Reçu", le message envoyé dans la variable *strText,* est pour l’affichage à l’autre extrémité de la communication, de sorte qu’il spécifie à l’utilisateur récepteur qu’un certain nombre de paquets de données ont été reçus. Le récepteur répond avec une chaîne similaire qui dit "Sent", pour l’affichage sur l’écran de l’expéditeur d’origine. La réception des deux chaînes indique qu’une communication réussie a eu lieu.

> [!CAUTION]
> Si vous écrivez un programme client MFC pour communiquer avec des serveurs (non-MFC) établis, n'envoyez pas les objets C++ à l'archive. Sauf si le serveur est une application MFC qui comprend les types d’objets que vous souhaitez envoyer, il ne sera pas en mesure de recevoir et de déséialiser vos objets. Un exemple dans l’article [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) montre une communication de ce type.

Pour plus d’informations, voir Windows Sockets Specification: **htonl**, **htons**, **ntohl**, **ntohs**. Aussi, pour plus d’informations, voir:

- [Windows Sockets : dérivation à partir des classes de sockets](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets : fonctionnement des sockets avec des archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::opérateur <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::opérateur >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)
