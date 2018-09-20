---
title: ID de commande | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5087c271151793169cbf7350f78750044ccead0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446970"
---
# <a name="command-ids"></a>ID de commande

Une commande est entièrement décrite par son identificateur de commande seul (codé dans le **WM_COMMAND** message). Cet ID est assigné à l’objet d’interface utilisateur qui génère la commande. En règle générale, les ID sont nommés pour la fonctionnalité de l’objet d’interface utilisateur à que sont affectées.

Par exemple, un élément Effacer tout dans le menu Edition risquent d’avoir un ID comme **ID_EDIT_CLEAR_ALL**. La bibliothèque de classes prédéfinit certains identificateurs, notamment pour les commandes que le framework gère lui-même, telles que **ID_EDIT_CLEAR_ALL** ou **ID_FILE_OPEN**. Vous allez créer des autres ID de commande vous-même.

Lorsque vous créez vos propres menus dans Visual C++ de l’éditeur de menu, il est conseillé de suivre la bibliothèque de classes de convention de dénomination comme illustré par **ID_FILE_OPEN**. [Commandes standard](../mfc/standard-commands.md) explique les commandes standards définies par la bibliothèque de classes.

## <a name="see-also"></a>Voir aussi

[Objets d’interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md)

