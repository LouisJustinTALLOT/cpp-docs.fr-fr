---
title: Classes de document et de vue créées par l'Assistant Application MFC
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: 766fe4efb37c199c5babb75ce2cb08ebf676cca6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616052"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>Classes de document et de vue créées par l'Assistant Application MFC

L’Assistant Application MFC vous permet de commencer à développer votre programme en créant des classes de vue et de document squelettiques pour vous. Vous pouvez ensuite [mapper des commandes et des messages à ces classes](reference/mapping-messages-to-functions.md) et utiliser l’éditeur de code source Visual C++ pour écrire leurs fonctions membres.

La classe de document créée par l’Assistant Application MFC est dérivée de la classe [CDocument](reference/cdocument-class.md). La classe de vue est dérivée de [CView](reference/cview-class.md). Les noms que l’Assistant application fournit à ces classes et les fichiers qui les contiennent sont basés sur le nom de projet que vous fournissez dans la boîte de dialogue Assistant Application. Dans l’Assistant Application, vous pouvez utiliser la page classes générées pour modifier les noms par défaut.

Certaines applications peuvent nécessiter plusieurs classes de document, vue ou classe de fenêtre frame. Pour plus d’informations, consultez [plusieurs types de documents, vues et fenêtres Frame](multiple-document-types-views-and-frame-windows.md).

## <a name="see-also"></a>Voir aussi

[Architecture document/vue](document-view-architecture.md)
