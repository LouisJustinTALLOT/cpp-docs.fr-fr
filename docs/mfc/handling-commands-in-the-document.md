---
title: Gestion des commandes dans le Document | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a1e848827b46d40c1ec39f2af4788e6957932c5
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929110"
---
# <a name="handling-commands-in-the-document"></a>Gestion des commandes dans le document
Votre classe de document peut également gérer certaines commandes générées par les éléments de menu, des boutons de barre d’outils ou des touches accélérateur. Par défaut, `CDocument` gère l’enregistrement et l’enregistrer en tant que les commandes dans le menu fichier, vous utilisez la sérialisation. Autres commandes qui affectent les données peuvent également être gérées par les fonctions membres de votre document. Par exemple, dans le programme Scribble, la classe `CScribDoc` fournit un gestionnaire pour la commande Modifier Effacer tout, ce qui supprime toutes les données actuellement stockées dans le document. Documents peuvent avoir des tables des messages, mais contrairement aux vues, les documents ne peut pas traiter les messages Windows standard, uniquement **WM_COMMAND** messages, ou « commandes ».  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de documents](../mfc/using-documents.md)

