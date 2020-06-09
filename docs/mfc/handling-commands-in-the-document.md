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
ms.openlocfilehash: ed2ef635437408cacfd600d6cdba4b3731d575b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625742"
---
# <a name="handling-commands-in-the-document"></a>Gestion des commandes dans le document

Votre classe de document peut également gérer certaines commandes générées par les éléments de menu, les boutons de barre d’outils ou les touches d’accès rapide. Par défaut, `CDocument` gère les commandes enregistrer et enregistrer sous dans le menu fichier, à l’aide de la sérialisation. D’autres commandes qui affectent les données peuvent également être gérées par les fonctions membres de votre document. Par exemple, dans le programme Scribble, la classe `CScribDoc` fournit un gestionnaire pour la commande Edit Clear All, qui supprime toutes les données actuellement stockées dans le document. Les documents peuvent avoir des tables de messages, mais contrairement aux affichages, les documents ne peuvent pas gérer les messages Windows standard (uniquement **WM_COMMAND** des messages ou des « commandes »).

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](using-documents.md)
