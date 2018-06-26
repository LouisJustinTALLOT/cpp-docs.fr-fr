---
title: ID de commande | Documents Microsoft
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
ms.openlocfilehash: e1e03f10199c1b582a1a8603a6ea6c93e1d55473
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931230"
---
# <a name="command-ids"></a>ID de commande
Une commande est entièrement décrite par son identificateur de commande seul (codé dans le **WM_COMMAND** message). Cet ID est attribué à l’objet d’interface utilisateur qui génère la commande. En règle générale, les ID sont nommés pour la fonctionnalité de l’objet d’interface utilisateur à qu'ils sont attribués.  
  
 Par exemple, un élément Effacer tout dans le menu Edition peut avoir un ID comme **ID_EDIT_CLEAR_ALL**. La bibliothèque de classes prédéfinit certains identificateurs, notamment pour les commandes que le framework gère elle-même, tel que **ID_EDIT_CLEAR_ALL** ou **ID_FILE_OPEN**. Vous allez créer vous-même autres ID de commande.  
  
 Lorsque vous créez vos propres menus dans Visual C++ de l’éditeur de menu, il est conseillé de suivre la bibliothèque de classes de convention de dénomination comme illustré par **ID_FILE_OPEN**. [Commandes standard](../mfc/standard-commands.md) explique les commandes standard définis par la bibliothèque de classes.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets d’interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md)

