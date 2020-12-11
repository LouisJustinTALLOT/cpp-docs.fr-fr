---
description: 'En savoir plus sur : ID de commande'
title: ID de commande
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: bba3b8b342b4d2e0c9492f9d0f3100a5d8f9e7d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159984"
---
# <a name="command-ids"></a>ID de commande

Une commande est entièrement décrite par son ID de commande seul (encodé dans le message **WM_COMMAND** ). Cet ID est affecté à l’objet interface utilisateur qui génère la commande. En règle générale, les ID sont nommés pour les fonctionnalités de l’objet d’interface utilisateur auquel elles sont affectées.

Par exemple, un élément effacer tout du menu Edition peut recevoir un ID tel que **ID_EDIT_CLEAR_ALL**. La bibliothèque de classes prédéfinit certains ID, en particulier pour les commandes que le Framework gère lui-même, par exemple **ID_EDIT_CLEAR_ALL** ou **ID_FILE_OPEN**. Vous allez créer vous-même d’autres ID de commande.

Lorsque vous créez vos propres menus dans l’éditeur de menus Visual C++, il est judicieux de suivre la Convention d’affectation de noms de la bibliothèque de classes, comme illustré dans **ID_FILE_OPEN**. [Commandes standard](standard-commands.md) explique les commandes standard définies par la bibliothèque de classes.

## <a name="see-also"></a>Voir aussi

[Objets de l’interface utilisateur et ID de commande](user-interface-objects-and-command-ids.md)
