---
title: Fonctionnalités des classes d'affichage des enregistrements (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 62597a3eb3f7a7e779ca57c9781565176df568d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213432"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Fonctionnalités des classes d'affichage des enregistrements (Accès aux données MFC)

Vous pouvez effectuer une programmation de l’accès aux données basée sur les formulaires avec la classe [CFormView](../mfc/reference/cformview-class.md), mais [CRecordView](../mfc/reference/crecordview-class.md) est généralement une meilleure classe à partir de laquelle dériver. En plus de ses fonctionnalités de `CFormView`, `CRecordView`:

- Permet l’échange de données de boîtes de dialogue (DDX) entre les contrôles de formulaire et l’objet Recordset associé.

- Gère les commandes déplacer en premier, déplacer suivant, déplacer vers le haut et déplacer en dernier pour naviguer dans les enregistrements de l’objet Recordset associé.

- Met à jour les modifications apportées à l’enregistrement actuel lorsque l’utilisateur passe à un autre enregistrement.

Pour plus d’informations sur la navigation, consultez [vues des enregistrements : prise en charge de la navigation dans une vue d’enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)
