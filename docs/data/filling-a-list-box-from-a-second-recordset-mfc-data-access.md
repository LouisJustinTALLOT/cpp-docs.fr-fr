---
title: Remplissage d'une zone de liste à partir d'un second recordset (Accès aux données MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, filling list boxes
- list boxes, filling from second recordset
- recordsets [C++], filling list boxes or combo boxes
- CComboBox class, filling object from second rowset
- ODBC recordsets [C++], filling list boxes or combo boxes
- combo boxes [C++], filling from second recordset
- CListCtrl class, filling from second recordset
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
ms.openlocfilehash: 7963d820848704921c40d5dc95a6f6d9c766d2be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588199"
---
# <a name="filling-a-list-box-from-a-second-recordset--mfc-data-access"></a>Remplissage d'une zone de liste à partir d'un second recordset (Accès aux données MFC)

Par défaut, une vue d'enregistrement est associée à un seul objet recordset dont les champs sont mappés aux contrôles de la vue d'enregistrement. Parfois, vous souhaiterez peut-être placer un contrôle de zone de liste ou de zone de liste déroulante dans votre vue d'enregistrement et le remplir avec des valeurs issues d'un second objet recordset. L'utilisateur peut utiliser la zone de liste pour sélectionner une nouvelle catégorie d'informations à afficher dans la vue d'enregistrement. Cette rubrique explique quand et comment procéder ainsi.

> [!TIP]
>  Sachez que le remplissage d'une zone de liste déroulante ou zone de liste à partir d'une source de données peut être lente. Prenez des précautions contre les tentatives de remplissage d'un contrôle à partir d'un recordset contenant un grand nombre d'enregistrements.

Le modèle pour cette rubrique se compose d'un recordset principal qui remplit les contrôles de votre formulaire, tandis qu'un recordset secondaire remplit une zone de liste ou zone de liste déroulante. La sélection d'une chaîne dans la zone de liste fait en sorte que votre programme réinterroge le recordset principal en fonction de ce qui a été sélectionné. La procédure suivante utilise une zone de liste déroulante, mais s'applique également à une zone de liste.

#### <a name="to-fill-a-combo-box-or-list-box-from-a-second-recordset"></a>Pour remplir une zone de liste déroulante ou une zone de liste à partir d'un second recordset

1. Créer l’objet recordset ([CRecordset](../mfc/reference/crecordset-class.md).

1. Obtenir un pointeur vers le [CComboBox](../mfc/reference/ccombobox-class.md) objet pour le contrôle de zone de liste déroulante.

1. Videz la zone de liste déroulante de son contenu précédent.

1. Parcourez tous les enregistrements dans le jeu d’enregistrements, appelant [CComboBox::AddString](../mfc/reference/ccombobox-class.md#addstring) pour chaque chaîne à partir de l’enregistrement actif que vous souhaitez ajouter à la zone de liste déroulante.

1. Initialisez la sélection dans la zone de liste déroulante.

```cpp
void CSectionForm::OnInitialUpdate()
{
    // ...

    // Fill the combo box with all of the courses
    CENROLLDoc* pDoc = GetDocument();
    if (!pDoc->m_courseSet.Open())
        return;

    // ...

    m_ctlCourseList.ResetContent();
    if (pDoc->m_courseSet.IsOpen())
    {
        while (!pDoc->m_courseSet.IsEOF() )
        {
            m_ctlCourseList.AddString(
                pDoc->m_courseSet.m_CourseID);
            pDoc->m_courseSet.MoveNext();
        }
    }
    m_ctlCourseList.SetCurSel(0);
}
```

Cette fonction utilise un second recordset, `m_courseSet`, qui contient un enregistrement pour chaque cours proposé, et un contrôle `CComboBox`, `m_ctlCourseList`, qui est stocké dans la classe de vue d'enregistrement.

La fonction obtient `m_courseSet` à partir du document et l'ouvre. Ensuite, elle vide `m_ctlCourseList` et parcourt `m_courseSet`. Pour chaque enregistrement, la fonction appelle la fonction membre `AddString` de la zone de liste déroulante pour ajouter la valeur de l'ID du cours à partir de l'enregistrement. Pour finir, le code définit la sélection de la liste déroulante.

## <a name="see-also"></a>Voir aussi

[Vues d’enregistrements (Accès aux données MFC)](../data/record-views-mfc-data-access.md)<br/>
[Liste de pilotes ODBC](../data/odbc/odbc-driver-list.md)