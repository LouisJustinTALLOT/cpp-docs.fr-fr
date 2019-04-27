---
title: Ajout d’un gestionnaire de messages ATL
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
ms.openlocfilehash: cc7631ac9e02891cee725b47133a273e756759d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223465"
---
# <a name="adding-an-atl-message-handler"></a>Ajout d’un gestionnaire de messages ATL

Pour ajouter un gestionnaire de messages (une fonction membre qui gère les messages Windows) à un contrôle, sélectionnez tout d’abord le contrôle dans l’affichage de classes. Ouvrez ensuite le **propriétés** fenêtre, sélectionnez le **Messages** icône et cliquez sur la liste déroulante contrôler dans la zone en regard du message requis. Cette opération ajoute une déclaration pour le Gestionnaire de messages dans le fichier d’en-tête du contrôle et une implémentation squelette du gestionnaire dans le fichier .cpp du contrôle. Il sera également ajouter la table des messages et ajoutez une entrée pour le gestionnaire.

Ajout d’un gestionnaire de messages dans ATL est similaire à l’ajout d’un gestionnaire de messages à une classe MFC. Consultez [Ajout d’un gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md) pour plus d’informations.

Les conditions suivantes s’appliquent uniquement à l’ajout d’un gestionnaire de messages ATL :

- Les gestionnaires de messages suivent la même convention d’affectation de noms que MFC.

- Les nouvelles entrées de mappage de message sont ajoutées dans la table des messages principale. L’Assistant ne reconnaît pas les tables des messages de remplacement et le chaînage.

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)
