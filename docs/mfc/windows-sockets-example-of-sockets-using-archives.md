---
title: "Windows Sockets : Exemple de Sockets utilisant des Archives | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0e70e8ecc14496b03bc758d91f078a926f33532
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets : exemple de sockets utilisant des archives
Cet article présente un exemple de classe [CSocket](../mfc/reference/csocket-class.md). L’exemple emploie `CArchive` objets à sérialiser des données via un socket. Notez qu’il ne s’agit pas de sérialisation des documents vers ou à partir d’un fichier.  
  
 L’exemple suivant illustre comment vous utilisez l’archive pour envoyer et recevoir des données via `CSocket` objets. L’exemple est conçu pour que les deux instances de l’application (sur le même ordinateur ou sur différents ordinateurs sur le réseau) échangent des données. Une seule instance envoie les données et l’autre instance reçoit et accuse réception. L’application peut déclencher un échange, et soit peut agir comme serveur ou client à l’autre application. La fonction suivante est définie dans la classe de vue de l’application :  
  
 [!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]  
  
 Le plus important de cet exemple est que sa structure correspond à celle d’une MFC `Serialize` (fonction). Le **PacketSerialize** fonction membre se compose d’un **si** instruction avec un **else** clause. La fonction reçoit deux [CArchive](../mfc/reference/carchive-class.md) en tant que paramètres : `arData` et `arAck`. Si le `arData` objet archive est défini pour le stockage (envoi), la **si** branche s’exécute ; sinon, si `arData` est défini pour le chargement (réception) la fonction prend le **else** branche. Pour plus d’informations sur la sérialisation dans MFC, consultez [sérialisation](../mfc/how-to-make-a-type-safe-collection.md).  
  
> [!NOTE]
>  Le `arAck` objet archive est censé pour être l’opposé de `arData`. Si `arData` est pour l’envoi, `arAck` reçoit, et l’inverse est vrai.  
  
 Pour l’envoi, la fonction de l’exemple effectue une boucle pour un nombre spécifié de fois, chaque fois que générer des données aléatoires à des fins de démonstration. Votre application serait obtenir des données réelles provenant d’une source, telle qu’un fichier. Le `arData` opérateur d’insertion de l’archive (**<<**) est utilisé pour envoyer un flux de données de trois segments consécutifs de données :  
  
-   Un « en-tête » qui spécifie la nature des données (dans ce cas, la valeur de la `bValue` variable et le nombre de copies est envoyé).  
  
     Les deux éléments sont générés au hasard pour cet exemple.  
  
-   Le nombre spécifié de copies des données.  
  
     Interne **pour** boucle envoie `bValue` le nombre de fois spécifié.  
  
-   Une chaîne appelée `strText` que le récepteur affiche à son utilisateur.  
  
 Pour la réception, la fonction opère de la même façon, sauf qu’elle utilise l’opérateur d’extraction de l’archive (**>>**) pour obtenir des données à partir de l’archive. L’application de réception vérifie les données qu’elle reçoit, affiche le message « Réception » final et puis envoie un message indiquant que « Envoi » pour l’application émettrice à afficher.  
  
 Dans ce modèle de communication, le mot « Reçu », le message envoyé le `strText` variable est pour l’affichage à l’autre extrémité de la communication, ce afin d’indiquer à l’utilisateur destinataire qu’un certain nombre de paquets de données ont été reçus. Le récepteur répond avec une chaîne semblable qui indique « Envoi » pour l’affichage sur l’écran de l’expéditeur d’origine. Réception des deux chaînes indique que la communication réussie s’est produite.  
  
> [!CAUTION]
>  Si vous écrivez un programme client MFC pour communiquer avec des serveurs (non-MFC) établis, n'envoyez pas les objets C++ à l'archive. À moins que le serveur est une application MFC qui comprend les types d’objets que vous souhaitez envoyer, il ne pourra plus être recevoir ni désérialiser vos objets. Un exemple dans l’article [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md) montre une communication de ce type.  
  
 Pour plus d’informations, consultez la spécification Windows Sockets : **htonl**, **htons**, **ntohl**, **ntohs**. En outre, pour plus d’informations, consultez :  
  
-   [Windows Sockets : dérivation à partir des classes de sockets](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets : fonctionnement des sockets avec des archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)   
 [CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::Flush](../mfc/reference/carchive-class.md#flush)   
 [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)

