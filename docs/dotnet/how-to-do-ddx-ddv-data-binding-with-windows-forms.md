---
title: 'Comment : Ne DDX-DDV Data Binding with Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 31629a4db2559112ba49f5c069b08de7abdfc2db
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754349"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Comment : établir la liaison des données DDX/DDV avec Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) appelle [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) pour créer un contrôle correspondant à l’ID de contrôle des ressources. Si vous `DDX_ManagedControl` utilisez `CWinFormsControl` pour un contrôle (dans le `CreateManagedControl` code généré par l’assistant), vous ne devez pas appeler explicitement pour le même contrôle.

Appelez `DDX_ManagedControl` [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) pour créer des contrôles à partir de ressources ID. Pour l’échange de données, vous n’avez pas besoin d’utiliser les fonctions DDX/DDV avec les commandes Windows Forms. Au lieu de cela, vous pouvez placer du `DoDataExchange` code pour accéder aux propriétés du contrôle géré dans la méthode de votre classe de dialogue (ou de vue), comme dans l’exemple suivant.

L’exemple suivant montre comment lier une chaîne C 'native à un contrôle de l’utilisateur .NET.

## <a name="example"></a>Exemple

Ce qui suit est un exemple de liaison de données `m_str` DDX/DDV d’une chaîne MFC avec la propriété définie par `NameText` l’utilisateur d’un contrôle utilisateur .NET.

Le contrôle est créé lorsque [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) appelle `CMyDlg::DoDataExchange` pour la `m_UserControl` première fois, de sorte que tout code que les références doivent venir après l’appel. `DDX_ManagedControl`

Vous pouvez implémenter ce code dans l’application MFC01 que vous avez créée dans [Comment : Créer le contrôle et l’hôte de l’utilisateur dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

Mettez le code suivant dans la déclaration de CMFC01Dlg:

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>Exemple

Mettez le code suivant dans la mise en œuvre de CMFC01Dlg:

```cpp
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
{
   CDialog::DoDataExchange(pDX);
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);

   if (pDX->m_bSaveAndValidate) {
      m_str = m_MyControl->textBox1->Text;
   } else
   {
      m_MyControl->textBox1->Text = gcnew System::String(m_str);
   }
}
```

## <a name="example"></a>Exemple

Maintenant, nous allons ajouter la méthode de gestionnaire pour un clic sur le bouton OK. Cliquez sur l’onglet **Vue sur les ressources.** Dans Resource View, double `IDD_MFC01_DIALOG`clic sur . La ressource de dialogue apparaît dans Resource Editor. Ensuite, doublez cliquez sur le bouton OK.

Définissez le gestionnaire comme suit.

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>Exemple

Et ajouter la ligne suivante à la mise en œuvre de BOOL CMFC01Dlg::OnInitDialog().

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Vous pouvez maintenant générer et exécuter l’application. Notez que tout texte dans la boîte de texte sera affiché dans une boîte de message pop-up lorsque l’application se termine.

## <a name="see-also"></a>Voir aussi

[CWinFormsControl, classe](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
