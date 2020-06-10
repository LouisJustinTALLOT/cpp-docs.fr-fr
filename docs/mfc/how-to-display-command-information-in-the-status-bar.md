---
title: "Comment : afficher les informations sur les commandes dans la barre d'état"
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: bff5d5b20ecc9b20b7b1e8335cda34d582441425
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622530"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Comment : afficher les informations sur les commandes dans la barre d'état

Lorsque vous exécutez l’Assistant application pour créer la structure de votre application, vous pouvez prendre en charge une barre d’outils et une barre d’État. Une seule option dans l’Assistant application prend en charge les deux. Lorsqu’une barre d’État est présente, l’application fournit automatiquement des commentaires utiles lorsque l’utilisateur déplace le pointeur sur les éléments dans les menus. L’application affiche automatiquement une chaîne d’invite dans la barre d’État lorsque l’élément de menu est mis en surbrillance. Par exemple, lorsque l’utilisateur déplace le pointeur sur la commande **couper** dans le menu **Edition** , la barre d’État peut afficher « coupe la sélection et la place dans le presse-papiers » dans la zone de message de la barre d’État. L’invite permet à l’utilisateur de comprendre l’objectif de l’élément de menu. Cela fonctionne également lorsque l’utilisateur clique sur un bouton de barre d’outils.

Vous pouvez ajouter à cette aide de la barre d’État en définissant des chaînes d’invite pour les éléments de menu que vous ajoutez au programme. Pour ce faire, fournissez les chaînes d’invite lorsque vous modifiez les propriétés de l’élément de menu dans l’éditeur de menus. Les chaînes que vous définissez sont stockées dans le fichier de ressources de l’application. ils ont les mêmes ID que les commandes qu’ils expliquent.

Par défaut, l’Assistant application ajoute **AFX_IDS_IDLEMESSAGE**, l’ID d’un message standard « prêt », qui s’affiche lorsque le programme attend de nouveaux messages. Si vous spécifiez l’option aide contextuelle dans l’Assistant Application, le message est remplacé par « pour obtenir de l’aide, appuyez sur F1 ».

## <a name="see-also"></a>Voir aussi

[Gestion et mappage des messages](message-handling-and-mapping.md)
