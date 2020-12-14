---
description: 'En savoir plus sur : Hébergement d’un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC'
title: Hébergement d'un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 0139e26fee834d47bc0d513c3b64bf3c09368b22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335461"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hébergement d'un contrôle utilisateur Windows Form en tant que boîte de dialogue MFC

MFC fournit la classe de modèle [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) afin que vous puissiez héberger un contrôle utilisateur Windows Forms ( <xref:System.Windows.Forms.UserControl> ) dans une boîte de dialogue MFC modale ou non modale. `CWinFormsDialog` est dérivé de la classe MFC [CDialog](../mfc/reference/cdialog-class.md), de sorte que la boîte de dialogue peut être lancée comme modale ou non modale.

Le processus qui `CWinFormsDialog` utilise pour héberger le contrôle utilisateur est similaire à celui décrit dans [hébergement d’un contrôle utilisateur Windows Form dans une boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Toutefois, `CWinFormsDialog` gère l’initialisation et l’hébergement du contrôle utilisateur afin qu’il n’ait pas à être programmé manuellement.

Pour obtenir un exemple d’application qui montre Windows Forms utilisé avec MFC, consultez [MFC and Windows Forms Integration](https://www.microsoft.com/download/details.aspx?id=2113).

### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application hôte MFC

1. Créez un projet d’application MFC.

   Dans le menu **fichier** , sélectionnez **nouveau**, puis cliquez sur **projet**. Dans le dossier **Visual C++** , sélectionnez **application MFC**.

   Dans la zone **nom** , entrez `MFC03` et remplacez le paramètre de solution par **Ajouter à la solution**. Cliquez sur **OK**.

   Dans l' **Assistant Application MFC**, acceptez toutes les valeurs par défaut, puis cliquez sur **Terminer**. Cela crée une application MFC avec une interface à plusieurs documents.

1. Configurez le projet.

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet **MFC03** , puis choisissez **Propriétés**. La boîte de dialogue **pages de propriétés** s’affiche.

   Dans la boîte de dialogue **pages de propriétés** , dans le contrôle d’arborescence **Propriétés de configuration** , sélectionnez **général**, puis dans la section **paramètres par défaut du projet** , affectez à **prise en** charge du Common Language Runtime la prise **en charge du Common Language Runtime (/CLR)**. Cliquez sur **OK**.

1. Ajoutez une référence au contrôle .NET.

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet **MFC03** et choisissez **Ajouter**, **références**. Dans la **page de propriétés**, cliquez sur **Ajouter une nouvelle référence**, sélectionnez WindowsControlLibrary1 (sous l’onglet **projets** ), puis cliquez sur **OK**. Cela ajoute une référence sous la forme d’une option du compilateur [/Fu](../build/reference/fu-name-forced-hash-using-file.md) afin que le programme soit compilé ; il copie également WindowsControlLibrary1.dll dans le `MFC03` répertoire du projet afin que le programme s’exécute.

1. Ajoutez `#include <afxwinforms.h>` à *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures) à la fin des instructions existantes `#include` .

1. Ajoutez une nouvelle classe qui sous-classe `CDialog` .

   Cliquez avec le bouton droit sur le nom du projet et ajoutez une classe MFC (appelée CHostForWinForm) qui sous-classe `CDialog` . Étant donné que vous n’avez pas besoin de la ressource de boîte de dialogue, vous pouvez supprimer l’ID de ressource (sélectionnez **affichage des ressources**, développez le dossier **boîte de dialogue** et supprimez la `IDD_HOSTFORWINFORM` ressource.  Ensuite, supprimez toutes les références à l’ID dans le code.).

1. Remplacez `CDialog` dans les fichiers CHostForWinForm. h et CHostForWinForm. cpp par `CWinFormsDialog<WindowsControlLibrary1::UserControl1>` .

1. Appelez DoModal sur la classe CHostForWinForm.

   Dans MFC03. cpp, ajoutez `#include "HostForWinForm.h"` .

   Avant l’instruction return dans la définition de CMFC03App :: InitInstance, ajoutez :

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Générez et exécutez le projet.

   Dans le menu **Générer**, cliquez sur **Générer la solution**.

   Dans le menu **Déboguer** , cliquez sur **exécuter sans débogage**.

   Ensuite, vous allez ajouter du code pour surveiller l’état d’un contrôle sur le Windows Forms à partir de l’application MFC.

1. Ajoutez un gestionnaire pour OnInitDialog.

   Affichez la fenêtre **Propriétés** (F4). Dans **affichage de classes**, sélectionnez CHostForWinForm. Dans la fenêtre **Propriétés** , sélectionnez remplacements et dans la ligne pour OnInitDialog, cliquez dans la colonne de gauche et sélectionnez \< Add > . La ligne suivante est ajoutée à CHostForWinForm. h :

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. Définissez OnInitDialog (dans CHostForWinForm. cpp) comme suit :

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. Ajoutez ensuite le gestionnaire OnButton1. Ajoutez les lignes suivantes à la section publique de la classe CHostForWinForm dans CHostForWinForm. h :

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   Dans CHostForWinForm. cpp, ajoutez la définition suivante :

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. Générez et exécutez le projet. Lorsque vous cliquez sur le bouton, qui se trouve dans le Windows Form, le code de l’application MFC s’exécute.

    Ensuite, vous allez ajouter du code pour afficher à partir du code MFC la valeur dans la zone de texte sur le Windows Form.

1. Dans la section publique de la classe CHostForWinForm dans CHostForWinForm. h, ajoutez la déclaration suivante :

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. Dans la définition de DoDataExchange dans CHostForWinForm. cpp, ajoutez les trois lignes suivantes à la fin de la fonction :

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. Dans la définition de OnButton1 dans CHostForWinForm. cpp, ajoutez les trois lignes suivantes à la fin de la fonction :

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. Générez et exécutez le projet.

## <a name="see-also"></a>Voir aussi

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[Utilisation d’un contrôle utilisateur Windows Form dans MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
