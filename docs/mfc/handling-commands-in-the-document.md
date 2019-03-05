---
title: Gestion des commandes dans le document
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: f3cce539d52bd04e97a6b5f84cbd833b05afb5bb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280431"
---
# <a name="handling-commands-in-the-document"></a>Gestion des commandes dans le document

Votre classe de document peut également gérer certaines commandes générées par les éléments de menu, des boutons de barre d’outils ou des touches accélérateur. Par défaut, `CDocument` gère l’enregistrement et l’enregistrer en tant que commandes dans le menu fichier, à l’aide de sérialisation. Autres commandes qui affectent les données peuvent également être gérées par les fonctions membres de votre document. Par exemple, dans le programme Scribble, la classe `CScribDoc` fournit un gestionnaire pour la commande Modifier Effacer tout, ce qui supprime toutes les données actuellement stockées dans le document. Documents peuvent avoir des mappages de message, mais contrairement aux vues, les documents ne peut pas traiter les messages Windows standard — uniquement **WM_COMMAND** messages, ou « commandes ».

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](../mfc/using-documents.md)
