---
description: 'En savoir plus sur : Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue'
title: "Comment : créer le contrôle utilisateur et l'héberger dans une boîte de dialogue"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
ms.openlocfilehash: 400906344f47f7100e52319adb37c39d1fb370e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283960"
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>Comment : créer le contrôle utilisateur et l'héberger dans une boîte de dialogue

Les étapes décrites dans cet article partent du principe que vous créez un projet de[Microsoft Foundation classes (MFC](../mfc/reference/cdialog-class.md)) basé sur une boîte de dialogue, mais vous pouvez également ajouter la prise en charge d’un contrôle Windows Forms à une boîte de dialogue MFC existante.

### <a name="to-create-the-net-user-control"></a>Pour créer le contrôle utilisateur .NET

1. Créez un projet de bibliothèque de contrôles Windows Forms Visual C# nommé `WindowsFormsControlLibrary1` .

   Dans le menu **Fichier**, cliquez sur **Nouveau**, puis cliquez sur **Projet**. Dans le dossier **Visual C#** , sélectionnez **Windows Forms bibliothèque de contrôles**.

   Acceptez le `WindowsFormsControlLibrary1` nom du projet en cliquant sur **OK**.

   Par défaut, le nom du contrôle .NET sera `UserControl1` .

1. Ajoutez des contrôles enfants à `UserControl1` .

   Dans la **boîte à outils**, ouvrez la liste **tous les Windows Forms** . Faites glisser un contrôle **Button** sur l' `UserControl1` aire de conception.

   Ajoutez également un contrôle **TextBox** .

1. Dans **Explorateur de solutions**, double-cliquez sur **UserControl1.Designer.cs** pour l’ouvrir et le modifier. Remplacez les déclarations de la zone de texte et du bouton par `private` `public` .

1. Créez le projet.

   Dans le menu **Générer**, cliquez sur **Générer la solution**.

### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application hôte MFC

1. Créez un projet d’application MFC.

   Dans le menu **Fichier**, cliquez sur **Nouveau**, puis cliquez sur **Projet**. Dans le dossier **Visual C++** , sélectionnez **application MFC**.

   Dans le champ **Nom**, saisissez `MFC01`. Remplacez le paramètre de solution par **Ajouter à la solution**. Cliquez sur **OK**.

   Dans l' **Assistant Application MFC**, pour type d’application, sélectionnez **basée sur une boîte de dialogue**. Acceptez les paramètres par défaut restants, puis cliquez sur **Terminer**. Cela crée une application MFC qui a une boîte de dialogue MFC.

1. Ajoutez un contrôle PlaceHolder à la boîte de dialogue MFC.

   Dans le menu **affichage** , cliquez sur **affichage des ressources**. Dans **affichage des ressources**, développez le dossier **boîte de dialogue** et double-cliquez sur `IDD_MFC01_DIALOG` . La ressource de boîte de dialogue s’affiche dans l' **éditeur de ressources**.

   Dans la **boîte à outils**, ouvrez la liste de l' **éditeur de boîtes de dialogue** . Faites glisser un contrôle de **texte statique** vers la ressource de boîte de dialogue. Le contrôle de **texte statique** servira d’espace réservé pour le contrôle de Windows Forms .net. Redimensionnez-le pour qu’il soit approximativement la taille du contrôle Windows Forms.

   Dans la fenêtre **Propriétés** , affectez à l' **ID** du contrôle de **texte statique** la `IDC_CTRL1` valeur et affectez à la propriété **TabStop** la **valeur true**.

1. Configurez le projet pour la prise en charge du Common Language Runtime (CLR).

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet MFC01, puis cliquez sur **Propriétés**.

   Dans la boîte de dialogue **pages de propriétés** , sous **Propriétés de configuration**, sélectionnez **général**. Dans la section **paramètres par défaut du projet** , définissez la prise en charge du Common **Language Runtime** sur la **prise en charge du Common Language Runtime (/CLR)**.

   Sous **Propriétés de configuration**, développez **C/C++** , puis sélectionnez le nœud **général** . Définissez **format des informations de débogage** sur **base de données du programme (/ZI)**.

   Sélectionnez le nœud **génération de code** . Affectez à **activer la régénération minimale** la valeur **non (/GM-)**. Affectez également la valeur **par défaut** aux **vérifications de base du runtime** .

   Cliquez sur **OK** pour appliquer les modifications.

1. Ajoutez une référence au contrôle .NET.

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet MFC01, puis cliquez sur **Ajouter**, **références**. Sur la **page de propriétés**, cliquez sur **Ajouter une nouvelle référence**, sélectionnez **WindowsFormsControlLibrary1** (sous l’onglet **projets** ), puis cliquez sur **OK**. Cela ajoute une référence sous la forme d’une option du compilateur [/Fu](../build/reference/fu-name-forced-hash-using-file.md) afin que le programme soit compilé. Il place également une copie de WindowsFormsControlLibrary1.dll dans le dossier du projet \MFC01\ afin que le programme s’exécute.

1. Dans stdafx. h, recherchez la ligne suivante :

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Au-dessus, ajoutez les lignes suivantes :

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Ajoutez du code pour créer le contrôle managé.

   Tout d’abord, déclarez le contrôle managé. Dans MFC01Dlg. h, accédez à la déclaration de la classe Dialog et ajoutez un membre de données pour le contrôle utilisateur dans la portée protégée, comme suit.

    ```
    class CMFC01Dlg : public CDialog
    {
       // ...
       // Data member for the .NET User Control:
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;
    ```

   Ensuite, fournissez une implémentation pour le contrôle managé. Dans MFC01Dlg. cpp, dans la substitution de boîte de dialogue de `CMFC01Dlg::DoDataExchange` qui a été générée par l’Assistant Application MFC (pas `CAboutDlg::DoDataExchange` , qui se trouve dans le même fichier), ajoutez le code suivant pour créer le contrôle managé et l’associer à l’espace réservé statique IDC_CTRL1.

    ```
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
    {
       CDialog::DoDataExchange(pDX);
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);
    }
    ```

1. Générez et exécutez le projet.

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **MFC01** , puis cliquez sur **définir comme projet de démarrage**.

   Dans le menu **Générer**, cliquez sur **Générer la solution**.

   Dans le menu **Déboguer** , cliquez sur **exécuter sans débogage**. La boîte de dialogue MFC doit afficher le contrôle Windows Forms.

## <a name="see-also"></a>Voir aussi

[Hébergement d’un contrôle utilisateur Windows Form dans une boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)
