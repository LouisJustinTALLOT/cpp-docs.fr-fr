---
title: 'Comment : créer le contrôle utilisateur et héberger l’affichage MDI | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 449f0026cd2d7603ceb190cc747138189313974f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136481"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Comment : créer le contrôle utilisateur et héberger l'affichage MDI
Les étapes suivantes montrent comment créer un contrôle utilisateur de .NET Framework, créer le contrôle utilisateur dans une bibliothèque de classes de contrôle (plus précisément, un projet de bibliothèque de contrôles Windows), puis compiler le projet dans un assembly. Le contrôle peut ensuite être consommé à partir d’une application MFC qui utilise des classes dérivées de [classe CView](../mfc/reference/cview-class.md) et [classe CWinFormsView](../mfc/reference/cwinformsview-class.md).  
  
 Pour plus d’informations sur la façon de créer un contrôle utilisateur Windows Forms et de créer une bibliothèque de classes de contrôle, consultez [Comment : créer des contrôles utilisateur](/dotnet/framework/winforms/controls/how-to-author-composite-controls).  
  
> [!NOTE]
>  Dans certains cas, les contrôles Windows Forms, par exemple un contrôle de grille tiers, ne peuvent pas se comportent de façon fiable lorsqu’il est hébergé dans une application MFC. Une solution de contournement recommandée consiste à placer un contrôle Windows Forms utilisateur dans l’application MFC et le contrôle de grille de tiers à l’intérieur du contrôle utilisateur.  
  
 Cette procédure suppose que vous avez créé un projet de bibliothèque de contrôles Windows Forms nommé WindowsFormsControlLibrary1, selon la procédure décrite dans [Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).  
  
### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application MFC hôte  
  
1.  Créer un projet d’Application MFC.  
  
     Sur le **fichier** menu, sélectionnez **nouveau**, puis cliquez sur **projet**. Dans le **Visual C++** dossier, sélectionnez **Application MFC**.  
  
     Dans le **nom** , entrez `MFC02` et modifiez le **Solution** à **ajouter à la Solution**. Cliquez sur **OK**.  
  
     Dans le **Assistant Application MFC**, acceptez les valeurs par défaut, puis cliquez sur **Terminer**. Cette opération crée une application MFC avec une Interface multidocument.  
  
2.  Configurer le projet pour la prise en charge du Common Language Runtime (CLR).  
  
     Dans **l’Explorateur de solutions**, cliquez sur le `MFC01` nœud de projet, puis sélectionnez **propriétés** dans le menu contextuel. Le **Pages de propriétés** boîte de dialogue s’affiche.  
  
     Sous **propriétés de Configuration**, sélectionnez **général**. Sous le **projet par défaut est** section, définissez **prise en charge du Common Language Runtime** à **prise en charge du Common Language Runtime (/ clr)**.  
  
     Sous **propriétés de Configuration**, développez **C/C++** et cliquez sur le **général** nœud. Définissez **Format des informations de débogage** à **(/ Zi) de la base de données du programme**.  
  
     Cliquez sur le **génération de Code** nœud. Définissez **activer la régénération minimale** à **non (/ Gm-)**. Définissez également **base Runtime vérifie** à **par défaut**.  
  
     Cliquez sur **OK** pour appliquer vos modifications.  
  
3.  Dans le fichier stdafx.h, ajoutez la ligne suivante :  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
4.  Ajoutez une référence au contrôle .NET.  
  
     Dans **l’Explorateur de solutions**, avec le bouton droit le `MFC02` le nœud de projet et sélectionnez **ajouter**, **références**. Dans le **Page de propriétés**, cliquez sur **ajouter une nouvelle référence**, sélectionnez WindowsFormsControlLibrary1 (sous la **projets** onglet), puis cliquez sur **OK** . Cette opération ajoute une référence sous la forme d’un [/FU](../build/reference/fu-name-forced-hash-using-file.md) option du compilateur afin que le programme exécute la compilation ; il copie également WindowsFormsControlLibrary1.dll dans le `MFC02` répertoire du projet afin que le programme s’exécute.  
  
5.  Dans le fichier stdafx.h, recherchez cette ligne :  
  
    ```  
    #endif // _AFX_NO_AFXCMN_SUPPORT   
    ```  
  
     Ajoutez ces lignes au-dessus d’elle :  
  
    ```  
    #include <afxwinforms.h>   // MFC Windows Forms support  
    ```  
  
6.  Modifier la classe d’affichage afin qu’elle hérite de [CWinFormsView](../mfc/reference/cwinformsview-class.md).  
  
     Dans MFC02View.h, remplacez [CView](../mfc/reference/cview-class.md) avec [CWinFormsView](../mfc/reference/cwinformsview-class.md) afin que le code s’affiche comme suit :  
  
    ```  
    class CMFC02View : public CWinFormsView  
    {  
    };  
    ```  
  
     Si vous souhaitez ajouter des affichages supplémentaires à votre application MDI, vous devez appeler [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pour chaque vue que vous créez.  
  
7.  Modifiez le fichier MFC02View.cpp pour transformer CView en CWinFormsView dans l’Explorateur de macros et message IMPLEMENT_DYNCREATE et remplacez le constructeur vide existant avec le constructeur illustré ci-dessous :  
  
    ```  
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)  
  
    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)   
    {  
    }  
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)  
    //leave existing body as is  
    END_MESSAGE_MAP()  
    ```  
  
8.  Générez et exécutez le projet.  
  
     Dans **l’Explorateur de solutions**, MFC02 d’avec le bouton droit et sélectionnez **définir comme projet de démarrage**.  
  
     Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**.  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)