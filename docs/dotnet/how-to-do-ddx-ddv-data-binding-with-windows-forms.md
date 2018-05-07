---
title: 'Comment : effectuer une liaison de données DDX-DDV avec Windows Forms | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2f6992aa0c7238d2dc89a8084c7b870dae23067a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Comment : établir la liaison des données DDX/DDV avec Windows Forms
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) appelle [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) pour créer un contrôle correspondant à l’ID du contrôle de ressource. Si vous utilisez `DDX_ManagedControl` pour un `CWinFormsControl` contrôle (dans le code généré par l’Assistant), vous ne devez pas appeler `CreateManagedControl` explicitement pour le même contrôle.  
  
 Appelez `DDX_ManagedControl` dans [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) pour créer des contrôles d’ID de ressource. Pour l’échange de données, vous n’avez pas besoin d’utiliser les fonctions DDX/DDV avec les contrôles Windows Forms. Au lieu de cela, vous pouvez placer le code pour accéder aux propriétés du contrôle managé dans la `DoDataExchange` méthode de votre classe de boîte de dialogue (ou vue), comme dans l’exemple suivant.  
  
 L’exemple suivant montre comment lier une chaîne C++ native à un contrôle utilisateur .NET.  
  
## <a name="example"></a>Exemple  
 Voici un exemple de liaison de données DDX/DDV d’une chaîne MFC `m_str` avec défini par l’utilisateur `NameText` propriété d’un contrôle utilisateur .NET.  
  
 Le contrôle est créé lorsque [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) appelle `CMyDlg::DoDataExchange` pour la première fois, afin que tout code qui fait référence à `m_UserControl` doit être placée après le `DDX_ManagedControl` appeler.  
  
 Vous pouvez implémenter ce code dans l’application MFC01 que vous avez créé dans [Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
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
  
 Vous pouvez maintenant générer et exécuter l’application. Notez que tout texte dans la zone de texte s’affichera dans une boîte de message lorsque l’application se ferme.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)   
 [DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)   
 [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)