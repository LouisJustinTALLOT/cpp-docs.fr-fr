---
title: Fonctionnalités des classes d'affichage des enregistrements (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 5f8de956065571109c988bd2940d21822bba7cfd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029873"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Fonctionnalités des classes d'affichage des enregistrements (Accès aux données MFC)

Vous pouvez effectuer la programmation d’accès aux données de formulaire avec la classe [CFormView](../mfc/reference/cformview-class.md), mais [CRecordView](../mfc/reference/crecordview-class.md) est généralement une meilleure classe à dériver à partir de. Outre ses `CFormView` fonctionnalités, `CRecordView`:

- Fournit l’échange de données de boîtes de dialogue (DDX) entre les contrôles du formulaire et l’objet recordset associé.

- Gère les commandes Move First Move Next, Move Previous et Move Last pour naviguer dans les enregistrements dans l’objet recordset associé.

- Mises à jour devient l’enregistrement en cours lorsque l’utilisateur se déplace vers un autre enregistrement.

Pour plus d’informations sur la navigation, consultez [vues d’enregistrements : Prise en charge de la Navigation dans une vue d’enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)