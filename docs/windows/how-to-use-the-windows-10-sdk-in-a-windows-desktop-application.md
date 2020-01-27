---
title: 'Comment : utiliser le kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows'
description: Comment définir la version cible du kit de développement logiciel (SDK) dans un projet d’application de bureau Windows pour utiliser le SDK Windows 10.
ms.custom: get-started-article
ms.date: 01/22/2020
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: c1d71b591398453f7cee02aa22cd2e377991588f
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725732"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Comment : utiliser le kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows

Quand vous créez un projet de bureau Windows classique dans Visual Studio, il cible le kit de développement logiciel (SDK) Windows 10 par défaut. Visual Studio installe une version de ce kit de développement logiciel ( C++ SDK) lorsque vous installez la charge de travail du bureau. Le kit de développement logiciel (SDK) Windows 10 prend en charge l’écriture de code pour Windows 7 SP1 et versions ultérieures. Pour plus d’informations sur le ciblage de versions spécifiques de Windows, consultez [utilisation des en-têtes Windows](/windows/win32/WinProg/using-the-windows-headers) et [Update winver et _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

Lorsque vous mettez à niveau un projet existant, vous avez le choix entre continuer à utiliser le SDK Windows cible spécifié dans votre projet. Ou vous pouvez recibler votre projet pour utiliser le kit de développement logiciel (SDK) Windows 10. Avec le kit de développement logiciel (SDK) Windows 10, vous bénéficiez des avantages de la prise en charge des systèmes d’exploitation et des normes linguistiques les plus récents.

## <a name="use-the-right-windows-sdk-for-your-project"></a>Utilisez le SDK Windows approprié pour votre projet

À compter de Visual Studio 2015, la bibliothèque C Runtime (CRT) a été divisée en deux parties : une partie, ucrtbase, contient les fonctions CRT standard C et propres à Microsoft que vous pouvez utiliser dans les applications Windows universelles. Cette bibliothèque est maintenant appelée Universal CRT, ou UCRT, et a été déplacée dans le kit de développement logiciel (SDK) Windows 10. Le UCRT contient de nombreuses nouvelles fonctions, telles que les fonctions C99, nécessaires pour prendre C++ en charge les normes de langage les plus récentes. L’autre partie du CRT d’origine est vcruntime. Il contient le code de prise en charge, de démarrage et d’arrêt du runtime C, ainsi que tout le reste qui n’a pas été placé dans le UCRT. La bibliothèque vcruntime est installée avec le compilateur C++ et l’ensemble d’outils dans Visual Studio. Pour plus d’informations, consultez fonctionnalités de la [bibliothèque CRT](../c-runtime-library/crt-library-features.md).

Le UCRT est désormais un composant système qui est installé sur chaque version de Windows 10. Il est également disponible en tant que composant pouvant être installé pour toutes les versions antérieures de Windows prises en charge. Vous pouvez utiliser le kit de développement logiciel (SDK) Windows 10 pour cibler toutes les versions de Windows prises en charge. Pour obtenir la liste complète des systèmes d’exploitation pris en charge, consultez [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

Pour recibler vos projets afin d’utiliser le kit de développement logiciel (SDK) Windows 10 quand vous effectuez une mise à niveau à partir d’une version de projet antérieure à Visual Studio 2015, procédez comme suit :

### <a name="to-target-the-windows-10-sdk"></a>Pour cibler le Kit de développement logiciel (SDK) Windows 10

1. Assurez-vous que le Kit de développement logiciel (SDK) Windows 10 est installé. Le kit de développement logiciel (SDK) Windows 10 est installé dans le cadre du **développement bureautique avec C++**  charge de travail. Une version autonome est disponible à l’adresse [téléchargements et outils pour Windows 10](https://developer.microsoft.com/windows/downloads).

1. Ouvrez le menu contextuel du nœud de projet, puis choisissez **recibler les projets**. (Dans les versions antérieures de Visual Studio, choisissez **recibler la version du kit de développement logiciel (SDK**).) La boîte de dialogue **examiner les actions** de la solution s’affiche.

   ![Examiner les actions de la solution](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

1. Dans la liste déroulante version de la **plateforme cible** , choisissez la version du kit de développement logiciel (SDK) Windows 10 que vous souhaitez cibler. En règle générale, nous vous recommandons de choisir la dernière version installée. Choisissez le bouton **OK** pour appliquer la modification.

   Le 8,1 dans ce contexte fait référence au kit de développement logiciel (SDK) Windows 8.1.

   Si cette étape est réussie, le texte suivant s'affiche dans la fenêtre Sortie :

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

1. Ouvrez la boîte de dialogue Propriétés du projet. Dans la section **Propriétés de Configuration** > **général** , notez les valeurs de version de la **plateforme cible Windows**. Changer la valeur ici revient à suivre cette procédure. Pour plus d'informations, consultez [Général, page de propriétés (Projet)](../build/reference/general-property-page-project.md).

   ![Version de la plateforme cible](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Cette action change les valeurs des macros du projet qui incluent des chemins d'accès aux fichiers d'en-tête et aux fichiers de la bibliothèque. Pour voir ce qui a changé, ouvrez la section **répertoires visuels C++**  de la boîte de dialogue **Propriétés du projet** . Sélectionnez l’une des propriétés, par exemple **répertoires Include**. Ensuite, ouvrez la liste déroulante de la valeur de propriété, puis choisissez **\<modifier >** . La boîte de dialogue **Répertoires Include** apparaît.

   ![Boîte de dialogue répertoires Include](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Choisissez le bouton **macros > >** , puis faites défiler la liste des macros vers le SDK Windows macros pour afficher toutes les nouvelles valeurs.

   ![Macros SDK Windows](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

1. Répétez la procédure de reciblage pour d’autres projets de solution, si nécessaire, et régénérez la solution.

### <a name="to-target-the-windows-81-sdk"></a>Pour cibler le Kit de développement logiciel (SDK) Windows 8.1

1. Ouvrez le menu contextuel du nœud de projet dans Explorateur de solutions, puis choisissez **recibler les projets**. (Dans les versions antérieures de Visual Studio, choisissez **recibler la version du kit de développement logiciel (SDK**).)

2. Dans la liste déroulante version de la **plateforme cible** , choisissez **8,1**.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : création d’une applicationC++de bureau Windows traditionnelle ()](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)
