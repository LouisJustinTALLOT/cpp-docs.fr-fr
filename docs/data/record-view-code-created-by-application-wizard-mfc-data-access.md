---
description: 'En savoir plus sur : code de vue d’enregistrement créé par l’Assistant Application (accès aux données MFC)'
title: Code de vue de l'enregistrement créé par l'Assistant Application (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: b0fa7a4960096f11ab66194fa6e41be60b45d4c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332432"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Code de vue de l'enregistrement créé par l'Assistant Application (Accès aux données MFC)

L' [Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md) remplace les `OnInitialUpdate` fonctions membres et de la vue `OnGetRecordset` . Une fois que l'infrastructure a créé la fenêtre frame, le document et la vue, elle appelle `OnInitialUpdate` pour initialiser la vue. `OnInitialUpdate` obtient un pointeur vers le recordset à partir du document. Un appel à la fonction [CView :: OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) de la classe de base ouvre le Recordset. Le code suivant illustre ce processus pour un `CRecordView` :

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Quand le recordset s'ouvre, il sélectionne des enregistrements. [CRecordset :: Open](../mfc/reference/crecordset-class.md#open) fait du premier enregistrement l’enregistrement actif, et DDX déplace les données des membres de données de champ du recordset vers les contrôles de formulaire correspondants dans la vue. Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md). Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le processus de création de document/vue, consultez [utilisation des classes pour écrire des applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
> Vous devez laisser à vos utilisateurs finaux la possibilité d'actualiser les contrôles de vue d'enregistrement à partir du recordset. Sans cette fonctionnalité, si un utilisateur affecte à un contrôle une valeur non valide, il risque de rester de manière permanente sur l'enregistrement actif. Pour actualiser les contrôles, vous appelez la `CWnd` fonction membre [UpdateData](../mfc/reference/cwnd-class.md#updatedata) avec un paramètre ayant la valeur false.

## <a name="see-also"></a>Voir aussi

[Utilisation d'une vue de l'enregistrement](../data/using-a-record-view-mfc-data-access.md)
