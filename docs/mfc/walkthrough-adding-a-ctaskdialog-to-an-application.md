---
title: 'Procédure pas à pas : Ajout d’un classe CTaskDialog à une Application | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f803af896c1bb2a0e5f58e45f4ef9f588f4e66d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420478"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Procédure pas à pas : ajout d'une classe CTaskDialog à une application

Cette procédure pas à pas présente la [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) et vous montre comment en ajouter une à votre application.

Le `CTaskDialog` est une boîte de dialogue de tâche qui remplace la boîte de message Windows dans Windows Vista ou version ultérieure. `CTaskDialog` améliore la boîte de message d’origine et ajoute des fonctionnalités. La boîte de message Windows est toujours pris en charge dans Visual Studio.

> [!NOTE]
> Versions de Windows antérieures à Windows Vista ne gèrent pas la `CTaskDialog`. Si vous voulez présenter un message à un utilisateur qui exécute votre application sur une version antérieure de Windows, vous devez programmer une autre option de boîte de dialogue. Vous pouvez utiliser la méthode statique [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) pour déterminer au moment de l’exécution si l’ordinateur d’un utilisateur peut afficher un `CTaskDialog`. De plus, `CTaskDialog` est disponible uniquement quand votre application est générée avec la bibliothèque Unicode.

`CTaskDialog` prend en charge plusieurs éléments facultatifs pour collecter et afficher des informations. Par exemple, un `CTaskDialog` peut afficher des liens de commande, des boutons personnalisés, des icônes personnalisées et un pied de page. Par ailleurs, `CTaskDialog` intègre plusieurs méthodes qui vous permettent d’interroger l’état de la boîte de dialogue de tâche pour identifier les éléments facultatifs que l’utilisateur a sélectionnés.

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Visual Studio 2010 ou version ultérieure

- Windows Vista ou version ultérieure

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Remplacement d’une boîte de message Windows par un CTaskDialog

La procédure suivante illustre la façon la plus élémentaire d’utiliser `CTaskDialog`, qui consiste à remplacer la boîte de message Windows. Cet exemple modifie aussi l’icône associée à la boîte de dialogue de tâche. Le fait de modifier l’icône donne à `CTaskDialog` la même apparence que la boîte de message Windows.

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>Pour remplacer une boîte de message Windows par un CTaskDialog

1. Créez un projet d’application MFC avec les paramètres par défaut. Appelez-le *MonProjet*.

2. Ouvrez le fichier MyProject.cpp dans l’ **Explorateur de solutions** .

3. Ajoutez `#include "afxtaskdialog.h"` après la liste d’includes.

4. Recherchez la méthode `CMyProjectApp::InitInstance`. Insérez les lignes de code suivantes avant l’instruction `return TRUE;` . Ce code crée les chaînes que nous utilisons dans la boîte de message Windows ou dans `CTaskDialog`.

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

5. Ajoutez le code suivant à la suite du code de l’étape 4. Ce code garantit que l’ordinateur de l’utilisateur prend en charge `CTaskDialog`. Si la boîte de dialogue n’est pas prise en charge, l’application affiche à la place une boîte de message Windows.

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

6. Insérez le code suivant entre parenthèses à la suite de l’instruction `if` de l’étape 5. Ce code crée `CTaskDialog`.

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

7. Dans la ligne suivante, ajoutez le code suivant. Ce code définit l’icône d’avertissement.

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

8. Dans la ligne suivante, ajoutez le code suivant. Ce code affiche la boîte de dialogue de tâche.

    ```cpp
    taskDialog.DoModal();
    ```

Vous pouvez omettre l’étape 7 si vous ne voulez pas que `CTaskDialog` affiche la même icône que celle de la boîte de message Windows. Si vous omettez cette étape, `CTaskDialog` ne présente aucune icône quand l’application l’affiche.

Compilez et exécutez l'application. L’application affiche la boîte de dialogue de tâche après avoir démarré.

## <a name="adding-functionality-to-the-ctaskdialog"></a>Ajout de fonctionnalités au CTaskDialog

La procédure suivante montre comment ajouter des fonctionnalités au `CTaskDialog` que vous avez créé dans la procédure précédente. L’exemple de code montre comment exécuter des instructions spécifiques en fonction des sélections de l’utilisateur.

### <a name="to-add-functionality-to-the-ctaskdialog"></a>Pour ajouter des fonctionnalités au CTaskDialog

1. Accédez à l’ **Affichage des ressources**. Si vous ne voyez pas l’ **Affichage des ressources**, vous pouvez l’ouvrir à partir du menu **Affichage** .

2. Développez l’ **Affichage des ressources** jusqu’à ce que vous puissiez sélectionner le dossier **Table de chaînes** . Développez-le et double-cliquez sur l’entrée **Table de chaînes** .

3. Faites défiler l’écran jusqu’au bas de la table de chaînes et ajoutez une nouvelle entrée. Modifiez l’ID en lui attribuant la valeur `TEMP_LINE1`. Définissez la légende en lui attribuant la valeur **Command Line 1**.

4. Ajoutez une autre nouvelle entrée. Modifiez l’ID en lui attribuant la valeur `TEMP_LINE2`. Définissez la légende en lui attribuant la valeur **Command Line 2**.

5. Revenez à MyProject.cpp.

6. À la suite de `CString emptyString;`, ajoutez le code suivant :

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

7. Recherchez l’instruction `taskDialog.DoModal()` et remplacez cette instruction par le code suivant. Ce code met à jour la boîte de dialogue de tâche et ajoute de nouveaux contrôles :

    ```cpp
    taskDialog.SetMainInstruction(L"Warning");
    taskDialog.SetCommonButtons(
        TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);
    taskDialog.LoadCommandControls(TEMP_LINE1, TEMP_LINE2);
    taskDialog.SetExpansionArea(
        expansionInfo, collapsedLabel, expandedLabel);
    taskDialog.SetFooterText(L"This is the a small footnote to the user");
    taskDialog.SetVerificationCheckboxText(L"Remember your selection");
    ```

8. Ajoutez la ligne de code suivante qui présente la boîte de dialogue de tâche à l’utilisateur et récupère la sélection de l’utilisateur :

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

9. Insérez le code suivant après l’appel à `taskDialog.DoModal()`. Cette section de code traite l’entrée de l’utilisateur :

    ```cpp
    if (taskDialog.GetVerificationCheckboxState())
    {
        // PROCESS IF the user selects the verification checkbox
    }

    switch (result)
    {
    case TEMP_LINE1:
        // PROCESS IF the first command line
        break;
    case TEMP_LINE2:
        // PROCESS IF the second command line
        break;
    case IDYES:
        // PROCESS IF the user clicks yes
        break;
    case IDNO:
        // PROCESS IF the user clicks no
        break;
    case IDCANCEL:
        // PROCESS IF the user clicks cancel
        break;
    default:
        // This case should not be hit because closing
        // the dialog box results in IDCANCEL
        break;
    }
    ```

Dans le code de l’étape 9, remplacez les commentaires qui commencent par PROCESS IF par le code que vous voulez exécuter dans les conditions spécifiées.

Compilez et exécutez l'application. L’application affiche la boîte de dialogue de tâche qui utilise les nouveaux contrôles et des informations supplémentaires.

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Affichage d’un CTaskDialog sans créer d’objet CTaskDialog

La procédure suivante montre comment afficher un `CTaskDialog` sans créer au préalable un objet `CTaskDialog` . Cet exemple est la suite des procédures précédentes.

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Pour afficher un CTaskDialog sans créer d’objet CTaskDialog

1. Ouvrez le fichier MyProject.cpp s’il n’est pas déjà ouvert.

2. Accédez à la parenthèse fermante de l’instruction `if (CTaskDialog::IsSupported())` .

3. Insérez le code suivant juste avant la parenthèse fermante de l’instruction `if` (avant le bloc `else` ) :

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

Compilez et exécutez l'application. L’application affiche deux boîtes de dialogue de tâche. La première boîte de dialogue résulte de la procédure Pour ajouter des fonctionnalités à CTaskDialog ; la deuxième provient de la dernière procédure.

Ces exemples ne montrent pas toutes les options accessibles à un `CTaskDialog`, mais ils devraient vous aider à vous lancer. Pour obtenir une description complète de la classe, consultez [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) .

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[CTaskDialog, classe](../mfc/reference/ctaskdialog-class.md)<br/>
[CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
