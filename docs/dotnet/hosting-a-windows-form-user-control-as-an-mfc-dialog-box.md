---
title: Hébergement d’un Windows forment un contrôle utilisateur comme une boîte de dialogue MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2355a5341259978e402ecc6f8de5c684c9435e3a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433060"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hébergement d'un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC

MFC fournit la classe de modèle [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) afin que vous pouvez héberger un contrôle utilisateur Windows Forms (<xref:System.Windows.Forms.UserControl>) dans une boîte de dialogue MFC modale ou non modale. `CWinFormsDialog` est dérivé de la classe MFC [CDialog](../mfc/reference/cdialog-class.md), de sorte que la boîte de dialogue peut être lancée en tant que modale ou non modale.

Le processus qui `CWinFormsDialog` utilise pour héberger le contrôle utilisateur est similaire à celui décrit dans [qui héberge un contrôle d’utilisateur Windows Form dans une boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Toutefois, `CWinFormsDialog` gère l’initialisation et l’hébergement du contrôle utilisateur afin qu’il n’a pas de le programmer manuellement.

Pour un exemple d’application qui illustre Windows Forms avec MFC, consultez [MFC et l’intégration de formulaires Windows](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application MFC hôte

1. Créer un projet d’Application MFC.

     Sur le **fichier** menu, sélectionnez **New**, puis cliquez sur **projet**. Dans le **Visual C++** dossier, sélectionnez **Application MFC**.

     Dans le **nom** , entrez `MFC03` et modifiez le paramètre Solution en **ajouter à la Solution**. Cliquez sur **OK**.

     Dans le **Assistant Application MFC**, acceptez toutes les valeurs par défaut, puis cliquez sur **Terminer**. Cette opération crée une application MFC avec une Interface multidocument.

1. Configurez le projet.

     Dans **l’Explorateur de solutions**, cliquez sur le **MFC03** nœud de projet, puis choisissez **propriétés**. Le **Pages de propriétés** boîte de dialogue s’affiche.

     Dans le **Pages de propriétés** boîte de dialogue le **propriétés de Configuration** contrôle d’arborescence, sélectionnez **général**, puis dans la **projet par défaut est**section, définissez **prise en charge du Common Language Runtime** à **prise en charge du Common Language Runtime (/ clr)**. Cliquez sur **OK**.

1. Ajoutez une référence au contrôle .NET.

     Dans **l’Explorateur de solutions**, avec le bouton droit le **MFC03** nœud de projet et choisissez **ajouter**, **références**. Dans le **Page de propriétés**, cliquez sur **ajouter une nouvelle référence**, sélectionnez WindowsControlLibrary1 (sous le **projets** onglet), puis cliquez sur **OK**. Cette opération ajoute une référence sous la forme d’un [/FU](../build/reference/fu-name-forced-hash-using-file.md) option du compilateur afin que le programme est compilé ; cela copie également WindowsControlLibrary1.dll dans le `MFC03` répertoire du projet afin que le programme s’exécute.

1. Ajouter `#include <afxwinforms.h>` à stdafx.h, à la fin de l’existante `#include` instructions.

1. Ajoutez une nouvelle classe qui sous-classe `CDialog`.

     Cliquez avec le bouton droit sur le nom du projet et ajoutez une classe MFC (appelée CHostForWinForm) qui sous-classe `CDialog`. Étant donné que vous n’avez pas besoin de la ressource de boîte de dialogue, vous pouvez supprimer l’ID de ressource (sélectionnez Affichage des ressources, développez le dossier de boîte de dialogue et supprimez la ressource IDD_HOSTFORWINFORM.  Ensuite, supprimez toutes les références à l’ID dans le code.).

1. Remplacez `CDialog` dans les fichiers CHostForWinForm.h et CHostForWinForm.cpp avec `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.

1. Appelez DoModal sur la classe CHostForWinForm.

     Dans MFC03.cpp, ajoutez `#include "HostForWinForm.h"`.

     Avant l’instruction return dans la définition de CMFC03App::InitInstance, ajoutez :

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Générez et exécutez le projet.

     Dans le menu **Générer** , cliquez sur **Générer la solution**.

     Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**.

     Ensuite, vous allez ajouter le code pour analyser l’état d’un contrôle sur les formulaires Windows à partir de l’application MFC.

9. Ajoutez un gestionnaire pour OnInitDialog.

     Afficher le **propriétés** fenêtre (F4). Dans **affichage de classes**, sélectionnez CHostForWinForm. Dans le **propriétés** fenêtre, sélectionnez remplace dans la ligne correspondant à OnInitDialog, cliquez dans la colonne de gauche et sélectionnez \< Ajouter >. Cette opération ajoute la ligne suivante est ajoutée à CHostForWinForm.h :

    ```cpp
    virtual BOOL OnInitDialog();
    ```

10. Définissez OnInitDialog (dans CHostForWinForm.cpp) comme suit :

    ```
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

11. Ensuite, ajoutez le gestionnaire OnButton1. Ajoutez les lignes suivantes à la section publique de la classe CHostForWinForm contenue dans CHostForWinForm.h :

    ```
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

     Dans CHostForWinForm.cpp, ajoutez la définition suivante :

    ```
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

12. Générez et exécutez le projet. Lorsque vous cliquez sur le bouton, ce qui se trouve sur le formulaire Windows, c’est le code de l’application MFC qui s’exécute.

     Ensuite, vous allez ajouter le code pour afficher la valeur à partir du code MFC dans la zone de texte sur le formulaire Windows.

13. Dans la section publique de la classe CHostForWinForm contenue dans CHostForWinForm.h, ajoutez la déclaration suivante :

    ```
    CString m_sEditBoxOnWinForm;
    ```

14. Dans la définition de DoDataExchange dans CHostForWinForm.cpp, ajoutez les trois lignes suivantes à la fin de la fonction :

    ```
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

15. Dans la définition de OnButton1 dans CHostForWinForm.cpp, ajoutez les trois lignes suivantes à la fin de la fonction :

    ```
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

16. Générez et exécutez le projet.

## <a name="see-also"></a>Voir aussi

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[À l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)