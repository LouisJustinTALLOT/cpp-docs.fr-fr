---
title: Fonctionnalités des classes d'affichage des enregistrements (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 2feda8f8f446e02a5056287c656707ea038f5387
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461150"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Fonctionnalités des classes d'affichage des enregistrements (Accès aux données MFC)

Vous pouvez effectuer la programmation d’accès aux données de formulaire avec la classe [CFormView](../mfc/reference/cformview-class.md), mais [CRecordView](../mfc/reference/crecordview-class.md) est généralement une meilleure classe à dériver à partir de. Outre ses `CFormView` fonctionnalités, `CRecordView`:

- Fournit l’échange de données de boîtes de dialogue (DDX) entre les contrôles du formulaire et l’objet recordset associé.

- Gère les commandes Move First Move Next, Move Previous et Move Last pour naviguer dans les enregistrements dans l’objet recordset associé.

- Mises à jour devient l’enregistrement en cours lorsque l’utilisateur se déplace vers un autre enregistrement.

Pour plus d’informations sur la navigation, consultez [vues d’enregistrements : prise en charge la Navigation dans une vue d’enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)