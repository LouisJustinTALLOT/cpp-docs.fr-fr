---
description: 'En savoir plus sur : gestion des commandes dans le document'
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
ms.openlocfilehash: 4d8252cb16eee0e1c5c802e5839ec925a7879cc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248890"
---
# <a name="handling-commands-in-the-document"></a>Gestion des commandes dans le document

Votre classe de document peut également gérer certaines commandes générées par les éléments de menu, les boutons de barre d’outils ou les touches d’accès rapide. Par défaut, `CDocument` gère les commandes enregistrer et enregistrer sous dans le menu fichier, à l’aide de la sérialisation. D’autres commandes qui affectent les données peuvent également être gérées par les fonctions membres de votre document. Par exemple, dans le programme Scribble, la classe `CScribDoc` fournit un gestionnaire pour la commande Edit Clear All, qui supprime toutes les données actuellement stockées dans le document. Les documents peuvent avoir des tables de messages, mais contrairement aux affichages, les documents ne peuvent pas gérer les messages Windows standard (uniquement **WM_COMMAND** des messages ou des « commandes »).

## <a name="see-also"></a>Voir aussi

[Utilisation de documents](using-documents.md)
