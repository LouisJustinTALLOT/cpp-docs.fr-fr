---
title: 'Procédure : Faire de DDX / DDV liaison de données avec Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 558c763fd18cd1569ff23435bf6156b3117f117d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387316"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Procédure : Faire de DDX/DDV liaison de données avec Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) appels [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) pour créer un contrôle correspondant à l’ID de contrôle de ressource. Si vous utilisez `DDX_ManagedControl` pour un `CWinFormsControl` contrôle (dans le code généré par l’Assistant), vous ne devez pas appeler `CreateManagedControl` explicitement pour le même contrôle.

Appelez `DDX_ManagedControl` dans [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) pour créer des contrôles à partir de l’ID de ressource. Échange de données, vous n’avez pas besoin d’utiliser les fonctions DDX/DDV avec les contrôles Windows Forms. Au lieu de cela, vous pouvez placer le code pour accéder aux propriétés du contrôle managé dans le `DoDataExchange` méthode de votre classe de boîte de dialogue (ou vue), comme dans l’exemple suivant.

L’exemple suivant montre comment lier une chaîne C++ native à un contrôle utilisateur .NET.

## <a name="example"></a>Exemple

Voici un exemple de liaison de données DDX/DDV d’une chaîne MFC `m_str` avec défini par l’utilisateur `NameText` propriété d’un contrôle utilisateur .NET.

Le contrôle est créé lorsque [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) appels `CMyDlg::DoDataExchange` pour la première fois, afin que tout code qui fait référence à `m_UserControl` doit être placée après le `DDX_ManagedControl` appeler.

Vous pouvez implémenter ce code dans l’application MFC01 que vous avez créé dans [Comment : Créer le contrôle utilisateur et l’héberger dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

Placez le code suivant dans la déclaration de CMFC01Dlg :

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>Exemple

Placez le code suivant dans l’implémentation de CMFC01Dlg :

```
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

Nous allons maintenant ajouter la méthode de gestionnaire pour un clic sur le bouton OK. Cliquez sur le **affichage des ressources** onglet. Dans l’affichage des ressources, double-cliquez sur `IDD_MFC01_DIALOG`. La ressource de boîte de dialogue s’affiche dans l’éditeur de ressources. Puis double-cliquez sur le bouton OK...

Définissez le gestionnaire comme suit.

```
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>Exemple

Et ajoutez la ligne suivante à l’implémentation de BOOL CMFC01Dlg::OnInitDialog ().

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Vous pouvez maintenant générer et exécuter l’application. Notez que n’importe quel texte dans la zone de texte s’affichera dans une boîte de message lorsque l’application se ferme.

## <a name="see-also"></a>Voir aussi

[CWinFormsControl, classe](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
