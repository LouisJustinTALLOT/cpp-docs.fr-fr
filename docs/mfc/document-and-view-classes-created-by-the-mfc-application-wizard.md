---
description: 'En savoir plus sur : classes de document et de vue créées par l’Assistant Application MFC'
title: Classes de document et de vue créées par l'Assistant Application MFC
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: f182278ebdd971364e3e35e15e51b6ea5e7aaf68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330318"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Classes de document et de vue créées par l'Assistant Application MFC

L’Assistant Application MFC vous permet de commencer à développer votre programme en créant des classes de vue et de document squelettiques pour vous. Vous pouvez ensuite [mapper des commandes et des messages à ces classes](reference/mapping-messages-to-functions.md) et utiliser l’éditeur de code source Visual C++ pour écrire leurs fonctions membres.

La classe de document créée par l’Assistant Application MFC est dérivée de la classe [CDocument](reference/cdocument-class.md). La classe de vue est dérivée de [CView](reference/cview-class.md). Les noms que l’Assistant application fournit à ces classes et les fichiers qui les contiennent sont basés sur le nom de projet que vous fournissez dans la boîte de dialogue Assistant Application. Dans l’Assistant Application, vous pouvez utiliser la page classes générées pour modifier les noms par défaut.

Certaines applications peuvent nécessiter plusieurs classes de document, vue ou classe de fenêtre frame. Pour plus d’informations, consultez [plusieurs types de documents, vues et fenêtres Frame](multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](document-view-architecture.md)
