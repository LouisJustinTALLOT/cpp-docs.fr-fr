---
title: Code de vue de l'enregistrement créé par l'Assistant Application (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: 69481299980329b98e378f02e090670fa3d7ece2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376018"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Code de vue de l'enregistrement créé par l'Assistant Application (Accès aux données MFC)

[L’assistant d’application MFC](../mfc/reference/database-support-mfc-application-wizard.md) remplace `OnInitialUpdate` `OnGetRecordset` les fonctions de la vue et des membres. Une fois que l'infrastructure a créé la fenêtre frame, le document et la vue, elle appelle `OnInitialUpdate` pour initialiser la vue. `OnInitialUpdate` obtient un pointeur vers le recordset à partir du document. Un appel à la classe de base [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) fonction ouvre le recordet. Le code suivant montre `CRecordView`ce processus pour un :

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Quand le recordset s'ouvre, il sélectionne des enregistrements. [CRecordset: :Open](../mfc/reference/crecordset-class.md#open) fait le premier enregistrement de l’enregistrement actuel, et DDX déplace les données des membres des données de champ du recordet aux contrôles de forme correspondants dans la vue. Pour plus d’informations sur RFX, voir [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md). Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le processus de création de documents/vue, voir [Utiliser les classes pour écrire des applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
> Vous devez laisser à vos utilisateurs finaux la possibilité d'actualiser les contrôles de vue d'enregistrement à partir du recordset. Sans cette fonctionnalité, si un utilisateur affecte à un contrôle une valeur non valide, il risque de rester de manière permanente sur l'enregistrement actif. Pour actualiser les contrôles, vous appelez la `CWnd` fonction membre [UpdateData](../mfc/reference/cwnd-class.md#updatedata) avec un paramètre de FALSE.

## <a name="see-also"></a>Voir aussi

[Utilisation d'une vue de l'enregistrement](../data/using-a-record-view-mfc-data-access.md)
