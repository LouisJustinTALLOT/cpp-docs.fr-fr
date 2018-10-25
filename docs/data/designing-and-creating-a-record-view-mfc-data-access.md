---
title: Conception et création d’une vue d’enregistrement (accès de données MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- designing forms
- record views, creating
- forms [C++], designing
- record views, designing
- application wizards [C++], creating record view classes
- designing record views
ms.assetid: 1d6f5439-754f-4b8b-a19d-841a4657827b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c03b85538a795142f5085c93df3a60f4c60481ab
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065848"
---
# <a name="designing-and-creating-a-record-view--mfc-data-access"></a>Conception et création d'une vue de l'enregistrement (Accès aux données MFC)

Vous pouvez créer votre classe de vue d’enregistrement avec le [Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md). Si vous utilisez un Assistant Application, il crée la classe de vue d'enregistrement et une ressource de modèle de boîte de dialogue pour elle (sans contrôles). Vous devez utiliser l'éditeur de boîtes de dialogue Visual C++ pour ajouter des contrôles à la ressource de modèle de boîte de dialogue. En revanche, si vous utilisez **ajouter une classe**, vous devez d’abord créer la ressource de modèle de boîte de dialogue dans la boîte de dialogue Éditeur et ensuite créer la classe de vue d’enregistrement.

#### <a name="to-create-your-record-view-with-the-mfc-application-wizard"></a>Pour créer votre vue d'enregistrement avec l'Assistant Application MFC

1. Consultez [prise en charge, Assistant Application MFC de base de données](../mfc/reference/database-support-mfc-application-wizard.md).

#### <a name="to-design-your-form"></a>Pour concevoir votre formulaire

1. Consultez [boîte de dialogue Éditeur](../windows/dialog-editor.md).

#### <a name="to-create-your-record-view-class"></a>Pour créer votre classe de vue d'enregistrement

1. Consultez [Ajout d’un consommateur ODBC MFC](../mfc/reference/adding-an-mfc-odbc-consumer.md).

Les rubriques suivantes décrivent d'autres aspects de l'utilisation des vues d'enregistrements :

- [Vues d’enregistrements : Prise en charge la Navigation dans une vue d’enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)

- [Vues d’enregistrements : À l’aide d’une vue d’enregistrement](../data/using-a-record-view-mfc-data-access.md)

- [Vues d’enregistrements : Remplissage d’une zone de liste à partir d’un Second Recordset](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Recordset (ODBC)](../data/odbc/recordset-odbc.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)