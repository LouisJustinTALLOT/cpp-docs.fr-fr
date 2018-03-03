---
title: "Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 81a618c46f08366b9de2a02cbf84f73d42e7b108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>Comment : créer le contrôle utilisateur et l'héberger dans une boîte de dialogue
Les étapes de cet article supposent que vous créez basé sur une boîte de dialogue ([CDialog (classe)](../mfc/reference/cdialog-class.md)) project de Microsoft Foundation Classes (MFC), mais vous pouvez également ajouter la prise en charge pour un contrôle Windows Forms à une boîte de dialogue MFC existante.  
  
### <a name="to-create-the-net-user-control"></a>Pour créer le contrôle utilisateur .NET  
  
1.  Créez un projet de bibliothèque de contrôles Windows Forms Visual c# nommé `WindowsFormsControlLibrary1`.  
  
     Dans le menu **Fichier** , cliquez sur **Nouveau** , puis sur **Projet**. Dans le **Visual C#** dossier, sélectionnez **bibliothèque de contrôles Windows Forms**.  
  
     Accepter la `WindowsFormsControlLibrary1` nom du projet en cliquant sur **OK**.  
  
     Par défaut, le nom du contrôle .NET sera `UserControl1`.  
  
2.  Ajouter des contrôles enfants à `UserControl1`.  
  
     Dans le **boîte à outils**, ouvrez le **tous les Windows Forms** liste. Faites glisser un **bouton** le contrôle à la `UserControl1` aire de conception.  
  
     Ajoutez également une **TextBox** contrôle.  
  
3.  Dans **l’Explorateur de solutions**, double-cliquez sur **UserControl1.Designer.cs** à ouvrir pour le modifier. Modifier les déclarations de la zone de texte et le bouton de `private` à `public`.  
  
4.  Générez le projet.  
  
     Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application MFC hôte  
  
1.  Créer un projet d’Application MFC.  
  
     Dans le menu **Fichier** , cliquez sur **Nouveau** , puis sur **Projet**. Dans le **Visual C++** dossier, sélectionnez **Application MFC**.  
  
     Dans la zone **Nom**, tapez `MFC01`. Modifiez le paramètre de la Solution à **ajouter à la Solution**. Cliquez sur **OK**.  
  
     Dans le **Assistant Application MFC**, pour le Type d’Application, sélectionnez **basée sur un dialogue**. Acceptez les paramètres par défaut restantes et cliquez sur **Terminer**. Cette opération crée une application MFC qui possède une boîte de dialogue MFC.  
  
2.  Ajouter un contrôle d’espace réservé à la boîte de dialogue MFC.  
  
     Sur le **vue** menu, cliquez sur **affichage des ressources**. Dans **affichage des ressources**, développez le **boîte de dialogue** et double-cliquez sur `IDD_MFC01_DIALOG`. La ressource de boîte de dialogue s’affiche dans **éditeur de ressources**.  
  
     Dans le **boîte à outils**, ouvrez le **boîte de dialogue Éditeur** liste. Faites glisser un **texte statique** contrôle à la ressource de boîte de dialogue. Le **texte statique** contrôle servira d’un espace réservé pour le contrôle Windows Forms .NET. Redimensionnez-le à environ la taille du contrôle Windows Forms.  
  
     Dans le **propriétés** fenêtre, de modifier le **ID** de la **texte statique** le contrôle à `IDC_CTRL1` et modifier le **TabStop** propriété **True**.  
  
3.  Configurer le projet pour la prise en charge du Common Language Runtime (CLR).  
  
     Dans **l’Explorateur de solutions**, cliquez sur le nœud de projet MFC01, puis cliquez sur **propriétés**.  
  
     Dans le **Pages de propriétés** boîte de dialogue **propriétés de Configuration**, sélectionnez **général**. Dans le **projet par défaut est** section, définissez **prise en charge du Common Language Runtime** à **prise en charge du Common Language Runtime (/ clr)**.  
  
     Sous **propriétés de Configuration**, développez **C/C++** et sélectionnez le **général** nœud. Définissez **Format des informations de débogage** à **(/ Zi) de la base de données du programme**.  
  
     Sélectionnez le **génération de Code** nœud. Définissez **activer la régénération minimale** à **non (/ Gm-)**. Définissez également **base Runtime vérifie** à **par défaut**.  
  
     Cliquez sur **OK** pour appliquer les modifications.  
  
4.  Ajoutez une référence au contrôle .NET.  
  
     Dans **l’Explorateur de solutions**, cliquez sur le nœud de projet MFC01, puis sur **ajouter**, **références**. Sur le **Page de propriétés**, cliquez sur **ajouter une nouvelle référence**, sélectionnez **WindowsFormsControlLibrary1** (sous la **projets** onglet), puis cliquez sur **OK**. Cette opération ajoute une référence sous la forme d’un [/FU](../build/reference/fu-name-forced-hash-using-file.md) option du compilateur afin que le programme exécute la compilation. Il place également une copie de WindowsFormsControlLibrary1.dll dans le dossier du projet \MFC01\ afin que le programme s’exécute.  
  
5.  Dans le fichier Stdafx.h, recherchez cette ligne :  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Au-dessus de lui, ajoutez ces lignes :  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Ajoutez du code pour créer le contrôle managé.  
  
     Commencez par déclarer le contrôle managé. Dans MFC01Dlg.h, accédez à la déclaration de la classe de boîte de dialogue et ajouter un membre de données pour le contrôle utilisateur dans la portée protégé, comme suit.  
  
    ```  
    class CMFC01Dlg : public CDialog  
    {  
       // ...  
       // Data member for the .NET User Control:  
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;  
    ```  
  
     Ensuite, fournir une implémentation pour le contrôle managé. Dans MFC01Dlg.cpp, dans la boîte de dialogue Remplacer de `CMFC01Dlg::DoDataExchange` qui a été généré par l’Assistant Application MFC (pas `CAboutDlg::DoDataExchange`, qui se trouve dans le même fichier), ajoutez le code suivant pour créer le contrôle managé et l’associer à l’espace réservé statique IDC_CTRL1.  
  
    ```  
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
    {  
       CDialog::DoDataExchange(pDX);  
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);  
    }  
    ```  
  
7.  Générez et exécutez le projet.  
  
     Dans **l’Explorateur de solutions**, avec le bouton droit **MFC01** puis cliquez sur **définir comme projet de démarrage**.  
  
     Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**. La boîte de dialogue MFC doit afficher le contrôle Windows Forms.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement d’un contrôle utilisateur Windows Form dans une boîte de dialogue MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)