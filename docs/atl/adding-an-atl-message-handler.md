---
description: 'En savoir plus sur : ajout d’un gestionnaire de messages ATL'
title: Ajout d’un gestionnaire de messages ATL
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [C++]
- ATL, windows
- message handling [C++], ATL message handler
- windows [C++], ATL
- ATL, message handlers
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
ms.openlocfilehash: 263cbcb863ee287c9b3f4650263a3fac33d7ab7b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166341"
---
# <a name="adding-an-atl-message-handler"></a>Ajout d’un gestionnaire de messages ATL

Pour ajouter un gestionnaire de messages (une fonction membre qui gère les messages Windows) à un contrôle, commencez par sélectionner le contrôle dans la Affichage de classes. Ouvrez ensuite la fenêtre **Propriétés** , sélectionnez l’icône **messages** , puis cliquez sur le contrôle de liste déroulante dans la zone en regard du message requis. Cette opération ajoute une déclaration pour le gestionnaire de messages dans le fichier d’en-tête du contrôle et une implémentation squelette du gestionnaire dans le fichier. cpp du contrôle. Elle ajoute également la table des messages et ajoute une entrée pour le gestionnaire.

L’ajout d’un gestionnaire de messages dans ATL est semblable à l’ajout d’un gestionnaire de messages à une classe MFC. Pour plus d’informations, consultez [Ajout d’un gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md) .

Les conditions suivantes s’appliquent uniquement à l’ajout d’un gestionnaire de messages ATL :

- Les gestionnaires de messages suivent la même convention d’affectation de noms que MFC.

- Les nouvelles entrées de la table des messages sont ajoutées à la table des messages principale. L’Assistant ne reconnaît pas les tables de messages de remplacement et le chaînage.

## <a name="see-also"></a>Voir aussi

[Implémentation d’une fenêtre](../atl/implementing-a-window.md)
