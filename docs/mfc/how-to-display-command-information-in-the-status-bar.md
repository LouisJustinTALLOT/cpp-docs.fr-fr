---
description: 'En savoir plus sur : Comment : afficher des informations de commande dans la barre d’État'
title: "Comment : afficher les informations sur les commandes dans la barre d'état"
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: 568e8d356659d5267e8c4947f2981cd6243a7056
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330224"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Comment : afficher les informations sur les commandes dans la barre d'état

Lorsque vous exécutez l’Assistant application pour créer la structure de votre application, vous pouvez prendre en charge une barre d’outils et une barre d’État. Une seule option dans l’Assistant application prend en charge les deux. Lorsqu’une barre d’État est présente, l’application fournit automatiquement des commentaires utiles lorsque l’utilisateur déplace le pointeur sur les éléments dans les menus. L’application affiche automatiquement une chaîne d’invite dans la barre d’État lorsque l’élément de menu est mis en surbrillance. Par exemple, lorsque l’utilisateur déplace le pointeur sur la commande **couper** dans le menu **Edition** , la barre d’État peut afficher « coupe la sélection et la place dans le presse-papiers » dans la zone de message de la barre d’État. L’invite permet à l’utilisateur de comprendre l’objectif de l’élément de menu. Cela fonctionne également lorsque l’utilisateur clique sur un bouton de barre d’outils.

Vous pouvez ajouter à cette aide de la barre d’État en définissant des chaînes d’invite pour les éléments de menu que vous ajoutez au programme. Pour ce faire, fournissez les chaînes d’invite lorsque vous modifiez les propriétés de l’élément de menu dans l’éditeur de menus. Les chaînes que vous définissez sont stockées dans le fichier de ressources de l’application. ils ont les mêmes ID que les commandes qu’ils expliquent.

Par défaut, l’Assistant application ajoute **AFX_IDS_IDLEMESSAGE**, l’ID d’un message standard « prêt », qui s’affiche lorsque le programme attend de nouveaux messages. Si vous spécifiez l’option aide Context-Sensitive dans l’Assistant Application, le message est remplacé par « pour obtenir de l’aide, appuyez sur F1 ».

## <a name="see-also"></a>Voir aussi

[Gestion et mappage des messages](message-handling-and-mapping.md)
