---
title: "Comment : créer le contrôle utilisateur et héberger l'affichage MDI"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 72501ba32d3b8b9a5c5fd8dd0c56f0628642b147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374466"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Comment : créer le contrôle utilisateur et héberger l'affichage MDI

Les étapes suivantes montrent comment créer un contrôle utilisateur .NET Framework, l’auteur du contrôle de l’utilisateur dans une bibliothèque de classe de contrôle (en particulier, un projet de bibliothèque de contrôle Windows), puis compiler le projet dans un assemblage. Le contrôle peut alors être consommé à partir d’une application MFC qui utilise des classes dérivées de [la classe CView](../mfc/reference/cview-class.md) et [de la classe CWinFormsView](../mfc/reference/cwinformsview-class.md).

Pour plus d’informations sur la façon de créer un contrôle utilisateur Windows Forms et d’écrire une bibliothèque de classe de contrôle, voir [Comment: Author User Controls](/dotnet/framework/winforms/controls/how-to-author-composite-controls).

> [!NOTE]
> Dans certains cas, les contrôles Windows Forms, tels qu’un contrôle de grille tiers, peuvent ne pas se comporter de manière fiable lorsqu’ils sont hébergés dans une application MFC. Une solution de contournement recommandée est de placer un contrôle utilisateur Windows Forms dans l’application MFC et de placer le contrôle de la grille tiers à l’intérieur du contrôle de l’utilisateur.

Cette procédure suppose que vous avez créé un projet Windows Forms Controls Library nommé WindowsFormsControlLibrary1, selon la procédure dans [Comment : Créer le contrôle de l’utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

### <a name="to-create-the-mfc-host-application"></a>Créer l’application d’hôte MFC

1. Créez un projet d’application MFC.

   Sur le menu **Du fichier,** sélectionnez **Nouveau**, puis cliquez sur **Le projet**. Dans le dossier **Visual CMD,** sélectionnez **L’application MFC**.

   Dans la boîte `MFC02` **nomin,** entrez et modifiez le paramètre **de solution** pour ajouter à **la solution**. Cliquez sur **OK**.

   Dans le **MFC Application Wizard**, accepter tous les défauts, puis cliquez sur **Finition**. Cela crée une application MFC avec une interface de document multiple.

1. Configurez le projet pour le support Common Language Runtime (CLR).

   Dans **Solution Explorer**, `MFC01` cliquez à droite sur le nœud du projet et sélectionnez **les propriétés** du menu contextuelle. La boîte de dialogue **des Pages de propriété** apparaît.

   Sous **Configuration Properties**, sélectionnez **Général**. Dans le cadre de la section **Défauts de projet,** définissez **le support Common Language Runtime** au support courant de temps **d’exécution de langue (/clr)**.

   Sous **Configuration Properties**, étendre **C/CM et** cliquez sur le nœud **général.** Définir **Le format d’information Debug** à **la base de données de programme (/Zi)**.

   Cliquez sur le nœud **De génération de** code. Définir **Permettre une reconstruction minimale** à no **(/Gm-)**. Définissez également **les vérifications de temps de course de base** par **défaut**.

   Cliquez **sur OK** pour appliquer vos modifications.

1. Dans *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt), ajoutez la ligne suivante :

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Ajoutez une référence au contrôle .NET.

   Dans **Solution Explorer**, `MFC02` cliquez à droite sur le nœud du projet et sélectionnez **Ajouter**, **Références**. Dans la **page propriété**, cliquez sur Ajouter une **nouvelle référence**, sélectionnez WindowsFormsControlLibrary1 (sous l’onglet **Projets),** et cliquez **sur OK**. Cela ajoute une référence sous la forme d’une option de compilation [/FU](../build/reference/fu-name-forced-hash-using-file.md) afin que le programme compile; il copie également WindowsFormsControlLibrary1.dll dans l’annuaire du `MFC02` projet afin que le programme s’exécute.

1. Dans stdafx.h, trouvez cette ligne :

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Ajoutez ces lignes au-dessus :

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Modifier la classe de vue de sorte qu’il hérite de [CWinFormsView](../mfc/reference/cwinformsview-class.md).

   Dans MFC02View.h, [remplacez CView](../mfc/reference/cview-class.md) par [CWinFormsView](../mfc/reference/cwinformsview-class.md) de sorte que le code apparaît comme suit :

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Si vous souhaitez ajouter des vues supplémentaires à votre application MDI, vous devrez appeler [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pour chaque vue que vous créez.

1. Modifier le fichier MFC02View.cpp pour changer CView en CWinFormsView dans la carte macro et message IMPLEMENT_DYNCREATE et remplacer le constructeur vide existant par le constructeur indiqué ci-dessous :

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

   Dans **Solution Explorer**, cliquez à droite MFC02 et sélectionnez Set comme **startUp Project**.

   Dans le menu **Générer**, cliquez sur **Générer la solution**.

   Sur le menu **Debug,** cliquez sur **Démarrer sans débogage**.

## <a name="see-also"></a>Voir aussi

[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
