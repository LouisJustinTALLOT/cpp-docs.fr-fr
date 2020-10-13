---
title: 'Procédure : Établir la liaison des données DDX/DDV avec Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: a0759eba1c55e72f2c0a99964b0b2d254df82a25
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008311"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Comment : établir la liaison des données DDX/DDV avec Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) appelle [CWinFormsControl :: CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) pour créer un contrôle correspondant à l’ID de contrôle de ressource. Si vous utilisez `DDX_ManagedControl` pour un `CWinFormsControl` contrôle (dans du code généré par l’Assistant), vous ne devez pas appeler `CreateManagedControl` explicitement pour le même contrôle.

Appelez `DDX_ManagedControl` dans [CWnd ::D odataexchange](../mfc/reference/cwnd-class.md#dodataexchange) pour créer des contrôles à partir d’ID de ressource. Pour l’échange de données, vous n’avez pas besoin d’utiliser les fonctions DDX/DDV avec les contrôles Windows Forms. Au lieu de cela, vous pouvez placer du code pour accéder aux propriétés du contrôle managé dans la `DoDataExchange` méthode de votre classe de boîte de dialogue (ou vue), comme dans l’exemple suivant.

L’exemple suivant montre comment lier une chaîne C++ native à un contrôle utilisateur .NET.

## <a name="example-ddxddv-data-binding"></a>Exemple : liaison de données DDX/DDV

Voici un exemple de liaison de données DDX/DDV d’une chaîne MFC `m_str` avec la propriété définie par l’utilisateur `NameText` d’un contrôle utilisateur .net.

Le contrôle est créé quand [CDialog :: OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) est appelé `CMyDlg::DoDataExchange` pour la première fois, donc tout code qui fait référence à `m_UserControl` doit venir après l' `DDX_ManagedControl` appel.

Vous pouvez implémenter ce code dans l’application MFC01 que vous avez créée dans [Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

Placez le code suivant dans la déclaration de CMFC01Dlg :

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example-implement-dodataexchange"></a>Exemple : Implement DoDataExchange ()

Placez le code suivant dans l’implémentation de CMFC01Dlg :

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

## <a name="example-add-handler-method"></a>Exemple : ajouter une méthode de gestionnaire

À présent, nous allons ajouter la méthode de gestionnaire d’un clic sur le bouton OK. Cliquez sur l’onglet **affichage des ressources** . Dans Affichage des ressources, double-cliquez sur `IDD_MFC01_DIALOG` . La ressource de boîte de dialogue s’affiche dans l’éditeur de ressources. Double-cliquez sur le bouton OK..

Définissez le gestionnaire comme suit.

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example-set-the-textbox-text"></a>Exemple : définir le texte de la zone de texte

Et ajoutez la ligne suivante à l’implémentation de BOOL CMFC01Dlg :: OnInitDialog ().

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Vous pouvez maintenant générer et exécuter l’application. Notez que le texte de la zone de texte s’affiche dans une boîte de message contextuel lorsque l’application se ferme.

## <a name="see-also"></a>Voir aussi

[CWinFormsControl, classe](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
