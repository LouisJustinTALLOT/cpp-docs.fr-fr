---
description: 'En savoir plus sur : Comment : créer le contrôle utilisateur et héberger l’affichage MDI'
title: "Comment : créer le contrôle utilisateur et héberger l'affichage MDI"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: d05d2132c4382365b1de16490481049cb43ffe22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328780"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Comment : créer le contrôle utilisateur et héberger l'affichage MDI

Les étapes suivantes montrent comment créer un contrôle utilisateur .NET Framework, comment créer le contrôle utilisateur dans une bibliothèque de classes de contrôle (plus précisément, un projet de bibliothèque de contrôles Windows), puis compiler le projet dans un assembly. Le contrôle peut ensuite être consommé à partir d’une application MFC qui utilise des classes dérivées de la [classe CView](../mfc/reference/cview-class.md) et de la [classe CWinFormsView](../mfc/reference/cwinformsview-class.md).

Pour plus d’informations sur la création d’un contrôle utilisateur Windows Forms et sur la création d’une bibliothèque de classes de contrôles, consultez [Comment : créer des contrôles utilisateur](/dotnet/framework/winforms/controls/how-to-author-composite-controls).

> [!NOTE]
> Dans certains cas, les contrôles de Windows Forms, tels qu’un contrôle de grille tiers, peuvent ne pas se comporter de façon fiable lorsqu’ils sont hébergés dans une application MFC. Une solution de contournement recommandée consiste à placer un contrôle utilisateur Windows Forms dans l’application MFC et à placer le contrôle de grille tiers à l’intérieur du contrôle utilisateur.

Cette procédure suppose que vous avez créé un projet de bibliothèque de contrôles Windows Forms nommé WindowsFormsControlLibrary1, conformément à la procédure décrite dans [Comment : créer le contrôle utilisateur et l’hôte dans une](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)boîte de dialogue.

### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application hôte MFC

1. Créez un projet d’application MFC.

   Dans le menu **fichier** , sélectionnez **nouveau**, puis cliquez sur **projet**. Dans le dossier **Visual C++** , sélectionnez **application MFC**.

   Dans la zone **nom** , entrez `MFC02` et remplacez le paramètre de **solution** par **Ajouter à la solution**. Cliquez sur **OK**.

   Dans l' **Assistant Application MFC**, acceptez toutes les valeurs par défaut, puis cliquez sur **Terminer**. Cela crée une application MFC avec une interface à plusieurs documents.

1. Configurez le projet pour la prise en charge du Common Language Runtime (CLR).

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `MFC01` nœud du projet, puis sélectionnez **Propriétés** dans le menu contextuel. La boîte de dialogue **pages de propriétés** s’affiche.

   Sous **Propriétés de configuration**, sélectionnez **général**. Dans la section **paramètres par défaut du projet** , définissez prise en charge du Common **Language Runtime** pour la **prise en charge du Common Language Runtime (/CLR)**.

   Sous **Propriétés de configuration**, développez **C/C++** , puis cliquez sur le nœud **général** . Définissez **format des informations de débogage** sur **base de données du programme (/ZI)**.

   Cliquez sur le nœud **génération de code** . Affectez à **activer la régénération minimale** la valeur **non (/GM-)**. Affectez également la valeur **par défaut** aux **vérifications de base du runtime** .

   Cliquez sur **OK** pour appliquer vos modifications.

1. Dans *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures), ajoutez la ligne suivante :

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Ajoutez une référence au contrôle .NET.

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le `MFC02` nœud du projet et sélectionnez **Ajouter**, **références**. Dans la **page de propriétés**, cliquez sur **Ajouter une nouvelle référence**, sélectionnez WindowsFormsControlLibrary1 (sous l’onglet **projets** ), puis cliquez sur **OK**. Cela ajoute une référence sous la forme d’une option du compilateur [/Fu](../build/reference/fu-name-forced-hash-using-file.md) afin que le programme soit compilé ; il copie également WindowsFormsControlLibrary1.dll dans le `MFC02` répertoire du projet afin que le programme s’exécute.

1. Dans stdafx. h, recherchez la ligne suivante :

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Ajoutez ces lignes au-dessus de celle-ci :

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Modifiez la classe d’affichage afin qu’elle hérite de [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   Dans MFC02View. h, remplacez [CView](../mfc/reference/cview-class.md) par [CWinFormsView](../mfc/reference/cwinformsview-class.md) afin que le code apparaisse comme suit :

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Si vous souhaitez ajouter des vues supplémentaires à votre application MDI, vous devrez appeler [CWinApp :: AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pour chaque vue que vous créez.

1. Modifiez le fichier MFC02View. cpp pour remplacer CView par CWinFormsView dans la IMPLEMENT_DYNCREATE la macro et la table des messages et remplacez le constructeur vide existant par le constructeur illustré ci-dessous :

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. Générez et exécutez le projet.

   Dans **Explorateur de solutions**, cliquez avec le bouton droit sur MFC02 et sélectionnez **définir comme projet de démarrage**.

   Dans le menu **Générer**, cliquez sur **Générer la solution**.

   Dans le menu **Déboguer** , cliquez sur **exécuter sans débogage**.

## <a name="see-also"></a>Voir aussi

[Hébergement d'un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
