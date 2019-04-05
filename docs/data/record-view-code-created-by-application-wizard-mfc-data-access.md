---
title: Code de vue de l'enregistrement créé par l'Assistant Application (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [C++], record view code
- record views, refreshing controls
- record views, application wizard code
ms.assetid: 18fd4703-5939-491d-b759-985f767b951f
ms.openlocfilehash: e25ca9cad1390dd11ab7328ffefed31badf6fc0b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036073"
---
# <a name="record-view-code-created-by-application-wizard--mfc-data-access"></a>Code de vue de l'enregistrement créé par l'Assistant Application (Accès aux données MFC)

Le [Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md) remplace la vue `OnInitialUpdate` et `OnGetRecordset` fonctions membres. Une fois que l'infrastructure a créé la fenêtre frame, le document et la vue, elle appelle `OnInitialUpdate` pour initialiser la vue. `OnInitialUpdate` Obtient un pointeur vers le recordset à partir du document. Un appel à la classe de base [CView::OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) fonction ouvre le jeu d’enregistrements. Le code suivant illustre ce processus pour une `CRecordView`:

```cpp
void CSectionForm::OnInitialUpdate()
{
   m_pSet = &GetDocument()->m_sectionSet;
   CRecordView::OnInitialUpdate();
}
```

Quand le recordset s'ouvre, il sélectionne des enregistrements. [CRecordset::Open](../mfc/reference/crecordset-class.md#open) fait du premier enregistrement l’enregistrement actif et DDX déplace les données à partir des membres de données de champ du jeu d’enregistrements correspondant dans l’affichage des contrôles de formulaire. Pour plus d’informations sur RFX, consultez [Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md). Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le processus de création de document/vue, consultez [utilisation des Classes pour écrire des Applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

> [!NOTE]
>  Vous devez laisser à vos utilisateurs finaux la possibilité d'actualiser les contrôles de vue d'enregistrement à partir du recordset. Sans cette fonctionnalité, si un utilisateur affecte à un contrôle une valeur non valide, il risque de rester de manière permanente sur l'enregistrement actif. Pour actualiser les contrôles, vous appelez le `CWnd` fonction membre [UpdateData](../mfc/reference/cwnd-class.md#updatedata) avec un paramètre false.

## <a name="see-also"></a>Voir aussi

[Utilisation d'une vue de l'enregistrement](../data/using-a-record-view-mfc-data-access.md)