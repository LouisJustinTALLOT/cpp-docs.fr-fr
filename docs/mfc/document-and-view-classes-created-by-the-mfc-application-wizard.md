---
title: Documenter et afficher les Classes créées par l’Assistant Application MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb1a1fc6c35bfb9589e827d798cb112640fa9b2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417616"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Classes de document et de vue créées par l'Assistant Application MFC

L’Assistant Application MFC vous donne une longueur d’avance sur le développement de votre programme en créant des documents squelette et classes d’affichage pour vous. Vous pouvez ensuite [mapper les commandes et les messages à ces classes](../mfc/reference/mapping-messages-to-functions.md) et utiliser l’éditeur de code source Visual C++ pour écrire leurs fonctions membres.

La classe de document créée par l’Assistant Application MFC est dérivée de la classe [CDocument](../mfc/reference/cdocument-class.md). La classe d’affichage est dérivée [CView](../mfc/reference/cview-class.md). Les noms que l’Assistant Application propose ces classes et les fichiers qui contiennent les sont basées sur le nom du projet que vous indiquez dans la boîte de dialogue Assistant Création d’applications. Dans l’Assistant Application, vous pouvez utiliser la page Classes générées pour modifier les noms par défaut.

Certaines applications peut-être plusieurs classes de document, classe d’affichage ou classe de fenêtre frame. Pour plus d’informations, consultez [plusieurs Types de documents, vues et Frame Windows](../mfc/multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](../mfc/document-view-architecture.md)

