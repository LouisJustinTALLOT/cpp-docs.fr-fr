---
title: Fonctionnalités d’enregistrement affichage de Classes (MFC Data Access) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b6717c0ef1167e01df2f5e8de14408b23a9dbb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089570"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Fonctionnalités des classes d'affichage des enregistrements (Accès aux données MFC)
Vous pouvez effectuer la programmation d’accès aux données de formulaire à la classe [CFormView](../mfc/reference/cformview-class.md), mais [CRecordView](../mfc/reference/crecordview-class.md) est généralement une meilleure classe dériver. En plus de son `CFormView` fonctionnalités, `CRecordView`:  
  
-   Fournit l’échange de données de boîtes de dialogue (DDX) entre les contrôles du formulaire et l’objet recordset associé.  
  
-   Gère les commandes Move First, Move Next, Move Previous et Move Last pour parcourir les enregistrements dans l’objet recordset associé.  
  
-   Mises à jour devient l’enregistrement actif lorsque l’utilisateur se déplace vers un autre enregistrement.  
  
 Pour plus d’informations sur la navigation, consultez [vues des enregistrements : prise en charge la Navigation dans une vue d’enregistrement](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vues des enregistrements (MFC Data Access)](../data/record-views-mfc-data-access.md)   
 [Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)