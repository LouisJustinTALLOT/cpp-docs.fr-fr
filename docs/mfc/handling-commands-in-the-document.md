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
ms.openlocfilehash: d2f0a7271452ace9b9e06ff995af61881db4403c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548952"
---
# <a name="handling-commands-in-the-document"></a>Gestion des commandes dans le document

Votre classe de document peut également gérer certaines commandes générées par les éléments de menu, des boutons de barre d’outils ou des touches accélérateur. Par défaut, `CDocument` gère l’enregistrement et l’enregistrer en tant que commandes dans le menu fichier, à l’aide de sérialisation. Autres commandes qui affectent les données peuvent également être gérées par les fonctions membres de votre document. Par exemple, dans le programme Scribble, la classe `CScribDoc` fournit un gestionnaire pour la commande Modifier Effacer tout, ce qui supprime toutes les données actuellement stockées dans le document. Documents peuvent avoir des mappages de message, mais contrairement aux vues, les documents ne peut pas traiter les messages Windows standard — uniquement **WM_COMMAND** messages, ou « commandes ».

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](../mfc/using-documents.md)

