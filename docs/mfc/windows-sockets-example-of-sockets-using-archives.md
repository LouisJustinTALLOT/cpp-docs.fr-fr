---
title: 'Windows Sockets : Exemple de Sockets utilisant des Archives'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 4ea1e2911b156066360da09993fa7302db79f12b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305292"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets : Exemple de Sockets utilisant des Archives

Cet article présente un exemple d’utilisation de classe [CSocket](../mfc/reference/csocket-class.md). L’exemple emploie `CArchive` objets à sérialiser des données via le socket. Notez qu’il ne s’agit pas de sérialisation de documents vers ou à partir d’un fichier.

L’exemple suivant illustre comment vous utiliser l’archive pour envoyer et recevoir des données via `CSocket` objets. L’exemple est conçu afin que les deux instances de l’application (sur le même ordinateur ou sur des ordinateurs différents sur le réseau) échangent des données. Une seule instance envoie les données et l’autre instance reçoit et accuse réception. L’application peut initier un échange, et soit peut agir comme serveur ou client à l’autre application. La fonction suivante est définie dans la classe d’affichage de l’application :

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

La chose la plus importante à propos de cet exemple est que sa structure correspond à une MFC `Serialize` (fonction). Le `PacketSerialize` fonction membre se compose d’un **si** instruction avec un **else** clause. La fonction reçoit deux [CArchive](../mfc/reference/carchive-class.md) références en tant que paramètres : *arData* et *arAck*. Si le *arData* objet archive est défini pour le stockage (envoi), le **si** branche s’exécute ; sinon, si *arData* est définie pour le chargement (réception) la fonction prend le **else** branche. Pour plus d’informations sur la sérialisation dans MFC, consultez [sérialisation](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
>  Le *arAck* objet archive est supposé pour être l’opposé de *arData*. Si *arData* est pour l’envoi, *arAck* reçoit, et l’inverse est vrai.

Pour l’envoi, l’exemple de fonction effectue une itération pendant un nombre spécifié de fois, chaque fois que générer des données aléatoires à des fins de démonstration. Votre application obtient des données réelles provenant d’une source, tel qu’un fichier. Le *arData* opérateur d’insertion de l’archive (**<<**) est utilisé pour envoyer un flux de trois segments consécutifs de données :

- Un « en-tête » qui spécifie la nature des données (dans ce cas, la valeur de la *bValue* variable et le nombre de copies sera envoyé).

   Les deux éléments sont générés au hasard pour cet exemple.

- Le nombre spécifié de copies des données.

   Interne **pour** boucle envoie *bValue* le nombre de fois spécifié.

- Une chaîne appelée *strText* affichant le récepteur à son utilisateur.

Pour la réception, la fonction fonctionne de façon similaire, sauf qu’elle utilise l’opérateur d’extraction de l’archive (**>>**) pour obtenir des données à partir de l’archive. L’application de réception vérifie les données qu’il reçoit, affiche le message « Réception » final et renvoie ensuite un message indiquant « Envoyé » pour l’application émettrice à afficher.

Dans ce modèle de communication, le mot « Réception », le message envoyé le *strText* variable, étant pour l’affichage à l’autre extrémité de la communication, à l’utilisateur destinataire, il spécifie qu’un certain nombre de paquets de données ont été reçu. Le récepteur répond avec une chaîne similaire indiquant que « Envoyé », pour l’affichage sur l’écran de l’expéditeur d’origine. Réception des deux chaînes indique qu’une communication réussie s’est produite.

> [!CAUTION]
>  Si vous écrivez un programme client MFC pour communiquer avec des serveurs (non-MFC) établis, n'envoyez pas les objets C++ à l'archive. À moins que le serveur est une application MFC qui comprend les types d’objets que vous souhaitez envoyer, il ne pourrez pas recevoir ni désérialiser vos objets. Un exemple dans l’article [Windows Sockets : Classement des octets](../mfc/windows-sockets-byte-ordering.md) montre une communication de ce type.

Pour plus d’informations, consultez la spécification de Windows Sockets : **htonl**, **htons**, **ntohl**, **ntohs**. Pour plus d’informations, consultez également :

- [Windows Sockets : Dérivation à partir des classes de sockets](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets : Fonctionnement des sockets avec des archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : Arrière-plan](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)
